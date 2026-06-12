---
title: "Removed a disk, computer won't boot"
date: 2013-09-11
forum: Hardware
---

### Post by skamarla on 2013-09-11
I'm stuck trying to recover my computer, please help!

My system used to have two disks: an older IDE disk, with Windows XP and an old Ubuntu installation, and a newer SATA disk, with a current Ubuntu. The older one started to give errors, but I wasn't too worried, since I hardly ever use Windows. But then the kernel upgrade started to take forever, because it got lots of errors while scanning the old disk.

So I decided to remove the IDE disk and keep just the SATA. Since then, I haven't been able to boot anymore. I first thought that the BIOS was still looking for something on the IDE that didn't exist any more, so I tried AHCI mode. It didn't work either, and I have been trying several variants on the BIOS, to no avail. The BIOS always detects the SATA DVD, but the hard disk isn't always detected.

I thought that the SATA disk probably didn't have a bootloader, so I tried booting with a Kubuntu live CD to run boot-repair and make it bootable. It took over an hour to boot, and even then, it didn't detect the hard disk. I have booted with System Rescue CD and booting takes a little shorter, but still over half an hour.

The Live CD kept giving errors like:

```
timeout: killing '/sbin/blkid -o udev -p ' ....
```


System Rescue CD gives the following errors while booting

```

udevadm settle - timeout of 180 seconds reached, the event queue contains:
/sys/devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/block/sda (1096)
/sys/devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/block/sda/sda1 (1097)
/sys/devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/block/sda/sda2 (1098)
/sys/devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/block/sda/sda3 (1099)
/sys/devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/block/sda/sda4 (1100)
/sys/devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/block/sda/sda5 (1101)
/sys/devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/block/sda/sda6 (1102)
/sys/devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/block/sda (1337)
udevd[162]; worker [189] unexpectedly returned with status 0x0100
```


After booting with System Rescue CD, I have managed to mount my home partition (it took a long time to mount, too), and I can access the files, so the disk seems to be good. Any ideas on what to do next? The motherboard is an Asus P5QC. I'm worried that the disk controller may have failed.

---

### Post by VMC on 2013-09-11
Sounds like your hard disk has problems. Or the cabling , but since you unplugged and re-connected the cables that should ruled that out.
Do you have a USB flash drive or USB hard disk that you could try, booting from the BIOS?

I have a small USB flash that has grub2 on it, just for stuff like this. That long boot time is an indication that either it can't find the MBR or hard disk errors.
Also try looking at *syslog*, *kern.log, dmesg* for indications. Remove the "quiet splash" from grub2 or hit the '*Esc*' key when booting to see any errors.

---

### Post by skamarla on 2013-09-21
I'm not sure whether it's the hard disk or the controller that has problems. It's too much of a coincidence for the two disks to fail at the same time!
Anyway, when I try to boot now, I get the following:

```
error:failure reading sector 0x41 from 'hd0'
grub rescue> ls
(hd0) (hd0,msdos4) (hd0,msdos3) (hd0,msdos1) (fd0)
```

When doing "ls (hd0,msdos3)/" I once got a directory listing, but the rest of the times I get "error:unknown filesystem."

Is there anything I can do to rule out either disk or controller, short of trying the disk on another PC?

---

### Post by VMC on 2013-09-21
From that listing, it only sees one hard drive, and not two. If you have two plugged, try removing the cable from one and try the listing again....
okay, I see, you pulled the old IDE drive out. If you know what partition linux is one, then try. for example:
```
configfile (hd0,1)/boot/grub/grub.cfg
``` Replace the '1' with what you think is your linux partition.

---

