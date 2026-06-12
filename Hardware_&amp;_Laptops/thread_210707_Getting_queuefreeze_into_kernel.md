---
title: "Getting queuefreeze into kernel"
date: 2006-07-07
forum: Hardware &amp; Laptops
---

### Post by MikeyB on 2006-07-07
Greetings!

I've got a nice new IBM T60 and everything works perfectly right out of the box with Ubuntu 6.06 except for two things:
- hdaps needs to be upgraded to recognize the new T60 - easy to do myself
- kernel-patch-queuefreeze needs to be applied

I would think that since hdaps is in the distribution kernel queuefreeze would be as well finally, but no. :(

If I rebuild the kernel from the debian source, a couple things happen that prevent me from using the system *nicely*:
- Framebuffer no longer works at boot... it goes blank until X starts
- linux-restricted-modules no longer works. I've recompiled that too, but it doesn't help.l
- It builds as kernel-image-..., not linux-image-... consequently I have to do some adding to debian/control to get it to build.

This is driving me nuts... it would make my life complete to have the queuefreeze already in the dist kernel... who can I arrange that with? :)

Alternatively, can somebody tell me what I'm doing wrong?

My changes are located here:
[http://www.supermathie.net/~michael/linux-source-2.6.15-mikeyb.patch](http://www.supermathie.net/~michael/linux-source-2.6.15-mikeyb.patch)

and I'm building with 'make-kpkg --initrd kernel_image'

---

