---
title: "Can't mount externall HDD"
date: 2013-12-01
forum: Hardware
---

### Post by Worp8d on 2013-12-01
Hi,

I've been unable to mount external (USB) HDDs for a while now. Indicator LEDs on the drives show that they are connected and working but they never show up in the file manager. USB flash drives work fine. I've been reading around but I'm at a loss on this one. Any ideas?

(Lubuntu 13.10)

---

### Post by varunendra on 2013-12-03
Please disconnect the drive, wait about 10 seconds, reconnect, and when it appears to be 'connected and working', run the following commands and post back their outputs -
```
dmesg | tail -20
mount
sudo fdisk -l
```

---

