---
title: "/dev/hdX not found, replaced by /dev/sdX causing problems"
date: 2008-05-14
forum: Hardware
---

### Post by yevgeni on 2008-05-14
I've searched this forum for an answer on this topic, but to no avail.

My setup:
Intel Core2 Duo
2G PC800 DDR2
GeForce 9600FX
1x SATA Optical Drive
2x IDE HDD's attached to motherboard
1x IDE HDD attached to primary channel of add-on IDE card
1x OnStream DI-30 tape drive attached to secondary of IDE card

I recently picked up an OnStream DI-30 IDE tape drive for quite the bargain. It works very well in Windows, but I bought it for Ubuntu, obviously :-)

I know that there is kernel support for said device, which was one of the selling points. Here's where the problem begins.

For some reason, and I have no idea why, Ubuntu detects all of my IDE devices as /dev/sdX instead of the normal /dev/hdX. I read elsewhere on the forum that this is due to a change in the kernel. Whatever the reason, it is messing up the kernel's ability to detect the tape drive at all. I know this because I booted up my Debian installer CD and the kernel gave me this line: 

```
hdg: DI-30 OnStream tape drive
```

It wasn't exactly this, but the point is that the kernel on the Debian CD detected all of the IDE devices normally, including the tape drive. Ubuntu's dmesg doesn't show that it detected the drive at all.

I guess the million dollar question here is:
Is there a way to reverse this /dev/sdX garbage in the kernel by modifying the stock config? I poked around in the source code documentation a little bit found no answers. If I could get my IDE devices to detect normally, I could easily get my tape drive working.

Thanks in advance!

---

