---
title: "Additional HD &quot;disappearing&quot;"
date: 2016-06-12
forum: Hardware
---

### Post by sirdragoth on 2016-06-12
First off, I apologize if this has been handled before--I tried to search for threads on it--maybe I used the wrong words, maybe it's NOT a duplicate issue, I am not sure... I don't often use forums, I am, I would say, 99% self-taught (so not very well-versed in "proper" terminology for hw)
Anyway, I have 4 HDs installed--my motherboard detects them all in BIOS.
No matter which "flavour" of ubuntu (or any other linux distro, tbh) that I use, this problem occurs--
When I first boot up, all 4 of my HDs USUALLY show up, and are mountable.  But, after a (seemingly random) amount of time, one of them suddenly disappears.  From GUI, AND lsblk, fdisk, etc.
I have tried using different SATA cables, different SATA ports--everything I can think of--but inevitably the same thing occurs.  According to the SMART data, the disk has 3 bad sectors. I have had the HD for a couple years--but when it's seen, it works as it always has.
No RAID arrays (the disk has never been part of a RAID--always used it as plain old .ext4 data storage)
The drive was mounted at /dev/sdd before it disappeared most recently.
I CAN just pull the data off of it and replace it if needed, but I would like to know if it is simply something I overlooked in upgrading to 16.04.
This computer was running standard Ubuntu 14.04, and it read the HD every time without the random dropping--so I wonder if it could be a bug, or if my HD may have failed when I moved the computer to the other side of the house (lol--but I KNOW that to be a possibility.)
When I decided to upgrade, I used a Live DvD, full reformat, repartition, and clean install.

Not sure if I missed any possibly relevant info...

---

### Post by X-RED_Tech on 2016-06-12
Do you have a know good power supply, enough for those four HDDs and everything else?

---

### Post by sirdragoth on 2016-06-12
The only change to the system (other than the HD shuffling I was doing to see if it was a port or cable issue) is the ubuntu version upgrade, hence my frustration. :)
I guess I can install an earlier ubuntu to see if maybe this old power supply could be failling--I hadn't considered that... thanks lol

---

### Post by weatherman2 on 2016-06-12
I concur with the idea about the power supply.  Power supplies can fail in unpredictable ways.  They may not simply fail entirely.  It may be the power supply is partly failing and/or unable to supply steady current to some of the connected devices, perhaps causing just this one drive to flake out sometimes.

---

