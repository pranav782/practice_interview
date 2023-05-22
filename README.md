# practice_interview

console.log(1 + '2' + '2');
console.log(1 + +'2' + '2');
console.log(1 + -'1' + '2');
console.log(+'1' + '1' + '2');
console.log('A' - 'B' + '2');
console.log(typeof typeof 1);
console.log(typeof null);
console.log(typeof NaN);
console.log(typeof undefined);
console.log(false == '0');
console.log(false === '0');
console.log('2' - 2);

Currying in JavaScript is a technique used to transform a function with multiple arguments into a sequence of functions, each taking a single argument. It allows you to partially apply a function by fixing some of its arguments, resulting in a new function that accepts the remaining arguments.

function add(x) {
  return function(y) {
    return x + y;
  }
}

// Curried function
const addCurried = add(5); // Fixing the first argument as 5

console.log(addCurried(3)); // Output: 8

Currying allows you to create reusable functions with different levels of specificity. It enables you to create more specialized functions from more general functions by fixing some arguments. This technique is particularly useful in functional programming paradigms and situations where you want to create variations of a function with common arguments.

Functional programming: Mention that currying is commonly used in functional programming paradigms, where functions are treated as first-class citizens. It aligns with concepts like higher-order functions and function composition, allowing for more expressive and concise code


In JavaScript, every object has a property called prototype, which refers to another object. The prototype object is used to implement inheritance in JavaScript through a mechanism called prototype inheritance.

Prototype:

The prototype property is an object associated with a constructor function or an object instance.
It serves as a blueprint or template for creating new objects or instances.
The prototype object contains properties and methods that are shared among all instances created from the constructor function or object.
Prototype Inheritance:

Prototype inheritance allows objects to inherit properties and methods from their prototype objects.
When accessing a property or method on an object, JavaScript first checks if the object itself has that property or method. If not, it looks up the prototype chain.
The prototype chain is formed by linking objects together through their prototype property.
If the property or method is found in a higher level of the prototype chain, it is accessed and used.
This process continues up the prototype chain until the property or method is found or until the end of the chain is reached (where the prototype is null).
Here's an example to illustrate prototype inheritance:

javascript
Copy code
// Constructor function
function Person(name) {
  this.name = name;
}

// Adding a method to the prototype of Person
Person.prototype.greet = function() {
  console.log(`Hello, my name is ${this.name}.`);
};

// Creating an instance of Person
const john = new Person('John');

// Accessing the inherited method
john.greet(); // Output: Hello, my name is John.
In this example, the Person constructor function has a prototype object. We add a greet method to the prototype object, which is shared by all instances of Person. When we create an instance john using the new keyword, john inherits the greet method from its prototype (Person.prototype), allowing us to call john.greet().

Prototype inheritance provides a way to define shared properties and methods for objects, promoting code reusability and efficient memory usage. It allows objects to delegate to their prototypes for properties and methods they don't directly have.

The __proto__ and .prototype are both related to prototype-based inheritance in JavaScript, but they have different purposes and usage.

__proto__:

__proto__ is a non-standard property that exists on object instances.
It allows you to access the prototype of an object directly.
It provides a way to traverse the prototype chain and access the prototype object associated with an object instance.
Note that __proto__ is not standardized and its usage is discouraged. Instead, you should use the Object.getPrototypeOf() and Object.setPrototypeOf() methods to interact with prototypes in a standardized way.
.prototype:

.prototype is a property that exists on constructor functions.
It is used to define the prototype object that will be assigned to instances created from the constructor function.
It is not accessible directly on object instances but only on the constructor functions themselves.
The properties and methods added to the .prototype object become shared among all instances created from the constructor.
This is how prototype-based inheritance is implemented in JavaScript, as instances delegate to their constructor's prototype for property and method lookups.
In summary, __proto__ is a property on object instances that provides direct access to the prototype, while .prototype is a property on constructor functions used to define the prototype object that will be assigned to instances created from that constructor. The former is used to traverse the prototype chain, and the latter is used to establish the prototype chain and enable inheritance.

The spread operator and rest operator are both syntax features introduced in JavaScript that involve the use of the ellipsis (...) symbol. While they share a similar syntax, they have different purposes and usage contexts.

Spread Operator (...):

