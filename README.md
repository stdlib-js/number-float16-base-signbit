<!--

@license Apache-2.0

Copyright (c) 2025 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# signbit

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Return a boolean indicating if the sign bit for a [half-precision floating-point number][ieee754] is on (true) or off (false).

<section class="installation">

## Installation

```bash
npm install @stdlib/number-float16-base-signbit
```

Alternatively,

-   To load the package in a website via a `script` tag without installation and bundlers, use the [ES Module][es-module] available on the [`esm`][esm-url] branch (see [README][esm-readme]).
-   If you are using Deno, visit the [`deno`][deno-url] branch (see [README][deno-readme] for usage intructions).
-   For use in Observable, or in browser/node environments, use the [Universal Module Definition (UMD)][umd] build available on the [`umd`][umd-url] branch (see [README][umd-readme]).

The [branches.md][branches-url] file summarizes the available branches and displays a diagram illustrating their relationships.

To view installation and usage instructions specific to each branch build, be sure to explicitly navigate to the respective README files on each branch, as linked to above.

</section>

<section class="usage">

## Usage

```javascript
var signbit = require( '@stdlib/number-float16-base-signbit' );
```

#### signbit( x )

Returns a boolean indicating if the sign bit for a [half-precision floating-point number][ieee754] is on (`true`) or off (`false`).

```javascript
var toFloat16 = require( '@stdlib/number-float64-base-to-float16' );

var bool = signbit( toFloat16( 4.0 ) );
// returns false

bool = signbit( toFloat16( -5.960464477539063e-8 ) );
// returns true

bool = signbit( 0.0 );
// returns false

bool = signbit( -0.0 );
// returns true
```

</section>

<!-- /.usage -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
var toFloat16 = require( '@stdlib/number-float64-base-to-float16' );
var uniform = require( '@stdlib/random-array-uniform' );
var map = require( '@stdlib/array-base-map' );
var logEachMap = require( '@stdlib/console-log-each-map' );
var signbit = require( '@stdlib/number-float16-base-signbit' );

// Create an array of random half-precision floating-point numbers:
var x = map( uniform( 100, -50.0, 50.0 ), toFloat16 );

// Determine whether the sign bit is on or off for each number:
logEachMap( 'x: %0.4f => %s', x, signbit );
```

</section>

<!-- /.examples -->

<!-- C interface documentation. -->

* * *

<section class="c">

## C APIs

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

</section>

<!-- /.intro -->

<!-- C usage documentation. -->

<section class="usage">

### Usage

```c
#include "stdlib/number/float16/base/signbit.h"
```

#### stdlib_base_float16_signbit( x )

Returns an integer indicating whether the sign bit for a half-precision floating-point number is on (`1`) or off (`0`).

```c
#include "stdlib/number/float16/ctor.h"
#include <stdint.h>

stdlib_float16_t x = stdlib_float16_from_bits( 51648 ); // => -11.5
int8_t out = stdlib_base_float16_signbit( x );
```

The function accepts the following arguments:

-   **x**: `[in] stdlib_float16_t` input value.

```c
int8_t stdlib_base_float16_signbit( const stdlib_float16_t x );
```

</section>

<!-- /.usage -->

<!-- C API usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

</section>

<!-- /.notes -->

<!-- C API usage examples. -->

<section class="examples">

### Examples

```c
#include "stdlib/number/float16/base/signbit.h"
#include "stdlib/number/float16/ctor.h"
#include "stdlib/number/float32/base/to_float16.h"
#include <stdint.h>
#include <stdio.h>
#include <inttypes.h>

int main( void ) {
    const float x[] = { 3.14f, -3.14f, 0.0f, -0.0f, 4.0f, 1.0f, -1.0f, 1.0e38f, -1.0e38f };

    stdlib_float16_t v;
    int8_t out;
    int i;
    for ( i = 0; i < 9; i++ ) {
        v = stdlib_base_float32_to_float16( x[ i ] );
        out = stdlib_base_float16_signbit( v );
        printf( "%f => signbit: %" PRId8 "\n", x[ i ], out );
    }
}
```

</section>

<!-- /.examples -->

</section>

<!-- /.c -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2026. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/number-float16-base-signbit.svg
[npm-url]: https://npmjs.org/package/@stdlib/number-float16-base-signbit

[test-image]: https://github.com/stdlib-js/number-float16-base-signbit/actions/workflows/test.yml/badge.svg?branch=v0.1.0
[test-url]: https://github.com/stdlib-js/number-float16-base-signbit/actions/workflows/test.yml?query=branch:v0.1.0

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/number-float16-base-signbit/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/number-float16-base-signbit?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/number-float16-base-signbit.svg
[dependencies-url]: https://david-dm.org/stdlib-js/number-float16-base-signbit/main

-->

[chat-image]: https://img.shields.io/badge/zulip-join_chat-brightgreen.svg
[chat-url]: https://stdlib.zulipchat.com

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/number-float16-base-signbit/tree/deno
[deno-readme]: https://github.com/stdlib-js/number-float16-base-signbit/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/number-float16-base-signbit/tree/umd
[umd-readme]: https://github.com/stdlib-js/number-float16-base-signbit/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/number-float16-base-signbit/tree/esm
[esm-readme]: https://github.com/stdlib-js/number-float16-base-signbit/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/number-float16-base-signbit/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/number-float16-base-signbit/main/LICENSE

[ieee754]: https://en.wikipedia.org/wiki/IEEE_754-1985

</section>

<!-- /.links -->
