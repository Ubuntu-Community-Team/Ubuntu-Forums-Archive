---
title: "Is it too late?"
date: 2008-07-29
forum: Hardware
---

### Post by darweth on 2008-07-29
Just installed the latest updates and rebooted.  This is what happened to one of my drives. I fear the worst, especially since it is a reiser partition.  

fsck 1.40.8 (13-Mar-2008)
/dev/sda2: clean, 62902/11091968 files, 18601217/22163675 blocks
Failed to open the device 'UUID=d7253cb3-d509-4b87-957f-7b068d3363c6': No such file or directory


fsck died with exit status 8


I cannot access it at all.  How can I attempt a manual repair or what can I do?  Thanks.

---

### Post by tuxxy on 2008-07-29
You could try running a manual **fsck -y** in mainteneance mode when you boot the system.

---

### Post by darweth on 2008-07-29
I don't know, my friend.  It keeps saying the drive does not exist or can't be find regardless of what kind of fsck or reiserfsck I run.  

Curious bit of info in the syslog?

```
Jul 29 10:52:51 bepogi-desktop kernel: [  140.188400] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
Jul 29 10:52:51 bepogi-desktop kernel: [  140.188463] ata1.01: BMDMA stat 0x64
Jul 29 10:52:51 bepogi-desktop kernel: [  140.189326] ata1.01: cmd c8/00:00:68:00:00/00:00:00:00:00/f0 tag 0 dma 131072 in
Jul 29 10:52:51 bepogi-desktop kernel: [  140.189327]          res 51/84:00:68:00:00/00:00:00:00:00/f0 Emask 0x10 (ATA bus error)
Jul 29 10:52:51 bepogi-desktop kernel: [  140.189393] ata1.01: status: { DRDY ERR }
Jul 29 10:52:51 bepogi-desktop kernel: [  140.189446] ata1.01: error: { ICRC ABRT }
Jul 29 10:52:51 bepogi-desktop kernel: [  140.189528] ata1: soft resetting link
Jul 29 10:52:51 bepogi-desktop kernel: [  140.376579] ata1.00: configured for UDMA/100
Jul 29 10:52:51 bepogi-desktop kernel: [  140.391661] ata1.01: configured for UDMA/33
Jul 29 10:52:51 bepogi-desktop kernel: [  140.391678] ata1: EH complete
Jul 29 10:52:51 bepogi-desktop kernel: [  140.479174] ata1.01: limiting speed to PIO4
Jul 29 10:52:51 bepogi-desktop kernel: [  140.479180] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
Jul 29 10:52:51 bepogi-desktop kernel: [  140.479241] ata1.01: BMDMA stat 0x64
Jul 29 10:52:51 bepogi-desktop kernel: [  140.479297] ata1.01: cmd c8/00:00:68:00:00/00:00:00:00:00/f0 tag 0 dma 131072 in
Jul 29 10:52:51 bepogi-desktop kernel: [  140.479298]          res 51/84:00:68:00:00/00:00:00:00:00/f0 Emask 0x10 (ATA bus error)
Jul 29 10:52:51 bepogi-desktop kernel: [  140.479364] ata1.01: status: { DRDY ERR }
Jul 29 10:52:51 bepogi-desktop kernel: [  140.479416] ata1.01: error: { ICRC ABRT }
Jul 29 10:52:51 bepogi-desktop kernel: [  140.479498] ata1: soft resetting link
Jul 29 10:52:51 bepogi-desktop kernel: [  140.667982] ata1.00: configured for UDMA/100
Jul 29 10:52:51 bepogi-desktop kernel: [  140.683075] ata1.01: configured for PIO4
Jul 29 10:52:51 bepogi-desktop kernel: [  140.683092] ata1: EH complete
```

---

### Post by darweth on 2008-07-29
A pic.  No idea if it is relevant.

---

### Post by darweth on 2008-07-29
I got rid of the UUID in Fstab and used /dev/sdb1.  Same problem. :(  I am doomed. :( :(

---

### Post by darweth on 2008-07-29
Ladies and gentlemen!  GOD EXISTS!  HALLELUJAH!   I opened up the box and tightened some cables and wiped some dust and it is BACK!!!!  I am going to back it up now ASAP to prevent this atheistic terror from striking me again.

Who know an Ubuntu update was powerful enough to move physical cables?  Wow.

Thank you.

---

### Post by gjoellee on 2008-07-29
Yes, it is important to maintain your computer ^^

---

