---
title: "Ubuntu doesn't show External Hard Drive"
date: 2009-09-12
forum: Hardware
---

### Post by pedrotome on 2009-09-12
Hi,
First, I'd like to state this problem needs an Urgent solution. :)

I have an external HDD which Ubuntu always recognized until it stopped doing it...
I ran sudo fdisk -l and one of the drives listed was the external hdd:

```
Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b3fa764

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001    7  HPFS/NTFS
pulsecloud@ubuntu:~$ lsusb
Bus 001 Device 009: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 001 Device 004: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```so I guess Ubuntu recognizes it but doesn't show it...
Also, the drive is fine: I tested it in my Windows XP and all was alright.

So... what can I do? Should I worry?

I'm running Ubutnu Jaunty, installed with Wubi.


Oh, as a side question: is it bad to have an external hard drive running (being written to) all night long?

Thanks,
Pedro

---

### Post by SunnyRabbiera on 2009-09-12
Yeh you may wish to shut your external down every so often.
Did you shut your external down before loading ubuntu?
Try that.
What filesystem does your external use?

---

### Post by pedrotome on 2009-09-12
I left both the computer and the Ext. HDD on. I was downloading some stuff to the drive, so I could keep my PC clean (only 80GB of total memory. For Ubuntu and Vista!).

The drive uses NTSC.

---

### Post by SunnyRabbiera on 2009-09-12
> **pedrotome said:**
> I left both the computer and the Ext. HDD on. I was downloading some stuff to the drive, so I could keep my PC clean (only 80GB of total memory. For Ubuntu and Vista!).

The drive uses NTSC.

Firstly I suggest you install ntfs-config, it might help.
Secondly after installing ntfs-config shut down your system and turn your external off, after that restart Ubuntu then after it boots try turning your external on.
Heres how to install software in Ubuntu:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Please note:
Normally ubuntu is good at windows drives and NTFS systems, but sometimes it doesnt pick them up right away.

---

### Post by pedrotome on 2009-09-12
It's fine now. I just restarted the computer and it was all back to normal.
Thanks, though. :)



[CENTER][SIZE=7]:::SOLVED:::
[/SIZE][/CENTER]

---

