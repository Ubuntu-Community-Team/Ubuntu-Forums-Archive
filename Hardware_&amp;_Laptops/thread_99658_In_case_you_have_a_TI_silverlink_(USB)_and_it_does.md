---
title: "In case you have a TI silverlink (USB) and it doesn't work in Breezy"
date: 2005-12-06
forum: Hardware &amp; Laptops
---

### Post by penvzila on 2005-12-06
For some reason I could never get the version of tilp in the breezy repositories to work with my usb graphlink. It just freezes when I start it. So I figured I REALLY NEED this program, and decided to see if I could compile it myself. It worked. The repo version of tilp worked fine in Hoary, after I followed Evan McNAbb's instructions, but this time it wasn't enough.

First off, I had to install libglade-dev. I just used whatever one is in synaptic. You may have other dependencies not met, that ./configure should tell you about if it fails.

You will need the following files, or at least what is in the following files: tilp.tar.gz, and tilibs.tar.gz. Tilibs contains libticables, libtifiles, and libticalcs. I had to compile all three, before I could compile tilp.

Get them at ticalc.org:  [http://www.ticalc.org/pub/unix/]("http://www.ticalc.org/pub/unix/")

Unpack them, obviously.  Doesn't matter where, they will be deleted.

Now just compile the libs and then tilp, and tilp should work with usb support. You have to do the libs in some order I can't remember, but it will tell you by failing if one has to come first.

You may have to:

```

mknod /dev/tiusb0 c 115 16 && chmod 666 /dev/tiusb0 
``` 
just like in the past.

---

### Post by AcidTripp on 2005-12-07
Thanks a lot for the post.

For anyone that cares, I compiled in the following order:
libtifiles
libticables
libticalcs
tilp

---

