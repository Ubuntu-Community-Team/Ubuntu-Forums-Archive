---
title: "CD-ROM drive goes crazy"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by robostang 548 on 2007-11-03
I'm having a bit of a problem with Ubuntu on my laptop.  I had 7.04 on my system and it would occasionally freeze (something about Ubuntu not liking my AMD64 processor).  Upon restart, I would see that on my desktop there was an Icon for a cd.  Sometimes it reads as a blank cd-rom other times as an audio disk even though there was nothing in the drive.  I try right clicking the icon and selecting "eject" but nothing happens.  I put a cd in the drive but still no change.  I went into the system log but couldn't even get the scroll bar to move in it because the system log was backed up with this:

```
Nov  3 22:20:02 don-laptop kernel: [ 3550.816958] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Nov  3 22:20:02 don-laptop kernel: [ 3550.816963] ide: failed opcode was: unknown
Nov  3 22:20:02 don-laptop kernel: [ 3550.816967] hda: drive not ready for command
```

Now I've done a fresh install of gutsy.  My laptop doesn't freeze anymore because of my processor but now at random I start having the same problem again.  The following is my boot line:

```
root=UUID=0718a88a-11fd-4658-b134-559b4e074a43 ro quiet splash noapic irqpoll pnpbios=off
```

I disabled the apic because my laptop wont run without it and the "irqpoll pnpbios=off" are because without them, the I have no usb plug-n-play.  

Has anyone else experienced this problem or does anyone have a solution?

-Don

---

### Post by dinub1 on 2007-11-03
Is the CD-ROM connected properly to the IDE cable? If 80 cable/40 pin IDE cable, drive C (primary) is the end connector, slave is the middle connector. Try setting both devices on cable to CS (Cable select). Check this issue.

---

### Post by robostang 548 on 2007-11-08
I'm using a laptop that I just bought about a month ago.  I assume the ide cable is attached properly.

---

