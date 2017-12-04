# Lecture 2: Data Types

### Wes Yu

Software Engineer, Honey

---
## Objectives
* Review the concept of a data type and how it relates to variables
* Declare, assign to, and manipulate data stored in a variable
* Create arrays and access values in them
* Iterate over and manipulate values in an array

---
## Agenda
* What is a Data Type?
* Variables
* Introduction to Arrays
* Iterating through Arrays

---
## What is a Data Type?

In programming languages, a data type is a classification identifying one of various types of data. From a data type, we can determine:

* the possible values for that type
* the operations that can be performed on that type
* the meaning of the data
* the way values of that type can be stored

---

Most programming languages have the following data types

* `strings` : single words or sentences surrounded by double or single quote, e.g. `'Hello World'`
* `integers` : any number without a decimal point, e.g. `9`
* `floats` : any number  with a decimal point, e.g. `3.99`
* `booleans` : either true or false, i.e. `true`, `false`
* `arrays` : collections of data, e.g. `['Shirts', 'Pants', 'Dresses']`
* `associative array`: collection of data in the form of key-value pairs. Also referred to as a `map` or `dictionary`.
* `objects` : a representation of something

---
In JavaScript, we have five `primitive` types:

* `string`
* `number` (all numbers are floating point numbers)
* `boolean`
* `undefined`
* `null`
* `symbol`*****

&nbsp;

Everything else, is an `object`, including:

* `arrays` *e.g.* `[]`, `['apple', 'orange']`
* `functions`, *e.g.*, `function foo() {}`
* `objects`, *e.g.* `{}`, `{ name: 'John Smith' }`

&nbsp;

***** Introduced in ES6. Let's not worry about them for now.

---
JavaScript has a standard library of `objects`, including `Array`, `Date`, `Math`, and `Function` with their own built-in methods. There is also a core set of language elements, such as:

* operators, *e.g.* `+`, `-`, `||`
* control structures, *e.g.* `if () {}`
* statements, *e.g.* `var x = 2;`

---
![GeneralAssemb.ly](../../img/icons/code_along.png)
##Data Types

Let's use `Node.js`'s console to explore types.

---
### Determining the Type
We can determine the type of a variable or value using `typeof()`*****, which returns a string.

```js
typeof(10) === 'number'
=> true
```
```js
typeof({}) === 'object'
=> true
```
```js
typeof('Hello World') === 'string'
=> true
```
***** Due to how JavaScript was first implemented, `typeof(null)` returns `'object'`

---
### Numbers
In most programming languages, numbers are divided into two types, integers and floating point numbers.

&nbsp;

In JavaScript, we only have floating point numbers, which results in cases like these:
```js
0.1 + 0.2
=> 0.30000000000000004
```

```js
3.0 === 3
=> true
```
---
### Arithmetic Operators
We use operators to work with data in JavaScript. The standard arithmetic operators are available:
```js
1 + 2
=> 3
```
```js
2 - 5
=> -3
```
```js
5 / 2
=> 2.5
```
```js
6 * 2
=> 12
```

---
### Additional Math Operators
For additional math operators, *e.g.* power, we can use the `Math` object
```js
// 3^2 becomes
Math.pow(3,2)
=> 9
```
```js
// square root of 4 becomes
Math.sqrt(4)
=> 2
```
```js
// random number between 0 and 1 exclusive
Math.random()
=> 0.3156855241316119
// hopefully, you got a different random number!
```
```js
// rounding a number to an integer
Math.round(3.99)
=> 4
```

---
### Strings
Strings are a collection of characters. We'll use this type for words and text, *e.g.* `'John Doe'`. We can combine, or concatenate strings together, using the `+` operator:
```js
// notice the space in "Hello "
"Hello " + "World!"
=> "Hello World!"
```

If we try adding a number and a string, the number gets converted to a string:
```js
"3" + 3
=> "33"

"5" + 6
=> "56"
```

---
Note that you need to end the string with whatever type of quote you started out with:
```js
"Greetings y'all!"
=> 'Greetings y\'all!'
```

Depending on the environment, the quote may appear as escaped or unescaped.

&nbsp;