The spread operator is used to expand an iterable (such as an array or string) into individual elements.
It allows you to spread the elements of an array or object into another array, object, or function call.
When used with arrays, it can be used to concatenate arrays, create shallow copies, or pass array elements as individual arguments to a function.
When used with objects, it can be used to create shallow copies or merge multiple objects into a new object.
The spread operator can also be used with strings to split them into individual characters.
Example usages of the spread operator:

javascript
Copy code
// Concatenating arrays
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const combinedArray = [...arr1, ...arr2]; // [1, 2, 3, 4, 5, 6]

// Copying arrays
const originalArray = [1, 2, 3];
const copyArray = [...originalArray];

// Passing array elements as arguments
const numbers = [1, 2, 3];
console.log(...numbers); // 1 2 3
Rest Operator (...):

The rest operator allows you to represent an indefinite number of function arguments as an array.
It is used in function parameter definitions to capture multiple arguments into a single array.
The rest operator collects the remaining arguments passed to a function into an array, even if the number of arguments is unknown or variable.
It provides a convenient way to work with functions that can accept a varying number of arguments.
Example usages of the rest operator:

javascript
Copy code
// Collecting function arguments into an array
function sum(...numbers) {
  return numbers.reduce((total, num) => total + num, 0);
}

console.log(sum(1, 2, 3)); // 6
console.log(sum(4, 5, 6, 7)); // 22
In this example, the rest operator (...numbers) collects all the arguments passed to the sum function into an array named numbers. This allows the function to handle any number of arguments and perform the desired operation.

To summarize, the spread operator (...) is used to spread elements from an array, object, or string, while the rest operator (...) is used to gather individual function arguments into an array. They are versatile features that simplify working with collections of elements or function arguments in JavaScript

Certainly! Here are some additional examples of the spread and rest operators:

Spread Operator (...):

Concatenating arrays:
javascript
Copy code
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const combinedArray = [...arr1, ...arr2]; // [1, 2, 3, 4, 5, 6]
Copying arrays:
javascript
Copy code
const originalArray = [1, 2, 3];
const copyArray = [...originalArray];
Merging objects:
javascript
Copy code
const obj1 = { foo: 1, bar: 2 };
const obj2 = { baz: 3 };
const mergedObject = { ...obj1, ...obj2 }; // { foo: 1, bar: 2, baz: 3 }
Passing array elements as function arguments:
javascript
Copy code
const numbers = [1, 2, 3];
console.log(...numbers); // 1 2 3
Spreading a string into individual characters:
javascript
Copy code
const str = 'hello';
const characters = [...str]; // ['h', 'e', 'l', 'l', 'o']
Rest Operator (...):

Collecting function arguments into an array:
javascript
Copy code
function sum(...numbers) {
  return numbers.reduce((total, num) => total + num, 0);
}

console.log(sum(1, 2, 3)); // 6
console.log(sum(4, 5, 6, 7)); // 22
Gathering remaining function arguments into an array:
javascript
Copy code
function printNames(first, second, ...others) {
  console.log('First:', first);
  console.log('Second:', second);
  console.log('Others:', others);
}

printNames('John', 'Doe', 'Jane', 'Smith', 'Mike');
/*
Output:
First: John
Second: Doe
Others: ['Jane', 'Smith', 'Mike']
*/
Combining arrays using the rest operator:
javascript
Copy code
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const combinedArray = [...arr1, ...arr2]; // [1, 2, 3, 4, 5, 6]
Destructuring an array, capturing the remaining elements:
javascript
Copy code
const [first, second, ...remaining] = [1, 2, 3, 4, 5];
console.log(first); // 1
console.log(second); // 2
console.log(remaining); // [3, 4, 5]
These examples demonstrate various use cases for the spread and rest operators in JavaScript, highlighting their flexibility and usefulness in working with arrays, objects, strings, and function arguments.

1 < 2 < 3:
The first expression appears to compare three numbers: 1, 2, and 3. However, JavaScript evaluates this expression from left to right.

First, 1 < 2 is evaluated, which is true (true is equivalent to 1 in JavaScript). So far, the expression becomes true < 3.

In the second comparison, true is coerced into the number 1, so the expression becomes 1 < 3, which is true.

