---
title: "I can't find my usb dvd"
date: 2009-11-01
forum: Hardware
---

### Post by trytenn on 2009-11-01
Hello!
My eyes are bleeding from all the google I have done. I hope someone can help me.
I can't use the usb dvd driver. I have tried to play music cd's, burn the same, mount dvd's and nothing will work. I have understand so much that the fstab shouldn't be the problem (right?). The right model comes up when I type lshal, that is samsung SE-S224Q. Please help me with this I really need it to work. I have xubuntu 9.04 and an asus eeepc 901.

ps. I'm used ubuntu/linux for a year now, so I know a little but not to much.

```
$ lshal | grep DVD
  scsi.model = 'CDDVDW SE-S224Q'  (string) 
``````
$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 13fd:2040 Initio Corporation 
Bus 001 Device 007: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by trytenn on 2009-11-11
I upgraded my bios and then ubuntu to 9.10 and even installed gnome, but it still isn't working. The dvd works on a friends ubuntu (8.10 i think) and it worked when i had the pre-installed xandros dist (i could at least play dvd-movies, but I think I had problem burning dvd's). How do I know if the bios supports the dvd?

And when i try to burn a cd in gnome it looks like it's working. The dvd sounds like it's doing something and the progress-bar looks good. It ejects when it's finish but the cd is blank.

So is anyone out there?

---