You can escape a quote manually using a `\`
```js
'John\'s a JavaScript developer!'
=> 'John\'s a JavaScript developer!'
```
---
## Variables
Variables are used to store data into a computer's memory so we can reference them later. We will always use the `var` keyword to declare a variable.*****

&nbsp;

If we declare a variable without assigning it a value, its value is `undefined`:
```js
var a;
a
=> undefined
```

A separate issue is that `var a` by itself returns `undefined` in the `REPL`.

&nbsp;

*****We'll talk about `const` and `let`, introduced in ES6, in a later class.

---
By convention, all names should be `camelCased`, whether they're for variables or functions. There are certain reserved words we can't use for names, *e.g.* `var`, `function`, `class`, etc

```js
var myScore = 100;
```
```js
var myString = "Hello World!";
```

---
### Assignment Operators
Values are assigned to a variable using `=`:
```js
var num = 1;
num;
=> 1
```

JavaScript also has compound assignment operators, `+=`, `-=`, `/=`, and `*=`:
```js
num;
=> 1

num += 5;
=> 6
```

---
We can use `++` and \-\- to increment and decrement by `1` respectively as postfix or prefix operators:
```js
var num = 5;
num;
=> 5

num++;
=> 5
num;
=> 6

++num;
=>7
```

---
### Number to String
Use the `toString()` method on a number by itself, or on a variable that's storing the number:
```js
var num = 1;
num.toString();
=> "1"

(1).toString();
=> "1"

1..toString();
=> "1"

1 .toString();
=> "1"

// what does this return?
1.toString();
```

---
### String to Number
Use the `Number()` method, and pass in the string. It will return `NaN`, or not-a-number for anything that's not parseable:
```js
Number("5");
=> 5

Number(":)");
=> NaN
```

---
## Arrays
We'll store collections of data in arrays. They're great for storing, enumerating, and reordering data.

&nbsp;

Each item in an array is called an element, and each element has an index.

```js
var friendsList = ['Moe', 'Larry', 'Curly'];
friendsList;
=> ['Moe', 'Larry', 'Curly']
```

---
### Indices
The items in an array will always be returned in the same order. We start counting at `0`, so the first element has the index `0`. We can access an element at an index using bracket notation:
```js
arrayVariable[index]
```
```js
var friendsList = ['Moe', 'Larry', 'Curly'];
var first = friendsList[0];
first;
=> 'Moe'

//what does friendsList[2] return?
```

---
### Assignment Via Index
We can also reassign values to the array based on the index.
```js
arrayVariable[index] = newValue
```
```js
var friendsList = ['Moe', 'Larry', 'Curly'];
friendsList[0] = "Sam";

//what does friendsList[0] return?
//what does friendsList now look like?
```
---
### Length Property
The `length` property of an array will give us `1` more than the last index. It's the number of items in the array. So, the index of the last element is always `length - 1`.
```js
var friendsList = ['Moe', 'Larry', 'Curly'];
friendsList.length;
=> 3

// what does friendsList[friendsList.length - 1] return?
```


---
### Types in Arrays
JavaScript arrays can contain elements of any type, and the elements can be of different types*****. They can also dynamically grow and shrink in size.
```js
var sillyArray = ["Hello World!", true, undefined, null,
    42, ["Look, a nested array!",
    "One more string for good measure!"], false];
```

&nbsp;

*****Well-written code should not have an array where the elements are of different types, unless the different type is `null` or `undefined`. Even then, not desirable.

---
Strings are array-like. We can use the `length` property to get the number of characters, and bracket notation to get a character at an index.
```js
var simpleString = "Hello World!";
simpleString.length;
=> 12

simpleString[0];
=> 'H'
```

---
### Creating Arrays
We've seen the literal notation so far, and it's the notation we **should** use. There's also the constructor***** notation which you should **not** use.
```js
var a = new Array();
a[0] = "dog";
a;
=> ["dog"]

var pets = new Array("dog", "cat", "tortoise");
pets;
=> ["dog", "cat", "tortoise"]
```

&nbsp;

*****We'll talk about constructors in-depth in a later class.

---
### Length Review
The `length` property is `1` more than the last index.
```js
var pets = ["dog", "cat", "tortoise"];
pets[100] = "fish";

//what does pets.length return?
//what does pets[99] return?
```

&nbsp;

***** We would say this array has holes.
---
###Array Helper Methods
There's quite a few array helper methods. You do **not** need to remember every method, but here's a complete list:
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#Methods

---
### Notable***** Helper Methods
```js
//returns a string with each element separated by a comma
a.toString()

//returns a string with each element separated by param
//default parameter is a comma
a.join(param)

//removes and returns the last item from the array
a.pop()

//adds one or more items to the end and returns new length
a.push(item1, ..., itemN)
```

***** Many popular programming languages have these methods, often with the same name.
---
```js
//reverses the array
a.reverse()

//removes and returns the first item
a.shift()