Therefore, the output of console.log(1 < 2 < 3) will be true.

3 > 2 > 1:
Similarly, the second expression is evaluated from left to right.

First, 3 > 2 is evaluated, which is also true. So far, the expression becomes true > 1.

However, here's where it gets tricky. Unlike the previous example, true is coerced into the number 1, but the comparison operator > does not perform a further comparison with 1. Instead, it compares 1 with 1.

Comparing 1 > 1 results in false because 1 is not greater than 1.

Therefore, the output of console.log(3 > 2 > 1) will be false.

In both cases, the result may seem counterintuitive. It's important to note that the comparison operators in JavaScript (<, >, <=, >=) are left-associative and evaluate expressions from left to right. Additionally, JavaScript performs implicit type coercion when necessary, which can lead to unexpected results. To avoid confusion, it's recommended to use strict equality operators (=== and !==) when comparing values.

console.log([] == []);
console.log([] === []);

for (var i = 0; i < 5; i++) {
  setTimeout(function() {
    console.log(i);
  }, 1000);
}

for (var i = 0; i < 5; i++) {
  (function(index) {
    setTimeout(function() {
      console.log(index);
    }, 1000);
  })(i);
}

In JavaScript, null and undefined are two special values that indicate the absence of a meaningful value. While they may appear similar, they have some differences in their behavior and usage.

undefined: The undefined value is automatically assigned to variables that have been declared but have not been assigned a value. It also represents the absence of a return value in functions that do not explicitly return anything. Additionally, undefined is the default value for function parameters that are not provided.
Example uses of undefined:

Declaring a variable without assigning a value to it.
When a function does not return a value explicitly

null: The null value is explicitly assigned to a variable to indicate the absence of an object value. It is often used as an intentional placeholder to indicate that a variable or property does not currently have a meaningful value.
Example uses of null:

Explicitly assigning an empty or non-existent object value.
Indicating the absence of a value in a variable or property.

To summarize:

undefined is a value that indicates the absence of an assigned value or a return value.
null is a value that represents the intentional absence of an object value.
In practice, you can use undefined when a variable hasn't been assigned a value or when a function does not return anything explicitly. On the other hand, you can use null when you want to explicitly indicate the absence of an object value or to reset a variable or property to an empty state.

In summary:

Synchronous programming executes tasks sequentially, one after another, blocking the program's execution.
Asynchronous programming allows tasks to execute concurrently, without blocking the program's execution, using callbacks, promises, or other asynchronous patterns.
Asynchronous programming is particularly useful when working with time-consuming operations, network requests, or any tasks that may take some time to complete. It helps prevent the program from becoming unresponsive and enables more efficient resource utilization.

Synchronous Programming:
Synchronous programming follows a sequential execution model where each task is executed one after another, blocking the execution until the current task is completed. In other words, the program waits for each operation to finish before moving on to the next one.

Example:

javascript
Copy code
console.log("Start");
console.log("Middle");
console.log("End");
In this synchronous example, the three console.log statements will execute in order: "Start" will be logged first, followed by "Middle", and finally "End". The program waits for each console.log statement to complete before moving on to the next one.

Asynchronous Programming:
Asynchronous programming allows multiple tasks to be executed concurrently without blocking the execution of the program. Instead of waiting for each task to complete, asynchronous operations are initiated and then continue with the next task without waiting for the result. When an asynchronous operation finishes, a callback function or a promise is used to handle the result.

Example:

javascript
Copy code
console.log("Start");
setTimeout(function() {
  console.log("Async Task");
}, 2000);
console.log("End");
In this asynchronous example, the setTimeout function is used to delay the execution of the callback function by 2000 milliseconds (2 seconds). The program continues to the next statement (console.log("End")) without waiting for the setTimeout operation to complete. After 2 seconds, the callback function is executed, and "Async Task" is logged to the console.

Another example of asynchronous programming is making an API request using the fetch function or performing file operations. These tasks are non-blocking, allowing the program to continue executing other statements while waiting for the asynchronous operation to complete.

In JavaScript, there are several methods available for iterating over objects and accessing their properties. Here are some commonly used methods:

for...in loop:
The for...in loop iterates over the enumerable properties of an object, including properties inherited from its prototype chain.

Example:

