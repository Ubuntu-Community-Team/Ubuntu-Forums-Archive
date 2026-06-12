---
title: "only 2 choices of resolution"
date: 2009-10-24
forum: Hardware
---

### Post by bregale on 2009-10-24
hi after two days now trying to get my wifes laptop to accept  ubuntu i have instsalled 8.04 on , the only problem is i can not adjust the resolution there i only 800x600 and 640x80 i have tried all different ways even tried to edit xorg resulting in a unbootable system any help will be welcome.
the laptop is a advent celeron 1.73ghz
1 gig of ram
80 gig hard drive 
fully updated
  thanks

---

### Post by cilynx on 2009-10-25
What graphic card are we working with?

```
lspci|grep -i vga
```

---

### Post by bregale on 2009-10-25
graphics card is sis systems from what i can gather the system is booting on the default driver versa below is the details


01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)


thanks again

---

### Post by cilynx on 2009-10-25
I've managed to stay away from SiS for the last few years, so I don't have any direct advice.  A quick search gave me the following:

[http://ubuntuforums.org/showthread.php?t=958967](http://ubuntuforums.org/showthread.php?t=958967)
[http://ubuntuforums.org/showthread.php?t=1083182](http://ubuntuforums.org/showthread.php?t=1083182)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/332140](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/332140)

---

