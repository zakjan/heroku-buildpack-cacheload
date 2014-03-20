# heroku-buildpack-cacheload

Copy files from cache. Paths are read from `.buildcache` file in your project source code.

You should use this, if your project is pulling a lot of dependencies during each build. If you store them into cache and during build you just check if they haven't changed, your build time will reduce dramatically.

## Usage example

`$ heroku config:add BUILDPACK_URL=https://github.com/ddollar/heroku-buildpack-multi.git`

`.buildpacks`:

```
https://github.com/heroku/heroku-buildpack-nodejs
https://github.com/zakjan/heroku-buildpack-cacheload#1.0.1
https://github.com/kr/heroku-buildpack-inline
https://github.com/zakjan/heroku-buildpack-cachesave#1.0.1
```

`.buildcache`:

```
code/server/node_modules
code/client/node_modules
code/client/bower_components
```

## Troubleshooting

**How to clear the cache?**

Use `heroku-repo` plugin.

```
$ heroku plugins:install https://github.com/heroku/heroku-repo.git
$ heroku repo:purge_cache -a appname
```
