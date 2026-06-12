---
title: "Sata disk won't show up"
date: 2007-01-26
forum: Hardware &amp; Laptops
---

### Post by ungluun on 2007-01-26
Hi,

As I was running out of disk space I bought myself a sata(II) disk and a pci controller card (my mobo is relatively old).
I installed and formatted the drive;

#mkfs.ext3 /dev/sda1
#mount /dev/sda1 /media/sda1

Then I tried to write some data to it. It went well for the first Gb, but then the process locked up and the superblock was destroyed.
I tried reformatting a couple of times; didn't work; same problem over and over again.

Then I tried setting the sata to 1.5Gb speed with the included jumper.
Started the format, mount, write(the drive showed up in /media/sda1) process again.
Result: lockup after writing 79 mp3's...

When I rebooted linux showed no device in /dev/sda1
even " #ls /dev/s* " didn't show a thing.

What should I do?
:confused: 


ps: the drive isn't defect as it was tested and worked in another pc.
pps: I'm using ubuntu dapper
P4 2.67Ghz
S478 mobo
pci sata controller card (with also a working(:)) sata dvd-drive attached)


Thanks guys!!

---

### Post by taurus on 2007-01-26
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by ungluun on 2007-01-26
That command shows my ide disks: hda & hdd, but no sda...

btw: my controller card is the silicon image 3112, but it's supported isn't it?

---

