## 2.0.0.beta3
* Accept `intervals` array argument to provide your own custom intervals.
* Refactor the exponential backoff code into it's own class.
* Add specs for exponential backoff, randomization, and config.

## 2.0.0.beta2
* Raise not return on max elapsed time, also check for elapsed time after next interval is calculated and it goes over the max elapsed time.
* Add specs for `max_elapsed_time` and `max_interval`.

## 2.0.0.beta1
* Require ruby 2.0+.
* Default to random exponential backoff, removes the `interval` option. Exponential backoff is configurable via arguments.
* Allow configurable defaults via `#configure`.
* Change `Retriable.retriable` to `Retriable.retry`.
* Support `max_elapsed_time` termination.

## 1.4.1
* Fixes non kernel mode bug. Remove DSL class, move `#retriable` into Retriable module. Thanks @mkrogemann.

## 1.4.0
* By default, retriable doesn't monkey patch `Kernel`. If you want this functionality,
you can `require 'retriable/core_ext/kernel'.
* Upgrade minitest to 5.x.
* Refactor the DSL into it's own class.

## 1.3.3.1
* Allow sleep parameter to be a proc/lambda to allow for exponential backoff.

## 1.3.3
* sleep after executing the retry block, so there's no wait on the first call (molfar)

## 1.3.2
* Clean up option defaults.
* By default, rescue StandardError and Timeout::Error instead of [Exception](http://www.mikeperham.com/2012/03/03/the-perils-of-rescue-exception).

## 1.3.1
* Add `rake` dependency for travis-ci.
* Update gemspec summary and description.

## 1.3.0

* Rewrote a lot of the code with inspiration from [attempt](https://rubygems.org/gems/attempt).
* Add timeout option to the code block.
* Include in Kernel by default, but allow require 'retriable/no_kernel' to load a non kernel version.
* Renamed `:times` option to `:tries`.
* Renamed `:sleep` option to `:interval`.
* Renamed `:then` option to `:on_retry`.
* Removed other callbacks, you can wrap retriable in a begin/rescue/else/ensure block if you need that functionality. It avoids the need to define multiple Procs and makes the code more readable.
* Rewrote most of the README

## 1.2.0

* Forked the retryable-rb repo.
* Extend the Kernel module with the retriable method so you can use it anywhere without having to include it in every class.
* Update gemspec, Gemfile, and Raketask.
* Remove echoe dependency.
