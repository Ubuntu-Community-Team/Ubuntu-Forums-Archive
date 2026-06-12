---
title: "Kubuntu 7.10 - USB drives not recognized"
date: 2007-11-21
forum: Hardware &amp; Laptops
---

### Post by pksdacheat on 2007-11-21
Hi there. I'm having a rather annoying problem with my gutsy distro running the kde desktop environment. Initially (for a couple weeks, at least) my laptop was recognizing my usb flash drive and external HD automatically. Now, when I plus them in, they aren't recognized at all (the flash drive's light doesn't come on).

I know these USB ports are working, as my mouse will work with either of them.

With my external HD plugged in and turned on, the output of "sudo fdisk -l" is as follows:

> Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris


As far as I can tell, that is only my internal HD, and the external is dead to my machine. Can anyone give me any advice on how to proceed? I'm not sure how to mount it manually, since fdisk isn't telling me what name or path I could use. I appreciate all the help. ](*,)

---

