# caddy-anubis

caddy-anubis is a plugin that loads anubis for requests in order to slow down AI and Scraper traffic from destroying infrastucture.

I consider this current implementation more of a Proof-of-Concept. I am not sure how stable or well it works. This is my first Caddy plugin.

One major issue is the very first request after a Caddy start or restart, takes like 5 seconds till anubis kicks in. All subsequent requests, especially after clearing cookies, are near instant.

## Current usage

Just add an `anubis` to your caddyfile in the block you want the protection. currently I have not seen it work properly inside a `route` or `handler` block. But it works outside of those.

There is an optional `target` field you can set if you want to force the redirect elsewhere. It does a 302 redirect.

Example (also check the caddyfile in this repo, it is used for testing):

```caddy

:80 {
  anubis

  # or 

  anubis {
    target https://qwant.com
  }
}
```

## Credits

- [anubis](github.com/TecharoHQ/anubis) - the project that started all of this.
