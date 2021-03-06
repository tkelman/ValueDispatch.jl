## Value Dispatch

Function dispatch on value instead of type. Quite similar to Clojure's
[multimethods](http://clojure.org/multimethods).

Behold:

```jl
@dispatch fizzbuzz(n::Int) = (n % 3 == 0, n % 5 == 0)

@on (true,true)  fizzbuzz(n) = "fizzbuzz"
@on (true,false) fizzbuzz(n) = "fizz"
@on (false,true) fizzbuzz(n) = "buzz"
@on :default     fizzbuzz(n) = n

for i in 1:15
    println(fizzbuzz(i))
end
# 1
# 2
# fizz
# 4
# buzz
# fizz
# 7
# 8
# fizz
# buzz
# 11
# fizz
# 13
# 14
# fizzbuzz
```
