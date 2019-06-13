# The Basics

Swift is the new Programming language from Apple that was 
announced at the Apple World Wide Developer Conference on
Jun 2, 2014. Unlike Apple's previous development language
Objective-C, Swift is not a super set of C. However,
Swift can interoperate easily with C and Objective-C code.
Swift has it's own implementation of all familiar fundamental
types from C and Objective-C, but also adds some new fundamental
types including: Tuples, Function Types and Optional Types.

Swift is a type-safe language. Some languages like Javascript will
 not check the types of variables you use and will only 
alert you to the problem when they are used incorrectly at runtime.
Conversely, Swift's compiler will alert you when you misuse a type
by failing your build immediately when an error is found. For example,
If you try to pass a value of type Double into a function parameter
that expects an Integer type the compiler will immediately let you 
know that this is not possible. This type of type checking, though
sometimes frustrating, type checking helps to eliminate misunderstandings
between the developer writing code and the compiler which is interpreting
that code for the machine it will be run on.

## Constants and Variables

Swift allows you to declare constant and variables. You should
prefer constants over variables where possible in order to make
clear the intent and use behind the value and to eliminate any 
ambiguity around whether or not the value may change at some point.

You can declare constants and variables with almost any character, including
Unicode characters, but don't declare them with emojis unless you want to piss
off your co-workers or anyone else who might be reading your code. 

## Integers

Integers are whole numbers like 47 and -100. Integers can be Signed 
(meaning they can have values that are either positive, zero or negative)
or they can be Unsigned (which means they can only have values that are 
positive or zero).

You can represent these values in 8, 16, 32 and 64 bit forms. 

For example:
The minimum value of UInt8 (pronounced "Unsigned 8 Bit Integer") is 0
and the maximum value of of an Unsigned 8 Bit Integer is 255.

For the most part you will not need to pick a specific integer type because
Swift provides the Int (uppercased I) type. This type will use a representation
of the value that matches the current platform's native word size.

On a 32-bit platform, Int is the same size as Int32.
On a 64-bit platform, Int is the same size as Int64.

UInt is Swift's Unsigned Integer type which has the same size as the
current platform's native word size.

On a 32-bit platform, UInt is the same size as UInt32.
On a 64-bit platform, UInt is the same size as UInt64.

`A Note from the Docs:
Use UInt only when you specifically need an unsigned integer type with 
the same size as the platform’s native word size. If this isn’t the 
case, Int is preferred, even when the values to be stored are known to be 
nonnegative. A consistent use of Int for integer values aids code 
interoperability, avoids the need to convert between different number 
types, and matches integer type inference.`

## Floating-Point Numbers

Floating-point numbers are numbers with a fractional component, such as 3.14159, 0.1, and -273.15.

Floating-point types can represent a much wider range of values than integer types, and can store numbers that are much larger or smaller than can be stored in an Int. Swift provides two signed floating-point number types:

Double represents a 64-bit floating-point number.
Float represents a 32-bit floating-point number.

`A Note from the Docs:
Double has a precision of at least 15 decimal digits, whereas the precision of Float can be as little as 6 decimal digits. The appropriate floating-point type to use depends on the nature and range of values you need to work with in your code. In situations where either type would be appropriate, Double is preferred.`

## Numeric Literals

Swift Numeric literals allow you to declare the same number in different ways. For example you can write the integer value One Thousand as either `1000` or as `1_000` to help with readability.

Taking it a step further, you can also represent the Integer value 17 in many different ways. You could simply initialize a constant with `17`, or you could use the binary notation using a `0b` prefix and represent 17 as `0b10001`. 10001 is the binary representation of 17 and `0b` is the prefix that tells Swift you want to declare a binary value.

You can represent an Octal with the prefix `0o`. An octal representation of 17 in swift would be `0o21`.

And finally you can represent a hexadecimal number with the prefix `0x`. Therefore, a swift Integer literal in hexadecimal notation for a value of 17 would be `0x11`.

Floating point literals can also be represented easily with some syntactic sugar.

For decimal numbers with an exponent of exp, the base number is multiplied by 10exp:

1.25e2 means 1.25 x 10^2, or 125.0.
1.25e-2 means 1.25 x 10^-2, or 0.0125.

For hexadecimal numbers with an exponent of exp, the base number is multiplied by 2^exp:

0xFp2 means 15 x 2^2, or 60.0.
0xFp-2 means 15 x 2^-2, or 3.75.

## Numeric Type Conversion

You should use the `Int` type for general-purpose integer constants and variables even if you you know those values will be nonnegative. Since `Int` is the default Integer type these values will be more interoperable.

You should use other more specific types only if they are needed for the task at hand because of outside factors like  explicitly sized data from an external source, because of memory usage or other necessary optimizations. If you use explicitly sized types in these situations it can help catch problems with accidental value overflows.


## Assertions and Preconditions

Assertions and preconditions are checks that happen at runtime. You use them to make sure an essential condition is satisfied before executing any further code. If the Boolean condition in the assertion or precondition evaluates to true, code execution continues as usual. If the condition evaluates to false, the current state of the program is invalid; code execution ends, and your app is terminated.

You use assertions and preconditions to express the assumptions you make and the expectations you have while coding, so you can include them as part of your code. Assertions help you find mistakes and incorrect assumptions during development, and preconditions help you detect issues in production.

In addition to verifying your expectations at runtime, assertions and preconditions also become a useful form of documentation within the code. Unlike the error conditions discussed in Error Handling above, assertions and preconditions aren’t used for recoverable or expected errors. Because a failed assertion or precondition indicates an invalid program state, there’s no way to catch a failed assertion.

Using assertions and preconditions isn’t a substitute for designing your code in such a way that invalid conditions are unlikely to arise. However, using them to enforce valid data and state causes your app to terminate more predictably if an invalid state occurs, and helps make the problem easier to debug. Stopping execution as soon as an invalid state is detected also helps limit the damage caused by that invalid state.

The difference between assertions and preconditions is in when they’re checked: Assertions are checked only in debug builds, but preconditions are checked in both debug and production builds. In production builds, the condition inside an assertion isn’t evaluated. This means you can use as many assertions as you want during your development process, without impacting performance in production.

Sources:
https://docs.swift.org/swift-book/LanguageGuide/TheBasics.html

