---
title: "new Kernel -&gt; Gnome doesn't recognize USB Stick"
date: 2006-02-16
forum: Hardware &amp; Laptops
---

### Post by rohrbold on 2006-02-16
Hello together,

I compiled and installed a new 2.6.15 Kernel the Debian way:
```
make oldconfig
fakeroot make-kpkg --initrd binary
sudo dpkg -i kernel-image-2.6.15-mh2_10.00.Custom_i386.deb
```
The Kernel boots and behaves well but unfortunately it lacks some nice usability features like the automatic disk-popup if I plug a USB Stick into my laptop or the ZAxis scrolling with my touchpad. Both works out of the box with all Ubuntu kernels.
I was wondering what might be the issue and what Ubuntu does differently from me. Any ideas?

---

### Post by kaamos on 2006-02-16
2.6.14 and 15 have problems with pmount in ubuntu. The drive gets mounted, but does not appear is desktop and is not accessible through computer:///. It can be accessed from /media/ though.

---

