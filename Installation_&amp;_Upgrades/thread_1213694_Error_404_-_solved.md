---
title: "Error 404 - solved"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by dougalkerr on 2009-07-15
I had a problem yesterday not getting to complete downloads for upgrades. Tried a couple of things till...

I managed to solve the problem. It seems the fault lies with the proxy setting. I usually use 'Automatic Proxy' setting of [http://www.../local/autproxy.pac](http://www.../local/autproxy.pac) or .php but, for some reason the system won't allow upgrades through this path so I have to enter a 'Manual Proxy' route, proxy0... :Port,8080 (syntax is different obviously to keep proxy private). It works... all software source paths now available... thanks for the input.

---