javascript
Copy code
const obj = { a: 1, b: 2, c: 3 };

for (let prop in obj) {
  console.log(prop + ": " + obj[prop]);
}
Object.keys():
The Object.keys() method returns an array of the object's own enumerable property names.

Example:

javascript
Copy code
const obj = { a: 1, b: 2, c: 3 };

Object.keys(obj).forEach(function(prop) {
  console.log(prop + ": " + obj[prop]);
});
Object.values():
The Object.values() method returns an array of the object's own enumerable property values.

Example:

javascript
Copy code
const obj = { a: 1, b: 2, c: 3 };

Object.values(obj).forEach(function(value) {
  console.log(value);
});
Object.entries():
The Object.entries() method returns an array of the object's own enumerable property key-value pairs.

Example:

javascript
Copy code
const obj = { a: 1, b: 2, c: 3 };

Object.entries(obj).forEach(function([key, value]) {
  console.log(key + ": " + value);
});
These methods provide different ways to iterate over the properties of an object. Choose the method that suits your specific use case, depending on whether you need to access the keys, values, or key-value pairs of the object.

for...of loop:
The for...of loop is a more concise way to iterate over an array, providing direct access to each element without needing an index.

Example:

javascript
Copy code
const arr = [1, 2, 3, 4, 5];

for (let element of arr) {
  console.log(element);
}



The some() and every() methods are array methods in JavaScript that allow you to check the elements of an array based on a specific condition. They both return a boolean value indicating whether the condition is true for at least one or all elements of the array, respectively.

some() method:
The some() method tests whether at least one element in the array satisfies the given condition. It returns true if the condition is met for any of the elements, and false otherwise.

Example:

javascript
Copy code
const arr = [1, 2, 3, 4, 5];

const hasEvenNumber = arr.some(function(element) {
  return element % 2 === 0;
});

console.log(hasEvenNumber); // Output: true
In this example, some() checks if there is at least one element in the array that is an even number. Since the array contains the number 2, which is even, the result is true.

every() method:
The every() method tests whether all elements in the array satisfy the given condition. It returns true only if the condition is met for every element in the array. If any element fails to meet the condition, it returns false.

Example:

javascript
Copy code
const arr = [1, 2, 3, 4, 5];

const allEvenNumbers = arr.every(function(element) {
  return element % 2 === 0;
});

console.log(allEvenNumbers); // Output: false
In this example, every() checks if all elements in the array are even numbers. Since the array contains the numbers 1, 3, and 5, which are not even, the result is false.



The event loop is a fundamental concept in JavaScript that enables the execution of asynchronous code and handles events and callbacks. It ensures that JavaScript remains single-threaded while allowing non-blocking operations, such as I/O operations and timers, to be executed efficiently.

Here's how the event loop works:

JavaScript maintains a call stack, which keeps track of the execution context of functions. It follows a Last-In-First-Out (LIFO) approach.

When JavaScript encounters an asynchronous operation, such as a timer or an I/O request, it delegates the operation to the browser's or runtime's internal components, which handle these tasks outside the JavaScript engine.

While the asynchronous operation is being performed, JavaScript continues to execute the remaining synchronous code in the call stack.

Once the asynchronous operation is completed, the result is placed in a task queue (also known as the callback queue or event queue). This queue holds tasks that are ready to be executed by the JavaScript engine.

The event loop constantly checks two things: the call stack and the task queue. If the call stack is empty, it takes the first task from the task queue and pushes it onto the call stack for execution.

The executed task may contain callbacks or event handlers, which are executed in turn. This process continues as long as there are tasks in the queue.

By following this event-driven model, the event loop ensures that asynchronous operations are executed in a non-blocking manner. It allows JavaScript to handle multiple events and callbacks concurrently without waiting for each operation to complete before moving on to the next one. This is crucial for handling tasks such as network requests, file operations, and user interactions without freezing the browser or blocking the execution of other code.

In summary, the event loop plays a crucial role in managing asynchronous operations in JavaScript, ensuring that they are executed in an efficient and non-blocking manner, while maintaining the single-threaded nature of JavaScript.

The some() and every() methods provide convenient ways to evaluate conditions on array elements. They are particularly useful when you need to determine if an array contains at least one element that satisfies a condition or if all elements meet a specific requirement.
