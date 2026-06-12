---
title: "Grub error 15"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by 311005901 on 2009-02-20
Crash bang boom.
I turned on my computer today and I get

```
GRUB Loading Stage 1.5
GRUB loading, please wait.
Error 15
```

And I can't get anything to show up by pressing keys on the keyboard. I put in an Ubuntu live CD and select "boot/install", only to get ```

SQUASHFS error: Unable to read fragment cache block [27e431eb]
SQUASHFS error: Unable to read page, block 27e431eb, size a87c
SQUASHFS error: sb_bread failed reading block 0x9f936

```
There is also a series of numbers on the left counting higher constantly.

What is going on? Is this a HDD problem or an Ubuntu problem?

---

### Post by Pumalite on 2009-02-20
Check your drive/partitions with TestDisk:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Pumalite on 2009-02-20
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by 311005901 on 2009-02-20
Thanks Pumalite for the expedient response! :D

I looked at what you suggested, but sadly, I had no success with either... :(

> **Pumalite said:**
> Check your drive/partitions with TestDisk:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
I couldn't do this because I can't boot to anything, HDD or CD.

> **Pumalite said:**
> [http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)
I downloaded a Super Grub Disc img and RawWrote it onto a floppy. I then booted to the floppy and I get:
```
GRUB Loading stage2......Read Error_
```
Do I just have a bad HDD?

---

### Post by Pumalite on 2009-02-21
It looks like.Do a memtest and check the cables.

---

### Post by 311005901 on 2009-02-21
Is there a way to run Memtest without booting to GRUB?

---

### Post by bustherh on 2009-02-21
I had this same issue when I first tried to install ubuntu on my big machine.
Grub was installing on the wrong hard drive even though I chose the correct one during install, it has something to do with the way Bios reads the HDDs vs. the way ubuntu reads them.

I had three HDDs one had windows, the other had Linux and the third was just for storage. 
I installed ubuntu many times and always got the same error. 
Finally I unplugged my storage drive and installed one more time and it worked. when I plugged the storage drive back in everything was fine.

---

### Post by 311005901 on 2009-03-04
Whatever.

I've tried everything I could think of. I even brought it to school to get it checked out.
No luck.

It looks like the drive is a goner. :(


Anyway, thanks for everybody's help! :D
I'd rather know that its not fixable than not know and have it sitting there.

The Ubuntu community will always be better than my hardware. :lol:

---

