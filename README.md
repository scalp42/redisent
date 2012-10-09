redisent
====

Sentinel aware Redis client.

Description
-----------

Redisent is a wrapper for the Redis client that fetches configuration
details from sentinels.

## Usage

Instead of passing a Redis URL, you have to pass an array with the
URLs of your Redis sentinels as the first parameter, then the name
of your master server (as defined in the sentinels configuration) as
the second parameter, and finally a hash of options to be used when
connecting to the master.

```ruby
# List of sentinels.
sentinels = ["redis://localhost:27379/",
             "redis://localhost:27380/",
             "redis://localhost:27381/"]

# Master server name as defined in sentinel.conf.
master = "server-1"

# Additional options for the master server.
options = { :timeout => 5, :password => "abcd" }

redis = Redisent.new(sentinels, master, options)
```

If the sentinels can't be reached, or if there is no master available,
you will get the exception `Redis::CannotConnectError`.

## Installation

You can install it using rubygems:

```
$ gem install redisent
```