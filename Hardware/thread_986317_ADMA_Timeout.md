---
title: "ADMA Timeout"
date: 2008-11-18
forum: Hardware
---

### Post by Tango_Down on 2008-11-18
So for the second time in as many months I've had issues with ADMA timouts during boot up. The first time, I replaced my hard-drive, and it seemed to fix the issue, but I am not inclined to do it now. 

I have a segate barracuda 160 GB harddrive and an LanParty nforce 4 board mainboard running a completely updated version of Hardy Heron. When I bootup in recovery mode, the prompt freezes and I get stuck at these two lines:

ata-5:Timeout waiting for ADMA IDLE
ata-5:Timeout waiting for ADMA LEGACY

Now I know that there is a way to disable ADMA using boot commands, but how? Also, what will that do to my system?

---

### Post by cariboo on 2008-11-18
Have you tried:

```
sata_nv.adma=0
``` 

on the kernel line of grub?

Jim

---

### Post by Tango_Down on 2008-11-18
Tried that, but it just gives me a line saying:

sata_nv.adma=0 unknown boot option; ignoring.

---

### Post by Tango_Down on 2008-11-18
Also, does this perhaps indicate a larger issue with my harddrive? My XP partition runs fine, but the bug did not pop up after an update. The last time this happened, XP decided to start blue-screening a few days later.

---