//adds one or more items to the start and returns new length
a.unshift(item1, ..., itemN)
```
*****Besides `toString()` and `join()`, these methods mutate, *i.e.* modify, the original array.

---
![GeneralAssemb.ly](../../img/icons/code_along.png)

In `Node`'s console, let's practice using the array helper methods. We're going to decode a secret message.

---
### Part 1. Array Creation and the .push() Method
```js
var message = [];

message.push(8);
=> 1
message.push('r', 'e', 'b', 'm', 'u');
=> 6
message.push('n', 's', 'i', 'A', 'G', 'K');
=> 12

message;
=> [ 8, 'r', 'e', 'b', 'm', 'u', 'n',
    's', 'i', 'A', 'G', 'K' ]
```

---
### Part 2. .pop(), .shift(), and .unshift()
```js
message.pop();
=> 'K'

message.shift();
=> 8

message.unshift(1);
=> 11
```

---
### Part 3. Array Reversal Using .reverse()
```js
message.reverse();
=> [ 'G', 'A', 'i', 's', 'n', 'u',
    'm', 'b', 'e', 'r', 1 ]
```

---
### Part 4. Turning an Array into a String using .join()
```js
message.join(' ');
=> 'G A i s n u m b e r 1'
```

&nbsp;

***** Although I agree, I can't take credit for the cheesiness of this exercise.

---
## Iterating through an Array
Iterating through an array is a very common (and useful) practice in programming. Anytime we have an array, we will almost always iterate through the elements one at a time.

---
### Iterating using a For Loop
We can***** manually iterate over the elements of an array using a `for` loop:
```js
var articleTopics = ['cat videos', 'news', 'gossip'];
for (var i = 0; i < articleTopics.length; i++) {
    console.log(articleTopics[i]);
}
```
```js
var articleTopics = ['cat videos', 'news', 'gossip'];
//what's the difference between this and the top example?
for (var i = 2; i < articleTopics.length; i++) {
    console.log(articleTopics[i]);
}
```
*****We will very rarely use this. There are simply better methods, with much cleaner syntax, to iterate through an array.

---
### Array Iteration Methods
JavaScript arrays have several *iteration* methods. Many of these methods require a function to be passed in as an argument.

&nbsp;

We refer to this as a *callback* function; this is very common in JavaScript. Each element in the array has the statements in the function body applied to it individually.

---
### forEach() Method
This syntax is much cleaner than the `for` loop we just saw:
```js
var articleTopics = ['cat videos', 'news', 'gossip'];
articleTopics.forEach(function(topic) {
    console.log(topic);
});
```
Take a look at the documentation: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach

---
![GeneralAssemb.ly](../../img/icons/code_along.png)

## Array Iteration Methods

---
### Reading Documentation
Being able to read documentation and skim it quickly is extremely important. It's part of **eating your vegetables** as an engineer.

&nbsp;

We'll usually skim  first to learn as much as needed for the moment. Later, we can go back to fill in any missing details.

---
### Research
You have eight minutes to skim the documentation on MDN (Mozilla's Developer Network) for:

* `.every()` - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every
* `.some()` - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some
* `.filter()` - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter
* `.map()` - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map

---
### Part 1. Setup
Create an `exercise.js` file in your class 2 folder, and let's create two arrays.
```js
var prices = [];
prices.push(20, 44, 62, 80, 100);
console.log(prices);

var shirtColors = [];
shirtColors.push("red", "blue", "pink", "neon");
console.log(shirtColors);
```

---
### Part 2. .every()
The `.every()` method tests whether **all** elements in an array pass the test implemented by the provided function.
```js
var allLessThanFifty = prices.every(function(price) {
  return price < 50;
});

console.log("allLessThanFifty", allLessThanFifty);


var allRedShirts = shirtColors.every(function(color) {
  return color === "red";
});

console.log("allRedShirts", allRedShirts);
```

---
### Part 3. .some()
The `.some()` method tests whether **an** element in the array passes the test implemented by the provided function.
```js
var someLessThanFifty = prices.some(function(price) {
  return price < 50;
});

console.log("someLessThanFifty", someLessThanFifty);
```

---
### Part 4. .filter()
The `.filter()` method **creates a new array** with all elements that pass the test implemented by the provided function. This method does not mutate the original array.
```js
var lowPrices = prices.filter(function(price) {
  return price < 50;
});

console.log("lowPrices", lowPrices);
```

---
### Part 5. .map()
The `.map()` method creates a new array with the results of calling a provided function on every element in the original array.
```js
var pricesDiscounted = prices.map(function(price) {
  return price * 0.9;
});

console.log("pricesDiscounted", pricesDiscounted);


var shirtTitles = shirtColors.map(function(color) {
  return color + " shirt";
});

console.log("shirtTitles", shirtTitles);
```