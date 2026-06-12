---
title: "Support for SSD as OS caching device (as with OSX Fusion drives)"
date: 2016-09-14
forum: Hardware
---

### Post by 99jetta on 2016-09-14
The subject is pretty much the question.  Two of my internal customers wish to set up such a rig for their (pending) new servers running 14.04 or 16.04.

Pointers to tech documents would be helpful.

I've used fscache for NFS caching ... but it ain't the same thing.

Oscar.

---

### Post by DuckHook on 2016-09-14
I looked into this a couple of years ago, but not since, so my recollection is pretty rusty.

The service you are looking for is called *bcache*. Description and instructions are as follows:

[https://wiki.ubuntu.com/ServerTeam/Bcache](https://wiki.ubuntu.com/ServerTeam/Bcache)

---

