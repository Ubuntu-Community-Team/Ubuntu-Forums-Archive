---
title: "disable discrete video card in ubuntu 14.04"
date: 2014-10-05
forum: Hardware
---

### Post by uther78 on 2014-10-05
Hi, I use ubuntu 10.04 because my laptop (hp pavilion dv6 3151sl) has switchable graphics (radeon hd 5650 and integrated hd 4250): When the video proprietary drivers are not installed, the discrete card overheats and ubuntu 10 is the last version of ubuntu that supports my card drivers.
Now i have to upgrade because of the end of 10.04 support.
I installed 14.04 and followed a guide for blacklisting radeon card (with editing of /etc/modprobe.d/blacklist.conf )
but dont worked.
the command 
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

only sometimes works.
What I have to do?

---

### Post by MartyBuntu on 2014-10-05
Ubuntu 12.04 (the original release) uses an older version of xorg and is still supported until 2017.

It's the newer version of xorg that breaks compatibility with Catalyst drivers for older AMD cards.

---

### Post by Vladlenin5000 on 2014-10-05
And if you really want to disable one of them, disable the integrated one (@BIOS). The HD5650 is still supported and better than in previous versions.

---

### Post by uther78 on 2014-10-06
> **Vladlenin5000 said:**
> And if you really want to disable one of them, disable the integrated one (@BIOS). The HD5650 is still supported and better than in previous versions.

Unfortunately my bios doesn't support bios card switching, not even after bios upgrade.

---

### Post by T.J. on 2014-10-06
You can try the open radeon driver and enable radeon dynamic power management.  I realize that is a not-so-helpful comment and I do apologise - but I no longer use 14.04.  You should be able to find the necessary information easily enough, though.

---

### Post by uther78 on 2014-10-06
I installed ubuntu 12.04 and during the installation and the after the boot the overheat problem dont happen. With sudo cat etc... the discrete video card is "dynamic off". Maybe automatically the last ubuntu 12.04 version disable it?

---

### Post by T.J. on 2014-10-06
Sorry i can't say what Ubuntu does, as I have abandoned Ubuntu entirely as of 12.04 (although I tested 14.04 out of curiosity).  What I can tell you is that if the dynamic management is off, the card is going to run hotter, because it is always drawing the full amount of power even when not under load.  You should be able to measure it with lmsensors if you want to find out for yourself.

---

### Post by uther78 on 2014-10-07
> **T.J. said:**
> Sorry i can't say what Ubuntu does, as I have abandoned Ubuntu entirely as of 12.04 (although I tested 14.04 out of curiosity).  What I can tell you is that if the dynamic management is off, the card is going to run hotter, because it is always drawing the full amount of power even when not under load.  You should be able to measure it with lmsensors if you want to find out for yourself.

Are you sure that dynamic off means that? In dynamic off mode the card dont overheats, even after 1 hour of use (when the card is on, it overheats fast and after a few minutes the fan produces noise).

---

