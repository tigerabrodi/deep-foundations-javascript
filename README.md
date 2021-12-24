# Types

## Primitive Types:
- Everything is not an object but can behave like an object.
- Variables do not have types, its values do.

## typeof operator:
- Default value of variables is undefined
- Undefined means that the variables currently has not value, not that it has no value.
- Use isArray to check if an Array is an array.
- Use typeof which returns a string representing the type of the variable

## BigInt:
- BigInts and regular numbers do not mix and match very well. BigInts can grow infinitely large, they are in a seperate space that allows them to do so.

## Kinds of Emptiness:
- Undefined means there is a variable and at the moment it has no value
- Undeclared means it's never been created in any scope that we have access to.
- We can also have a variable that has never been initialized.

## Nan & isNan:
- Think of NaN as an invalid number. It is a number but an invalid number.
- NaN will compare unequal to itself every time
- JavaScript will coerce isNaN argument to a NaN value, an invalid number
- We do have Number.isNan, which definitely checks if it is an invalid number

## Negative Zero:
- -0 does exist in JavaScript.
- If you really need to check whether a number is 0 or -0 use Object.is which returns true or false.
- Object.is is sort quadruplets equal operators (Kyle's example)

## Fundamental Objects:
- You can use new to assign values using fundamental objects.
- Do not use new with String, Number or Boolean. These objects coerces their inputs to their type.


# Coercion

## Abstract Operations:
- toString takes it value and returns it in string form
- toNumber turns its input into a number. It also has weird behaviours, such as empty string turning into 0.
- toBoolean take an input and turns it into a boolean. Falsy values for toBooleans: "", 0 -0, null, NaN, false, undefined. toBoolean do not coerce the values, it just checks if its there or not.


## Philosophy of Coercion
- That JS is dynamic is one of the best parts with it. It is a multi-paradigm language, which makes it so powerful.
- Think of implicit as abstracted


## Equality
- Double equal is gonna allow coercion when the types are different, while triple equals will not allow coercion.
- You can use double equals to check if a value is null, this will not just check for null but also undefined.
- Do not complain at double equals when you are making a nonsensical comparion, Numbers vs Strings.
- Do not use double equals with 0 or "", even strings with spaces only. Do not use it with non-primitives.


#Scope
- Scope means where to look for things
- Functions and block create scopes
- JS must parse/compile before run

- All the scopes JS has to deal with, is determined in compile time, not during run time, it is used at runtime but determined at compile time.

- When JS executes it's code, variables can either be in a source or target position. Source means, we try to retrieve the value of the variable, target means, we are assigning something to the variable.
- There is a process of look up for variables. If JS can not find a variable within its scope, it will go to the outer scope and look up the variable there.


# Scope & Function Expressions
- Function expression means that the function is assigned to a variable. Which you can use to call etc. The assigned variable will be a part of the global scope, while the function value, will have its own scope.
- Always prefer named function expressions. Why?: Self-reference to the function, recursion etc. Debuggable stack traces, self-documenting code.



# Advanced Scope
- IIFE Can be used to only assign a value once to a variable. Inside of the IIFE in that particular case, you can use a try - catch block.

- There are still use-cases for var. Let and const or block scoped, for localized usage.
- Var will be scoped to its outer function or the global scope.
- The Var keyword can be reused within its scope.

- Explicit let block, for its own scope.

- Const do come with problems

- Hoisting. When declaring with variables with var, JS says when the scopes starts, initialize it to undefined.
- When let hoists its variables into its block scope, it says create a location called teacher, but don't initialize it.
- TDZ error was invented for const. It should not be undefined and then later another value.


# Closure
- Closure is when a function "remembers" its lexical scope even when the function is executed outside that lexical scope.
- Closure, when a function is able to hold on to scopes as reference, it is not magical, rather, that is closure!
- Closure is preservance of the linkage to the variable

- The idea of a module, is that there are things that are public and private, aka the public API.
- The module pattern requires the concept of encapsulation.
- Encapsulation means hiding data and behaviour. You should have some control over what is hidden and what is not, control over visibility of your data.



# Objects
- A function's "this" references the execution context for that call, determined entirely by how the function was called.
- How was the function called? Not the definition of the function!

- 4 ways to invoke a function in JavaScript

- Invoking a function with the .call method. The first argument will be an object, who's "this" context will be used. The rest arguments are the parameters of the particular function that is getting invoked.
- Invoking a function with the .bind method. The argument is the explicit object's this context we wanna use. We are here enforcing the context, we lose flexibility but gain predictability, since we know have explicitly set the "this" context for the function.

- Using "new" keyword to create an object, also called "constructor calls". 1. Create a brand new object. 2. Link that object to another object. 3. Calls the function with "this" set to the new object. If function does not return an object, it assumes return of "this" keyword.

- Default way of invoking a function, the "this" of the function will be used.

- Determining where "this" context belong to when invoking a function. 1. Function called with "new", newly created object will be the "this" keyword. 2. Function called with call, apply or bind, if so, the context object specified will be used. 3. If function is called on a context object, like workshop.ask, then use that object as "this" context. 4. Default: global object, except in strict mode, where "this" is undefined.

- There is no such thing as "this" keyword in an arrow function, therefore it revolves lexically, it keeps going up to it's parent until it finds a function that defines a "this" keyword, and it will use the "this" keyword that is pointed at the function, the "this" context for that function.
