---
title: "intel gma 3150 not detected"
date: 2010-05-09
forum: Hardware
---

### Post by firdausyusari on 2010-05-09
i just installed 10.04 remix on my hp mini 210 netbook...
everything works fine,except the intel gma 3150...
it's not detected on proprietary drivers...
is there has any way to enable this driver...
tq...:(

---

### Post by firdausyusari on 2010-05-10
bump

---

### Post by bedgen on 2010-05-25
any solution?

---

### Post by jthighlander on 2010-06-08
Hi bedgen,

[It appears that support of the GMA 3150 chipset is included in version 2.10 of the Intel video driver.]("http://bbs.archlinux.org/viewtopic.php?id=89645")  Unfortunately, that version isn't part of Lucid or Maverick (but we can request the latter).

Debian sid (experimental) includes version 2.11, and I experimented by including sid's repository in a recent Lucid build and installing the driver (xserver-xorg-video-intel), which did install successfully.

I am receiving my own HP Mini 210 HD this week and will try it out there and re-post here as to my findings.

Nonetheless, even without the driver, the video should work, but performance will not be the best.

---

### Post by jthighlander on 2010-06-09
I've also submitted bug [591579]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/591579") to have 2.11 of the driver incorporated into Maverick.

---

### Post by Henry78 on 2010-08-05
There's also a PPA including version 2.11:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

---

