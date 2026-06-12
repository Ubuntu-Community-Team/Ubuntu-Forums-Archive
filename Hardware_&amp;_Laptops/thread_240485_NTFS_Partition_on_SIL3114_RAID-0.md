---
title: "NTFS Partition on SIL3114 RAID-0"
date: 2006-08-20
forum: Hardware &amp; Laptops
---

### Post by budious on 2006-08-20
My setup is an Abit K8V MAX-3 motherboard which features an onboard Silicon Image SATA RAID controller. I have 2x 74GB WD Raptors setup in RAID-0 which is home to my current NTFS partition. My third drive is a 160GB Samsung IDE drive which I want to install ubuntu.

Booting from live dvd the hardware is detected, both sata drives are detected, and the raid volume is shown on the partition list of first sata drive. However, the file system shows up as unknown and has unaccessible status which cannot be enabled. Reference screenshot below.

[[IMG]http://img99.imageshack.us/img99/465/screenshotbx7.th.png[/IMG]](http://img99.imageshack.us/my.php?image=screenshotbx7.png)

Ideally, I want to have the NTFS partition detected by linux and mounted as /ntfs in the linux file system. Currently, I have the raid volume setup as the boot volume, but I could switch it to the IDE to install Grub to dual boot if necessary. I assume if this is resolved it would work either way though.

Any thoughts?

---

