---
title: "Connect to usb cd-drive"
date: 2008-11-04
forum: Hardware
---

### Post by Wiesje on 2008-11-04
Hi,

I've got a laptop without cd-drive (acer aspire one).
I want to connect an external cd-drive (with USB to IDE adapter) but where can I find it in my File Browser?
It doesn't show up.

Thanks from a Linux newbie

---

### Post by nixscripter on 2008-11-04
USB devices are usually treated as "fake" SCSI devices. See if you can identify the device after connecting it from the output of the **dmesg** command. It should be one of these: ```
ls /dev/sd*
```

---

### Post by Wiesje on 2008-11-05
Thanks for your reply!
```
dmesg 
``` results in a huge list.
```
ls /dev/sd*
``` results in /dva/sda /dva/sda1 /dva/sda2 /dva/sda3 /dva/sda5 /dva/sda6
But now: how to access the device?

---

### Post by nixscripter on 2008-11-05
I think the ls devices might actually be your hard drive, since it has partitions (sda and sda**1**, 2, etc).

Try filtering the output of dmesg a little bit: ```
dmesg | grep CD
``` and see if there's a CD-ROM device showing up.

---

