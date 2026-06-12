---
title: "3d acceleration on GMA950 macbook?"
date: 2008-07-16
forum: Hardware
---

### Post by smocksturr on 2008-07-16
hey gang
i'm currently running the i810 driver, though i did install xserver-xorg-video-intel.
glxgears is slow as bloody molasses, how can i enable 3d acceleration and/or desktop effects with this graphics card?

---

### Post by jimv on 2008-07-16
You could try downloading the drivers from Intel.

[http://www.intellinuxgraphics.org/index.html](http://www.intellinuxgraphics.org/index.html)

God be with you on the installation.

---

### Post by smocksturr on 2008-07-16
my lord
i think i'll stick with unaccelerated graphics
is there honestly any way to get it to work otherwise? i'm running feisty... should i do a complete reinstall with hardy heron?

---

### Post by phidia on 2008-07-16
> **smocksturr said:**
> my lord
i think i'll stick with unaccelerated graphics
is there honestly any way to get it to work otherwise? i'm running feisty... should i do a complete reinstall with hardy heron?

The l[ink at the bottom]("http://www.intellinuxgraphics.org/download.html") of the download page "(recommended to ordinary users)" looks doable-although it does look like it requires recompiling the kernel-kernel patching.

Thanks for that link jimv!

---

### Post by stchman on 2008-07-16
> **smocksturr said:**
> hey gang
i'm currently running the i810 driver, though i did install xserver-xorg-video-intel.
glxgears is slow as bloody molasses, how can i enable 3d acceleration and/or desktop effects with this graphics card?

That card should work OOB.  Are you using Hardy?

---

### Post by phidia on 2008-07-16
You probably want to read [this thread]("http://ubuntuforums.org/showthread.php?t=799647&highlight=GMA950") it's short and maybe pertinent.

---

### Post by mnml on 2009-01-30
to activate 3d acceleration you should try setting
**DefaultDepth	16**
in your /etc/X11/xorg.conf file.

---

