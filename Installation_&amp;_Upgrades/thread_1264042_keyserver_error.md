---
title: "keyserver error"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by Nick Payne on 2009-09-11
When I try to retrieve the key for Openoffice 3.1.1 installation:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247D1CFF

I get an error:

gpg: requesting key 247D1CFF from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

A ping or tracert to keyserver.ubuntu.com works ok, so it's not a connectivity problem. I tried yesterday and again today - some problem both times.

---

### Post by ticopelp on 2009-10-05
It's a bug, as far as I know: 

[https://bugs.launchpad.net/ubuntu-website/+bug/435193](https://bugs.launchpad.net/ubuntu-website/+bug/435193)

---

