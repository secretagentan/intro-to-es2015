# Group A

## let + const
- [let + const](https://github.com/lukehoban/es6features#let--const)
```
- Block-scoped binding constructs
- 'let' is the new 'var'
  - Declares a block scope local variable
  - Limited in scope to the block, statement, or expression on which it is used
  - Unlike var - which declares variables globally or locally to the entire function
  - Advantages: 
    - Cleaner code when inner functions are used 
  - Errors/Limitations:
    - Cannot be used globally
    - Redeclaring it within a block => SyntaxError (incl. switch statements)
    - Using same name for variable as parameter passed through the function => TypeError
    - "Temporal Dead Zones" - before the variable is declared
        - 'let' will hoist variable to top of the block, but referencing it before declaration
        => ReferenceError
```
```js
var x = 1;
function letTest() {
  if (true) {
    let x = 2;
    console.log(x);  // 2
  }
  console.log(x);  // 1
}
```
```
- Constant or 'const': block-scoped, similar to 'let' statements 
    - Is single-assignment - cannot reassign or redeclare
  - Creates a 'read-only' reference to the variable
  - Requires an initializer in declaration
  - Advantages: 
    - Can be global or local 
  - Errors/Limitations:
    - Cannot share a name with functions or variables in the same scope
    - All considerations re: temporal dead zones for let, apply to const
    - Overwriting an entire object throws an erro
        - HOWEVER - object keys are NOT protected (can assign new value to keys)
      - Same for arrays - can push new items into array, but cannot overwrite entire array
```
```js
// define NUM as a constant and give it the value 7
const NUM = 7;

// Reassign NUM
NUM = 20; // Uncaught TypeError: Assignment to constant variable.

// Redeclare 
const NUM = 20; // Uncaught SyntaxError: Identifier 'MY_FAV' has already been declared

var NUM = 20; // Uncaught SyntaxError: Identifier 'MY_FAV' has already been declared

```

## arrows
- [arrows](https://github.com/lukehoban/es6features#arrows)
```
 -A function shorthand using =>  , best suited for non-method functions.  
 -Always anonymous
 - Basic Syntax -- (params) => {statement}
      ---(params) => expression
      -parentheses are optional with one param   ( single param) => {statement} || single param => {statement}
      -a function with no params requires parentheses    () => {statement}
      
  - Doesnt define its own THIS value
  -Can't be used as a constructor, will throw error when used with 'new'  var foo = new Foo()  TypeError, Foo not a constructor.
  -  '{' immediately following => is treated as the start of a block, not the start of an object.  so wrap object literals in parentheses. 
            example(myObj = {string: "string',
                         boolean: true,
                         int: 4
                                                })    ....no parentheses would result in Undefined.
  -
                        
```

## Array.from()
- [Array.from()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from)

- creates a new Array instance from an array-like or iterable object.

- Parameters: 
- 1. arrayLike
- An array-like or iterable object to convert to an array.
- 2. mapFn
- Optional. Map function to call on every element of the array.
- 3. thisArg
- Optional. Value to use as this when executing mapFn.

```

Array.from("foo");
// ["f", "o", "o"]

```

- Example using optional map function as a second argument

```

Array.from([1, 2, 3], x => x + x);      
// [2, 4, 6]

```

## classes
- [classes](https://github.com/lukehoban/es6features#classes)
```
https://hacks.mozilla.org/2015/07/es6-in-depth-classes/ //Founder's blog post of classes.
JavaScript classes provide a much simpler and clealer syntax to create objects and deal with existing prototype-based inheritance. 

It is a way to group all methods relating to a class together while also cleaning the code.

class Polygon {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
  
  get area() {
    return this.calcArea();
  }

  calcArea() {
    return this.height * this.width;
  }
}

var square = new Polygon(2, 2);
const column = new Polygon(10, 2);

column.area = 20; // vs column.width * column.height = 20;

A class can group together all objects that share a similar trait. For instance, all electronics share the same
trait 'need for power'. So all electronics cou


```

## String.prototype.includes()
- [String.prototype.includes()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/includes)
```
My definition: The string.prototype.includes() method is a string method that takes 2 parameters, the first parameter is the 
string you would like to test against the original string. The second parameter takes a number, this number will determine the 
position of the starting point within the test string, proportionally to the index value of the test string. This method will return a boolean value.
Either true or false, and the method is case sensitive.

The includes() method determines whether one string may be found within another string,
returning true or false as appropriate.

examples: 
  var str = 'To be, or not to be, that is the question.';

  console.log(str.includes('question'));    // true
  console.log(str.includes('nonexistent')); // false
  console.log(str.includes('To be', 1));    // false


```
