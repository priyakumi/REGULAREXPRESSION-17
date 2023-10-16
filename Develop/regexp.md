

# Module 17: Javascript Regular Expressions(Regex)

As a web development student, I have developed this tutorial, where you will learn about the Regex abbreviation of Regular Expression and how you can use it to identify characters in a text.

## Summary

Regex or Regular Expressions are patterns used to identify combinations or characters in a string, they can be used to validate text based on complex criteria, and they can also be used to replace patterns of the character in a string.

In this tutorial we are going to use this Email Regular Expression:  /^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{2,6})$/ 
as an example of how to breakdown some Regular Expression examples and how to use it.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors(^,$)

Anchors have special meaning in regular expressions. They do not match any character. Instead, they match a position before or after characters:

 ^ – The caret anchor matches the beginning of the text.
 $ – The dollar anchor matches the end of the text.

### Quantifiers

Quantifiers are used to communicate how many characters are expected. Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found. By default, quantifiers are greedy, and will match as many characters as possible. If the ",+,?,{}" characters are found within regular expressions, they are considered quantifiers. The ? indicates the expression to match 0 or 1 time. As mentioned in the summary above because there are 2 types of formats we'll use the or operator to distinguish which format we are using. In our Hex Value regular expression we have {6} (Hex Triplet Format) and {3} (Shorthand Hex Format), this indicates that the length of the component preceding these quantifiers should be 6 for {6} and 3 for {3}.

Quantifiers summary

The following lists the quantifiers:

Quantifier	Description
*	Match zero or more times.
+	Match one or more times.
?	Match zero or one time.
{ n }	Match exactly n times.
{ n ,}	Match at least n times.
{ n , m }	Match from n to m times.

### OR Operator 

/^#?([a-f0-9]{6}|[a-f0-9]{3})$/
The "or" operator within a regular expression is defined using the | element. The or operator indicates that it could either of the components that we are separating with the |. For our hex value regular expression we have ([a-f0-9]{6}``|``[a-f0-9]{3}). Note the or operator separating these 2 components. This means that our hex value could either be 6 characters [a-f0-9]{6} or 3 characters [a-f0-9]{3}.

### Character Classes

/^#?([a-f0-9]{6}|[a-f0-9]{3})$/
Character classes are components within our regular expression that tells us what type of characters to expect. In our example our character classes are confined within brackets []. For our example we have 2 character classes: [a-f0-9] and [a-f0-9] which searches for the same values. We will be breaking down what the characters are searching within these character classes. a-f searches for letters a-f and 0-9 searches for digits 0-9.

### Flags

Regular expressions may have flags that affect the search.

There are only 6 of them in JavaScript:

i
With this flag the search is case-insensitive: no difference between A and a (see the example below).
g
With this flag the search looks for all matches, without it – only the first match is returned.
m
Multiline mode (covered in the chapter Multiline mode of anchors ^ $, flag "m").
s
Enables “dotall” mode, that allows a dot . to match newline character \n (covered in the chapter Character classes).
u
Enables full Unicode support. The flag enables correct processing of surrogate pairs. More about that in the chapter Unicode: flag "u" and class \p{...}.
y
“Sticky” mode: searching at the exact position in the text (covered in the chapter Sticky flag "y", searching at position)

### Grouping and Capturing

Regular expressions can be grouped by placing them inside parentheses () to apply quantifiers or restrict alternation to that part of the regex;

For example:
/^([a-z0-9_\.-]+)@([\da-z\.-]+).([a-z\.]{2,6})$/ 
There are three groups in the regex code above.

 Group 1: [a-z0-9_\.-] is used for the username of the email account.
 Group 2: [\da-z\.-] is used to capture the domain name/email service. 
 Group 3: [a-z\.] is used to capture the domain extension.

### Bracket Expressions

 Bracket expression is a list of characters enclose by []. Much like the grouping and capturing section. Below is an example:

/^([a-z0-9_\.-]+)@([\da-z\.-]+).([a-z\.]{2,6})$/
We have three brackets in the above example:

Bracket Expression 1: [a-z0-9_\.-] - includes case sensitive characters from a-z, numbers from 0-9 an underscore, periods and hyphens.

Bracket Expression 2: [\da-z\.-] - includes all digits, case sensitive characters from a-z, periods and hyphens

Bracket Expression 3: [a-z\.] - includes case sensitive characters from a-z and periods.

### Greedy and Lazy Match

/^#?([a-f0-9]{6}|[a-f0-9]{3})$/
A greedy match tries to match an element as many times as possible. Whereas, a lazy match tries to match an element as few times as possible. In our example we have ? which signifies lazy quantifier. This is referred to a lazy quantifier because it causes the regular expression engine to match as few occurances as possible. We can simply turn this lazy match into a greedy one by adding a ?.

### Boundaries

\b Matches on a word boundary, meaning one side is a word character (usually a letter, digit or underscore) and the other side is not a word character (string or space character).

Example:
/^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{2,6})$/

/^ Matches: This indicates the beginning of the string.

([a-z0-9_.-]+) Matches: This is a capturing group that can matches one or more lowercase letters, digits, underscores, dots, or hyphens.

@ Matches: This matches the "@" symbol that separates the username and domain parts of an email address.

([\da-z.-]+) Matches: This is a second group in the same string of our email that matches one or more digits, lowercase letters, dots, or hyphens.

. Matches: This corresponds to a literal dot character. The backslash is used to escape the dot because it has a special meaning in regex.

([a-z.]{2,6}) Matches: This is the third and final group of our email that matches between 2 and 6 lowercase letters or dots. This is used to match the top-level domain (TLDs) of the email address, such as ".com" or ".org". Domain extensions are used to categorize websites by type, location or business model.


### Back-references

Back-references What does a back-reference look like? It is typically a \ followed by single-digit. Back-reference is a command, which refers to something that already happened or a previous part of a matched regular expression. You could make a better preference by name or number; basically, what you are doing is you are referencing a named group, and you would have a bag/and a K then the name of that group, for example.

### Look-ahead and Look-behind

Look ahead and look behind allows how matches get handled when using regular expressions.Look ahead and look behinds, also known as look around assertions, are similar to a start and end of the line or anchors. However, look around can match characters, and then they return a result of either a match or no match.

## REFERENCES
- https://www.w3schools.com/js/js_regexp.asp
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions/Cheatsheet
- https://javascript.info/regular-expressions
- Javascript: A beginner's guide,Fourth Edition - John Pollock.


## Author
My name is Mohanapriya. I am  currently enrolled in the Berkeley Coding Bootcamp.

GITHUB LINK: https://github.com/priyakumi
