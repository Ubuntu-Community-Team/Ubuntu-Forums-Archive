---
title: "Tor Project"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by immortaldingo on 2008-12-07
[https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian](https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian)

I'm using intrepid.

Do I put "deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) intrepid main" into the terminal by itself or with "$ apt-get update"?

Do I need to verify the signature?

I'm new x.x.

---

### Post by snova on 2008-12-07
Tor is in the repositories already, it shouldn't be necessary. Just install via Synaptic the way you would anything else, and then continue their instructions.

(It goes in /etc/apt/sources.list, so you know. But really, unless you have a specific reason, just use Synaptic.)

---

