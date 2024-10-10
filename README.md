# Regex fundamentals

Source: [HackerRank](https://www.hackerrank.com/domains/regex)

## Table of contents

## Regex
A string matching pattern.

### Basic string

```js
hackerrank						// Pattern.

test_hackerrank_test			// Test string.

hackerrank						// Output.
```

### Complex specific string

```js
^								// Start of the string.
.{3}							// Any three characters except a new line.
\.								// A literal dot.
(){3}							// Use parentheses to group the previous chain and a quantifier to look for it three times.
.{3}							// Three more characters except a new line.
$								// End of the string.

^(.{3}\.){3}.{3}$				// Final pattern.

test_abc.def.ghi.jkx_test		// Test string.

abc.def.ghi.jkx					// Output.
```

#### Anchoring

```js
^(.{3}\.){3}.{3}$							// Anchored pattern using ^ and $.

test_abc.def.ghi.jkx_test					// This works since there is only one instance of the pattern in the string.
abc.def.ghi.jkx								// Output.

test_abc.def.ghi.jkxabc.def.ghi.jkx_test	// However, this will not work using an anchored pattern.
```

### Digits \d and non-digits \D

```js
^								// Start.
\d{2}							// Two digits.
\D								// One non-digit.
\d{2}							// Two digits.
\D								// One non-digit.
\d{4}							// Four digits.
$								// End.

^\d{2}\D\d{2}\D\d{4}$			// Final pattern.

test_12A34B5678_test			// Test string.

12A34B5678						// Output.
```

### Whitespace \s and non-whitespace \S

```js
\S{2}							// Two non-whitespace characters.
\s								// One whitespace.
(){2}							// Wrap prior pattern and look for two instances.
\S{2}							// Two non-whitespace characters.

(\S{2}\s){2}\S{2}				// Final pattern.

test_12 23 34 98 87 65_test		// Test string.

12 23 34						// Output 1.
98 87 65						// Output 2.
```

### Word characters \w

```js
^\d								// Starts with a digit.
[\w]{4}							// Contains four word characters (word characters can be digits as well as letters and symbols).
\.$								// Ends with a dot.

^\d[\w]{4}\.$					// Final pattern.

test_1a_ze._test				// Test string.

1a_ze.							// Output.
```

#### Parentheses vs brackets

```js
[xyz]{4}						// Use brackets for ranges.
								// The elements will not be grouped for matching.

(\w\s){4}						// Use parentheses for chained tokens.
								// Or for elements that need to be matched.
```

### Negation

```js
^												// Start.
[^\d]											// Should not be a digit (using the caret ^).
[^aeiou]
[^bcDF]
[^\s]
[^AEIOU]
[^.,]
$												// End.

^[^\d][^aeiou][^bcDF][^\s][^AEIOU][^.,]$		// Final pattern.

think?											// Test string.

think?											// Output.

```

### Repetitions

```js
\d{3, 5}						// Will match a digit three, four or five times.

\d{3,}							// Will match a digit three or more times.

\d*								// Will match zero or more instances.

\d+								// Will match one or more instances.
```

### Word boundaries \b

```js
\bhello\b						// It will match a position of word characters separated by non-word characters.

hello world.					// Will match 'hello'.
helloworld.						// Will not match 'hello'.
```

### Eveything enclosed

```js
(?:ok){3,}						// Match everything enclosed, ie 'ok', three times or more without grouping.

test_okokokokkkokokok_test		// Test string.

okokokok						// Output 1.
okokok							// Output 2.
```

### Separation |

```js
^(?:Mr\.|Mrs\.|Ms\.|Dr\.|Er\.)[a-zA-Z]+$

Mr.Yoshi						// Match.
Dr.Yoshi						// Match.
Dr#Yoshi						// Not a match.
```

