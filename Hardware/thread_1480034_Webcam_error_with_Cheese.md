---
title: "Webcam error with Cheese"
date: 2010-05-11
forum: Hardware
---

### Post by Elen-Sil on 2010-05-11
Hi!

I'm all new to Ubuntu, so I don't know what to look for to see if someone has had the same problem (sorry about that - I did search).

Problem:  My netbook, msi wind U100 now has the latest upgrade of Ubuntu (netbook Remix), but for some reason, the built-in webcam doesn't work. It did, when I had Windows installed on it, and a while after I installed Ubuntu (without any upgrades). Now I just get the message (no unit found). I figured it could be the gstreamer that is corrupt, but I have no idea how it works or how to change it or whatever you do.

If you know what the problem is, please guide me through it, I don't know much about this system.


Elen-Sil

---

### Post by khelben1979 on 2010-05-11
I looked [here]("http://event.msi.com/nb/u160/") to take a look at it's tech. specifications. It would be good to know something more about the hardware of that webcam, try:
```
lsusb
```
to see what it lists and post in this thread.

It might be that an Ubuntu update made you switch to a newer Linux kernel which is the reason to why your webcam don't work any more and if that's the case, take a look in your [Synaptic Package Manager]("http://en.wikipedia.org/wiki/Synaptic_package_manager") and search for kernel to see if you can downgrade to the previous Linux kernel.

---

