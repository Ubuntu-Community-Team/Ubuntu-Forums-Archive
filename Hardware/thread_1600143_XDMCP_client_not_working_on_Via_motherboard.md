---
title: "XDMCP client not working on Via motherboard"
date: 2010-10-18
forum: Hardware
---

### Post by JRV on 2010-10-18
I did a fresh install of Ubuntu 10.10 on a Via PC2500E motherboard (Model: ID-PCM7E).

I logged in, opened a terminal and installed Xephyr.

I ran Xephyr with my usual command:

   Xephyr :1 -query HOSTNAME -fullscreen -once

and I got the following error message:

Xephyr: ../../../../include/privates.h:122: dixGetPrivateAddr: Assertion `key->initialized' failed.
Aborted

After this I tried installing Xnest and it did not work to use XDMCP from within tsclient either.

---

