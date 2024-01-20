# Title (replace with your title)

This gist aims to provide an overview of regular expressions and their usage. Regular expressions (Regex) prove valuable when attempting to identify specific character combinations within a string. They are particularly useful for extracting information from code or performing validation. To illustrate, this tutorial will walk through a code snippet designed to match an email address, highlighting various components of regular expressions along the way.



## Summary

Throughout the tutorial, the subsequent code will serve as a concrete illustration, demonstrating the practical application of individual components within regular expressions. Specifically, this code is designed for matching email addresses. An important utility of this code lies in its ability to validate whether an email adheres to the correct format.

Matching email:

```

^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$

```


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

* [Author](#author)

## Regex Components

### Anchors
Anchors are used to assert the position of the regex pattern within the input text. Anchors do not match characters but rather specific positions in the text. Anchors are useful for defining where in the input text a match should occur.    Anchors: ^ and $ are used to match the start and end of a line, respectively.They provide a way to enforce specific conditions on the position of the pattern, such as matching at the start or end of lines, or as whole words. 
Here are the commonly used anchors:

    Caret ^:

    The caret asserts the position at the start of a line or the start of the entire string.
        Example: ^start matches "start" only when it appears at the beginning of a line or the start of the entire string.

    Dollar $:

    The dollar sign asserts the position at the end of a line or the end of the entire string.
        Example: end$ matches "end" only when it appears at the end of a line or the end of the entire string.

    Word Boundary \b:

    \b asserts a position at a word boundary.
        Example: \bword\b matches the word "word" only when it appears as a whole word and not as part of another word.

    Non-Word Boundary \B:

    \B asserts a position where a word boundary does not occur.
        Example: \Bword\B matches the word "word" only when it is part of another word, not when it appears as a whole word.

    String Start \A:

    \A asserts the position at the start of the entire string.
        Example: \Astart matches "start" only when it appears at the very beginning of the entire string.

    String End \Z:

    \Z asserts the position at the end of the entire string but allows for an optional final newline character.
        Example: end\Z matches "end" only when it appears at the very end of the entire string.

    String End \z:

    \z asserts the position at the end of the entire string.
        Example: end\z matches "end" only when it appears at the very end of the entire string without allowing for a final newline character.

 

### Quantifiers
Quantifiers: Specify the number of occurrences of a character or group. For example, a{2,4} matches 2 to 4 consecutive "a" characters. Quantifiers are used to specify the number of occurrences of a character, group, or character class. They allow you to match patterns of different lengths, ranging from zero occurrences to an unlimited number of occurrences. 
Here are some commonly used quantifiers:

    Asterisk *:

    Matches 0 or more occurrences of the preceding element.
        Example: ab*c matches "ac," "abc," "abbc," and so on.

    Plus +:

    Matches 1 or more occurrences of the preceding element.
        Example: ab+c matches "abc," "abbc," and so on, but not "ac."

    Question Mark ?:

    Matches 0 or 1 occurrence of the preceding element. 
        Example: colou?r matches both "color" and "colour."

    Braces {m}:

    Matches exactly m occurrences of the preceding element.
        Example: x{3} matches "xxx."

    Braces {m,}:

    Matches m or more occurrences of the preceding element.
        Example: x{2,} matches "xx," "xxx," and so on.

    Braces {m,n}:

    Matches between m and n occurrences of the preceding element (inclusive).
        Example: x{2,4} matches "xx," "xxx," and "xxxx."

    Lazy Quantifiers (*?, +?, ??, {m,}?, {m,n}?):

    Make the preceding quantifier lazy, meaning it matches as few characters as possible.
        Example: a.*?b matches the shortest sequence between "a" and "b" in "aXbYbZ," resulting in "aXb."

### OR Operator
    OR operator is represented by the vertical bar |. It is used to specify alternatives, allowing you to match one pattern or another. The | serves as a logical OR, meaning that it matches the pattern on its left or the pattern on its right. The OR operator is represented by the pipe symbol |. It allows you to match either the pattern on the left or the pattern on the right. The OR operator is used to create alternatives within a regular expression.

        Example:  cat|dog  This regex will match either "cat" or "dog." If the input string contains either "cat" or "dog," the regex will find a match.

        Example:  (cat|dog) food  You can use parentheses to group expressions when using the OR operator to make the intention clearer.


### Character Classes
    Character Classes: A set of characters enclosed in square brackets. For example, [aeiou] would match any vowel.  character classes (also known as character sets) are used to specify a group of characters that you want to match at a particular position in the input string. Character classes are enclosed within square brackets []. They allow you to match any single character from the specified set.

    Examples:
    Single Characters:

    [aeiou]: Matches any vowel (a, e, i, o, u).
    [123]: Matches the digits 1, 2, or 3.

    Ranges:

    [a-z]: Matches any lowercase letter.
    [A-Z]: Matches any uppercase letter.
    [0-9]: Matches any digit.

    Negation:

    [^aeiou]: Matches any character that is not a vowel.
    [^0-9]: Matches any non-digit character.

    Combining Characters:

    [aeiou123]: Matches any vowel or digit 1, 2, or 3.

    Escape Sequences:

    [\d]: Matches any digit (equivalent to [0-9]).
    [\w]: Matches any word character (alphanumeric + underscore).
    [\s]: Matches any whitespace character.

    Combining Characters with Ranges:

    [a-zA-Z]: Matches any uppercase or lowercase letter.
    [0-9a-fA-F]: Matches any hexadecimal digit.

### Flags
In regular expressions (regex), flags are optional parameters that modify the behavior of the regex pattern matching. Flags are added after the closing delimiter of the regex and are usually represented by letters. Each flag serves a specific purpose, and you can combine them as needed to achieve the desired behavior for your regex pattern matching. The most common flags include:

    Case Insensitive (i): This flag makes the regex pattern case-insensitive, meaning it will match both uppercase and lowercase characters. For example:
    /pattern/i

    Global (g): This flag enables global searching, meaning the regex will find all matches in the input string rather than stopping after the first match. For example:
    /pattern/g

    Multiline (m): This flag enables multiline mode, changing the behavior of ^ and $ to match the start and end of each line within a multiline input string. For example:
    /pattern/m

    Dot All (s): This flag makes the dot (.) in the regex match any character, including newline characters (\n). Without this flag, the dot typically does not match newline characters. For example:
    /pattern/s

    Sticky (y): This flag restricts the regex search to match only at the index indicated by the lastIndex property of the regex. It enforces that the match must start at a specific position. For example:
    /pattern/y

    Unicode (u): This flag enables full Unicode matching. It is useful when working with Unicode characters and ensures correct handling of surrogate pairs. For example:
    /pattern/u

    Flags are added at the end of a regex literal or within the RegExp constructor when creating a regex object in JavaScript. For instance:
    const regex = /pattern/gi;
    // or
    const regexObj = new RegExp('pattern', 'gi');


### Grouping and Capturing
Grouping and Capturing: Parentheses () are used for grouping and capturing. They can also be used to apply quantifiers to a group.


### Bracket Expressions
In regular expressions, bracket expressions (also known as character classes) are used to define a set of characters that you want to match at a particular position in the input string. Bracket expressions are enclosed within square brackets [], and they match any single character within the specified set.

    Examples of bracket expressions:

    Single Characters:

    [aeiou]: Matches any vowel (a, e, i, o, u).
    [123]: Matches the digits 1, 2, or 3.
    
    Ranges:

    [a-z]: Matches any lowercase letter.
    [A-Z]: Matches any uppercase letter.
    [0-9]: Matches any digit.
    
    Negation:

    [^aeiou]: Matches any character that is not a vowel.
    [^0-9]: Matches any non-digit character.
    
    Combining Characters:

    [aeiou123]: Matches any vowel or digit 1, 2, or 3.
    
    Escape Sequences:

    [\d]: Matches any digit (equivalent to [0-9]).
    [\w]: Matches any word character (alphanumeric + underscore).
    [\s]: Matches any whitespace character.

    Keep in mind that within a bracket expression, most metacharacters lose their special meaning, and only the character they represent is matched. However, some metacharacters still have a special meaning within brackets, such as the caret ^ when used at the beginning to negate the set.

    Examples:

    [-abc]: Matches a hyphen, "a," "b," or "c."
    [^-abc]: Matches any character except a hyphen, "a," "b," or "c."

### Greedy and Lazy Match

    Greedy Quantifiers:

    Greedy quantifiers match as much of the input as possible while still allowing the overall regex to match. The most common greedy quantifiers are * (matches 0 or more), + (matches 1 or more), and ? (matches 0 or 1).
    Examples:
    .*: Greedily matches any sequence of characters (including none).
    .+: Greedily matches one or more characters.
    .{2,5}: Greedily matches between 2 and 5 characters.
    In a regex like .*, the * is greedy and will match as many characters as possible.

    Lazy (Non-Greedy) Quantifiers:

    Lazy quantifiers match as little of the input as possible while still allowing the overall regex to match. They are denoted by adding a ? after the quantifier (*?, +?, ??).
    Examples:
    .*?: Lazily matches any sequence of characters (including none).
    .+?: Lazily matches one or more characters.
    .{2,5}?: Lazily matches between 2 and 5 characters.
    In a regex like .*?, the *? is lazy and will match as few characters as possible.

    Examples to illustrate the difference:

    Greedy: Regex a.*b applied to the string aXbYb will match the entire string (aXbYb), as .* greedily consumes as many characters as possible.

    Lazy: Regex a.*?b applied to the same string aXbYb will match only aXb, as .*? lazily consumes as few characters as possible to satisfy the overall pattern.

### Boundaries
    Boundaries are used to define specific positions within the input text. These boundaries help in constraining matches to occur at certain locations in the text rather than anywhere in the string. These boundaries are useful for specifying where in the input text a match should occur. They are especially handy when you want to find patterns at the beginning or end of lines, whole words, or the entire string. 
    Here are some common boundary-related constructs in regular expressions:

    Word Boundary (\b):

    \b asserts a position at a word boundary.
        Example: \bword\b will match the word "word" only when it appears as a whole word and not as part of another word.

    Non-Word Boundary (\B):

    \B asserts a position where a word boundary does not occur.
        Example: \Bword\B will match the word "word" only when it is part of another word, not when it appears as a whole word.

    Line Start (^):

    ^ asserts the position at the start of a line.
        Example: ^start will match "start" only when it appears at the beginning of a line.

    Line End ($):

    $ asserts the position at the end of a line.
        Example: end$ will match "end" only when it appears at the end of a line.

    String Start (\A):

    \A asserts the position at the start of the entire string.
        Example: \Astart will match "start" only when it appears at the very beginning of the entire string.

    String End (\Z):

    \Z asserts the position at the end of the entire string but allows for an optional final newline character.
        Example: end\Z will match "end" only when it appears at the very end of the entire string.

    String End (\z):

    \z asserts the position at the end of the entire string.
        Example: end\z will match "end" only when it appears at the very end of the entire string without allowing for a final newline character.



### Back-references
    Back-references allow you to refer back to capturing groups within the regex pattern. They enable you to match the same text that was previously captured by a capturing group. Backreferences are typically used with parentheses () to define capturing groups.

    The syntax for a backreference is \n, where n is the index or number of the capturing group. The index is usually a positive integer, indicating the order in which the capturing group appears in the pattern.

        Example to illustrate backreferences:
        (\w+) and \1

        (\w+): This is a capturing group that matches one or more word characters.
        and: This is a literal string.
        \1: This is a backreference to the first capturing group, \w+. It means "match the same text as captured by the first group."
        This regex would match patterns like "apple and apple" or "banana and banana," where the same word appears twice separated by "and."

        Another example that validates repeated words:
        \b(\w+)\b.*\b\1\b

        \b(\w+)\b: This capturing group matches a whole word.

        .*: This matches any characters (zero or more).

        \b\1\b: This is a backreference to the first capturing group, ensuring that the same word appears again.

        This regex would match strings like "apple and banana and apple."

### Look-ahead and Look-behind

    Lookahead and lookbehind are zero-width assertions in regular expressions. They don't consume characters in the input string but instead assert whether a certain pattern is or isn't present at a specific position. They are used to define conditions for a match without including the matched text in the result.

    Positive Lookahead (?=...):

    A positive lookahead asserts that a certain pattern must be present at a specific position in the input.
        Example: a(?=b) matches the "a" only if it is followed by a "b."
        Example: apple(?=pie) Positive Lookahead: Match "apple" only if it is followed by "pie."

    Negative Lookahead (?!...):

    A negative lookahead asserts that a certain pattern must not be present at a specific position in the input.
        Example: a(?!b) matches the "a" only if it is not followed by a "b."
        Example: apple(?!pie) Match "apple" only if it is not followed by "pie."


    Positive Lookbehind (?<=...):

    A positive lookbehind asserts that a certain pattern must be present immediately before the current position in the input.
        Example: (?<=a)b matches the "b" only if it is preceded by an "a."
        Example: (?<=apple)pie Match "pie" only if it is preceded by "apple."

    Negative Lookbehind (?<!...):

    A negative lookbehind asserts that a certain pattern must not be present immediately before the current position in the input.
        Example: (?<!a)b matches the "b" only if it is not preceded by an "a."
        Example: (?<!apple)pie  Match "pie" only if it is not preceded by "apple."


## Author
This tutorial was created by Shan Nowak.

Contact:

GITHUB: https://github.com/scnowak

EMAIL: SHAN.NOWAK93@GMAIL.COM