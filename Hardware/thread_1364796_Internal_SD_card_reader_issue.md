---
title: "Internal SD card reader issue"
date: 2009-12-26
forum: Hardware
---

### Post by minimustangs on 2009-12-26
My laptop (ACER Aspire 5102wlmi) has an SD card reader. It reads my SD cards fine...the first time. If I eject the SD card and later re-insert it, I have to reboot the laptop to have it pick up the SD card. It will after a reboot pickup the card, without fail. Is this a bug or am I missing something. I was looking for an option to "mount" the card, but haven't found that yet.

Merry Christmas...

---

### Post by goseph on 2010-01-09
BUMP
I have exactly the same problem.

running:

```

$ dmesg | tail -n 20

```gives:

```

[   28.421501] ppdev: user-space parallel port driver
[   30.983398] [drm] TV-14: set mode NTSC 480i 0
[   31.127184] [drm] TV-14: set mode NTSC 480i 0
[   31.415722] [drm] TV-14: set mode NTSC 480i 0
[   31.559726] [drm] TV-14: set mode NTSC 480i 0
[   31.847617] [drm] TV-14: set mode NTSC 480i 0
[   31.990869] [drm] TV-14: set mode NTSC 480i 0
[   33.367930] [drm] TV-14: set mode NTSC 480i 0
[   33.511411] [drm] TV-14: set mode NTSC 480i 0
[   72.172110] mmc1: card 9d62 removed
[   72.172245] mmcblk0: error -123 sending status comand
[   72.172250] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[   72.172290] mmcblk0: error -123 requesting status
[   72.172305] end_request: I/O error, dev mmcblk0, sector 1431937
[   72.172309] __ratelimit: 24 callbacks suppressed
[   72.172313] Buffer I/O error on device mmcblk0p1, logical block 1431800
[   72.172316] lost page write due to I/O error on mmcblk0p1
[   72.172320] end_request: I/O error, dev mmcblk0, sector 1431938
[   72.172323] Buffer I/O error on device mmcblk0p1, logical block 1431801
[   72.172326] lost page write due to I/O error on mmcblk0p1

```

---

### Post by minimustangs on 2010-01-09
Well I thought I was onto something with this.. the other day I noticed that my 512 meg card would mount and unmount s often as I wanted - without rebooting. Since I was on a bit of a deadline getting some photo's submitted, I just used the 512 instead of my 2Gb cards.

Out all day, snapping pictures. Load up SD card....nothing. 

Reboot...nothing.

Ended up installing it into the camera again, taking it over to other PC (desktop), copying off cam to system, back to USB to upload from laptop. What a pain.

Oh, the Acer L/T died over Christmas, this is a Toshiba Satellite A70 I'm using now.

---

### Post by Jota37 on 2012-09-16
It's 2012 and I too STILL have this problem... Very weird, and quite sick of having to reboot the computer if I need the card reader more than once...

By the way, I found that the problem does not occur in my computer (Ubuntu 12.04) if I do "Eject" instead of "Safely remove", try that!

---

### Post by cariboo on 2012-09-16
Again things have changed quite a bit with a new version of udisk and gvfs, so this information may not be relevant. Thread Closed.

---

### Post by Jota37 on 2012-09-16
Well, maybe those subsystems did not change where it matters for this problem... My install is **12.04 (regular Ubuntu)**, fresh install from a couple months ago, **fully updated**, and I have exactly the same problem as the poster from Dec. 2009. Unless, as I said earlier, I remember to "Eject" and NOT "Safely remove"...

---

