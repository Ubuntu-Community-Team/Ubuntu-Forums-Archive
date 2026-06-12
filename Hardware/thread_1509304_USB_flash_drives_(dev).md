---
title: "USB flash drives (/dev)"
date: 2010-06-14
forum: Hardware
---

### Post by TomAbada on 2010-06-14
i need to know 
that a certain USB that i plug in my PC
what sdX is it exacly ??
sda ? sdb ? sdc ? etc.....

thanks in advance

---

### Post by sikander3786 on 2010-06-14
```

sudo fdisk -l

```

Simple.

Regards.

---

### Post by sandyvong on 2010-06-14
SDX seems to be a midi audio file.Sounds more like you are looking for this    [http://en.wikipedia.org/wiki/Self-extracting_archive](http://en.wikipedia.org/wiki/Self-extracting_archive)

---

### Post by C.S.Cameron on 2010-06-14
Or you can start gparted and look there.

---

### Post by quadproc on 2010-06-14
> **TomAbada said:**
> ...
what sdX is it exacly ??
sda ? sdb ? sdc ? etc.....

thanks in advance
Other posters have offered some good answers and I wanted to add one thing: the /dev designator can be different every time that the system boots, and it might change while running if you unmount it, remove or install some other removable device, and remount the USB drive.  The moral of this story is: do not depend on the sdX designator!

quadproc

---

### Post by alexshr on 2010-06-14
```

$ dmesg | grep sda

```if you find the sda then the device is there.

---

