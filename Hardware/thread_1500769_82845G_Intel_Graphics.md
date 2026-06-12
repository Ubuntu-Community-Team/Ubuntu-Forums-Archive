---
title: "82845G Intel Graphics"
date: 2010-06-03
forum: Hardware
---

### Post by jedi22 on 2010-06-03
Hello everyone.

I'm trying to get the Intel 82845G Brookdale Graphics Controller working on Ubuntu.  I know there are other threads on a subject similar to this but I have found something very interesting.

So booting in Ubuntu, no dice.  So I went into recovery mode and dropped to a netroot shell. I typed startx and it actually worked!  Why does it not work when booted not in recovery mode.

Second try, I boot in sabayon and get a similar issue, so I do the same thing.  I type startx and I get a Graphic interface with 3 terminals.  Here is where it get's really interesting.  I then typed "glxgears" and it worked!  Meaning that direct rendering is working on this chipset.  I'm going to try and copy this xorg configuration to Ubuntu to see if it works there.

If you have anything to add, or if you just know how to get it working please tell me.

Cheers.

---

