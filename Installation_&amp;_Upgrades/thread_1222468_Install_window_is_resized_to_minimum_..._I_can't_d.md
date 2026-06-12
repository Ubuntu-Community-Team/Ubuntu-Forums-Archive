---
title: "Install window is resized to minimum ... I can't do anything with it!"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by epp_b on 2009-07-24
I'm installing Ubuntu 9.04.  During working with the partitions, I just closed the "reading disks..." window just to get it out the way (I don't know if this has anything to do with my problem).

The install window I see is just this:

[img]http://img33.imageshack.us/img33/3686/screenshotinstallingsysv.png[/img]

Now, it seems the CD has stopped spinning and the hard drive is no longer being written to, so I guess the install is done ... but I can't do anything about it!

How do I resize the window or otherwise get it into a state in which I can actually see it and control it?

---

### Post by fbugnon on 2009-07-25
> **epp_b said:**
> I'm installing Ubuntu 9.04.  During working with the partitions, I just closed the "reading disks..." window just to get it out the way (I don't know if this has anything to do with my problem).

I think the installation program took it as a *cancel* order...  :)  but couldn't hand-it correctly and crashed, leaving you with this mini-window.

It looks like the installation it-self was not yet started, so the best to do would be to reboot and start over again.

---

### Post by epp_b on 2009-07-25
Ah... a new window pops up when it's finished installing, so it's all good (and it did install).  Thanks.

One more thing: I overwrote the MBR (intentionally).  How to I reinstall grub onto a SATA drive?

---

### Post by epp_b on 2009-07-25
Never mind, I found it.  I initially tested this setup in a VM.  I needed to use (hd0,2) on the metal for my particular disk structure, instead of (hd0,1) like on the VM.

Thanks for helping me help myself ;)

---

