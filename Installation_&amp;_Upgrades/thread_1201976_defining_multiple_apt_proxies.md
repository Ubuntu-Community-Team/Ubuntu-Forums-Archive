---
title: "defining multiple apt proxies"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by freakalad on 2009-07-01
Been using apt-cacher-ng at home & work for quite some time now. 
Absolutely FANTASTIC! Especially if either have several debian-based systems on the same network, or if you frequently build & test VM systems.

The problem I've got, is that I have a netbook & laptop that I use at both sites, and I have to reconfigure my proxy at every site.

A simple solution, I guess, would be to have a script that would set the proxy for each environment, but I was hoping to specify multiple proxies in the single config file.

The config for /etc/apt/apt.conf.d/00proxy
@ home: Acquire::http { Proxy "http://10.0.0.16:3142"; };
@ work, Acquire::http { Proxy "http://192.168.0.160:3142"; };

will start working on a script, but was hoping there was a simpler solution off the bat

---

### Post by islandlinux on 2011-10-26
I agree: apt-cacher-ng and location specific proxies would be great. I use a laptop in different environments where this functionality would be useful.

However the functionality does not exist (yet).

I tried added multiple proxies in the hope that if the first failed then the second would be tried. Only the last entry is used; all others are ignored. Having functionality to try listed proxies in order with an optional "no-proxy" as the last in the list would be optimal for me.

---

