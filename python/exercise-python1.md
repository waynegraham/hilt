---
layout: exercise
title: First Python Exercises
description: Your first python exercises
permalink: /exercises/python-one/
javascript:
  - /assets/js/hint.js
---

[Python Cheatsheet](/resources/python-cheatsheet/)

# Printing to the Screen
Store your street address, city, state, and zip code in variables (or
even better, a **dictionary**!), then print them in the usual format:

Name<br/>
Street<br/>
City, State, Zip



{% highlight python %}
address = {
  "name": "Thomas Jefferson",
  "street": "931 Thomas Jefferson Parkway",
  "city": "Charlottesville",
  "state": "Virginia",
  "zip": "22902"
}

print(address['name'])
print(address['street'])
print(address['city'] + ", " + address['state'] + " " + address['zip'])
{% endhighlight %}

<hr/>

# Calculations

Write a program that converts seconds to years. Test your program with
`600000000` seconds, `60` seconds, and `40000.33` seconds.

Does this make sense for all the inputs? We can get a bit more exact if
we cast `test1` as a **float**.

`test1 = 600000000.to_f`

{% highlight python %}

test1 = 600000000
# there are 60 seconds and minute
in_minutes = test1 / 60
# there are 60 minutes in an hour
in_hours = in_minutes / 60
# there are 24 hours in a day
in_days = in_hours / 24
# there are about 365 days in a year
in_years = in_days / 365

print(in_years)

{% endhighlight %}


<hr class="prepend"/>

# Collections

Create a collection of these authors and the year they kicked the bucket. Print the
collection in the following format:

Charles Dickens died in 1870.

Charles Dickens, 1870<br/>
William Thackeray, 1863<br/>
Anthony Trollope, 1882<br/>
Gerard Manley Hopkins, 1889

{% highlight python %}
authors = {
    "Charles Dickens": "1870",
    "William Thackeray": "1863",
    "Anthony Trollope": "1882",
    "Gerard Manley Hopkins": "1889"
}

for author, date in authors.items():
    print("%s" % author + " died in " + "%s." % date)
{% endhighlight %}

<hr/>

# Branching

A time traveler has suddenly appeared in your classroom!

Create a variable representing the traveler's year of origin (e.g., year = 2000) and greet our strange visitor with a different message if he is from the distant past (before 1900), the present era (1900-2020), or from the far future (beyond 2020).

If you want to get really fancy, try writing a line of code that would ask your user "What year is this time traveler from?", then print the appropriate response according to their answer. (Hint: try looking here for tools! https://docs.python.org/3/tutorial/controlflow.html)

{% highlight python %}

year = 1899
# if you chose to get fancy, the input request might look like this:
# year = int(input("What year is this time traveler from? "))

if year <= 1900:
    print ("Welcome from the distant past!")
elif year > 1900 and year < 2020:
    print ("Welcome from the present!")
else:
    print ("Welcome from the far future!")

{% endhighlight %}

<hr/>

# Pirate Test (easy)
Write a program that tests whether someone is a pirate or not.  As we all know, no pirate can resist using the exclamation "**Arrr!**" constantly.  If a string contains "**Arrr!**", tell the pirate to go away.  Otherwise, welcome your non-pirate friend with open arms.

## Tests:

* **Arrr! How are ye?**
* **Hello, friend.**

**Hint**: `string_variable["some text"]` equals "`some text`" if those characters exist in
`string_variable` and otherwise equals `nil`.

{% highlight python %}
answers = ["Arrr! How are ye?", "Hello, friend."]

for answer in answers:
    if "Arrr!" in answer:
        print("Go away, scurvy sea dog!")
    else:
        print("Welcome!")

{% endhighlight %}

<hr/>

# Longest word (not too hard)
Print out the longest word in "The quick brown fox jumped over the lazy dogs" and its length.

##Hints
* `len(my_string)` equals the length of a string.
* `list_of_words = my_long_string.split()` will break the string up by spaces into a list.

What about "The quick brown fox jumps over the lazy dogs"?  How might we find all the longest words?

{% highlight python %}
sentence = "The quick brown fox jumped over the lazy dogs"

longest = ""

words = sentence.split()

for word in words:
    if len(word) > len(longest):
        longest = word

print("The word '" + longest + "' is ", len(longest), " characters long.")

{% endhighlight %}

<hr/>

# Calculating Grades (ok, let me think about this one)

Write a program that will average 3 numeric exam grades and return an average test score, a corresponding letter grade, and a message stating whether the student is passing.

<table>
<tr>
<th>Average</th>
<th>Grade</th>
</tr>
<tr>
<th>90+</th>
<th>A</th>
</tr>
<tr>
<th>80-89</th>
<th>B</th>
</tr>
<tr>
<th>70-79</th>
<th>C</th>
</tr>
<tr>
<th>60-69</th>
<th>D</th>
</tr>
<tr>
<th>0-59</th>
<th>F</th>
</tr>
</table>

Exams: 89, 90, 90<br/>
Average: 90<br/>
Grade: A<br/>
Student is passing.

Exams: 50, 51, 0<br/>
Average: 33<br/>
Grade: F<br/>
Student is failing.


{% highlight python %}
# option 1 to calculate the grade average
e1 = 89
e2 = 90
e3 = 90

avg = (e1 + e2 + e3) / 3

# option 2 to calculate the grade average
grades = [50, 51, 0]
sum = 0
for grade in grades:
  sum = sum + grade

avg = sum / len(grades)

if avg >= 90:
    letter_grade = "A"
elif avg >= 80 and avg < 90:
    letter_grade = "B"
elif avg > 69 and avg < 80:
    letter_grade = "C"
elif avg <= 69 and avg >= 65:
    letter_grade = "D"
else:
    letter_grade = "F"

for grade in grades:
    print("Exam: " + str(grade))

print("Average: " + str(avg))

print("Grade: " + letter_grade)

if letter_grade is "F":
    print "Student is failing."
else:
    print "Student is passing."



{% endhighlight %}

<hr/>

# Population Growth (Might need to ask somebody)

The population of Fibonaccia has been shown to grow at an exponential rate with a really odd phenomenon: each year the total population is the sum of the population for the previous two years. With a starting population of 10, the population for the first five years would be:

10, 20, 30, 50, 80

Write a program that will calculate the population of Fibonaccia after 10 years, 20 years, 100 years.

**Hint**: `population = [0,10]`

{% highlight python %}
years = [100]
population = [0,10]

for i in range(years):
    population.append(population[-1] + population[-2])

print(population)
{% endhighlight %}

<hr/>

# Population Growth (Are you serious?)

Each new term in the Fibonacci sequence is generated by adding the previous two terms. By starting with 1 and 2, the first 10 terms will be:

1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, ...

Find the sum of all the even-valued terms in the sequence which do not exceed 4 million.

{% highlight python %}
# There are many ways to solve this problem; here is one:

MAX = 4000000

fib_seq = [1, 2]
sum = 2

while fib_seq[-1] <= MAX:
    next_fib = fib_seq[-1] + fib_seq[-2]
    fib_seq.append(next_fib)
    if next_fib % 2 == 0:
        sum += next_fib

print("Sum of even members of Fibonacci sequence less than 4,00,000: %d") % sum

{% endhighlight %}
