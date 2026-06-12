---
title: "Extreme HDD temps causing excessive CPU temps"
date: 2009-10-24
forum: Hardware
---

### Post by AesoSpadez on 2009-10-24
So I've been searching for a few days (including through these forums), and I can't seem to find a solution to my problem.

I'm currently doing maintenance for a close friend of mine on an HP dv2000, and I was noticing unusually high temperatures (regardless of computer use) consistently 20-25 minutes after start up.  I've done a bunch of tracking through hardware temps, and found that the ST9160821AS (formatted to ext4) is going in excess of 60C!  Even if the computer sits unused, the HDD slowly makes it's way up, raising the CPU idle temps 10-15C and even more for the full load temps.

My understanding of Linux and Debian-based operating systems isn't exactly thorough, but I've got a solid grip on the majority of commonplace tasks.  If anyone can offer any advice on how to counter-act this, I'm willing to try just about anything.

Also, I'm upgrading tonight to 9.10, in hopes this problem may solve itself (not much left I know to do that might help).  Thanks for any input in advance.

**EDIT**

After installing Karmic Koala, Palimpsest Disk Utility says the drive has -1 bad sectors?  I'm not sure how that's possible. Again, any help would be greatly appreciated.

---

### Post by subever on 2009-11-12
I have same problem with seagate hdd... I believe it's ext4 filesystem, coz I didn't face this problem when I used ext3.

---

