# Laravel ETag

[![Latest Version on Packagist](https://img.shields.io/packagist/v/divtag/laravel-etag.svg?style=flat-square)](https://packagist.org/packages/divtag/laravel-etag)
[![Build Status](https://img.shields.io/travis/divtag-nl/laravel-etag/master.svg?style=flat-square)](https://travis-ci.org/divtag-nl/laravel-etag)
[![Quality Score](https://img.shields.io/scrutinizer/g/divtag-nl/laravel-etag.svg?style=flat-square)](https://scrutinizer-ci.com/g/divtag-nl/laravel-etag)
[![Total Downloads](https://img.shields.io/packagist/dt/divtag/laravel-etag.svg?style=flat-square)](https://packagist.org/packages/divtag/laravel-etag)

This package provides a middleware which can automatically generate and add an [`ETag`](https://en.wikipedia.org/wiki/HTTP_ETag) header to responses and respond with a `304 Not Modified` response when needed. 

## Installation

You can install the package via composer:

```bash
composer require divtag/laravel-etag
```

## Usage

When you assign the middlware to a route the package will take care of generating the `ETag` header and responding with a `304 Not Modified` response when needed.

``` php
Route::get('/', function () {
    return view('welcome');
})->middleware('etag');
```

You can still take care of generating the `ETag` header in your own code. When an `ETag` header is already attached to the response, the package will skip generating the `ETag` and just handle the responding with a `304 Not Modified` response when needed.

``` php
Route::get('/', function () {
    return response('foobar')
        ->header('ETag', 'W/"foobar"');
})->middleware('etag');
```

### Testing

``` bash
composer test
```

### Security

If you discover any security related issues, please email machiel@divtag.nl instead of using the issue tracker.

## Credits

- [All Contributors](../../contributors)

## About us

[Divtag](https://www.divtag.nl/) is a digital agency based in Drunen, the Netherlands. As part of [MPO Ventures](https://www.mpo-ventures.com/) we are working day in, day out at very exciting projects and products. Having any questions about our services or open vacancies? Feel free to contact us.

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
