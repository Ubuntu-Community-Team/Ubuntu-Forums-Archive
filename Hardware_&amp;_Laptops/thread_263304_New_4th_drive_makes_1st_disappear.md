---
title: "New 4th drive makes 1st disappear?"
date: 2006-09-22
forum: Hardware &amp; Laptops
---

### Post by futz on 2006-09-22
Ok, here goes. In my box there were three SATA hard drives. 

There's a 36GB Raptor (sdb1 thru sdb5) that has a boot partition, root partition, swap file, a small archive partition and one other that I don't remember what it is. This is my Ubuntu drive.

There's a 74GB Raptor (sdc1) that's just one partition of storage.

And there's a 250GB Maxtor (sda1 thru sda3) - more storage.

Today I plugged in a new 320GB Maxtor SATA and hit the power. The BIOS saw the new drive fine. I checked boot priorities in the BIOS and let it reboot.

Ubuntu starts to boot normally, but when it gets to the first screen past black (the one with the brown/orange and the really crappy looking font) and hits the second line (mounting boot partition? or something like that), it craps out and can't find the files it's looking for.

Unplug the new drive and all is normal again. Plug it in and it won't boot. 

Any ideas?

I never had this problem when I added the 250GB drive. I hooked the 320GB to another Ubuntu box here and had no problems making it work, tho it was only second drive there, if that makes any difference.

---

### Post by BCRailrodder on 2006-09-23
I've not used Sata drives so I can't say for sure but Ide (in my humble experience :rolleyes: ) tends to only register 4 devices (2 masters & 2 slaves) so if you have a cdrom/dvd you might not be able to use a 4th drive.

Kent

---

### Post by futz on 2006-09-23
> **BCRailrodder said:**
> I've not used Sata drives so I can't say for sure but Ide (in my humble experience :rolleyes: ) tends to only register 4 devices (2 masters & 2 slaves) so if you have a cdrom/dvd you might not be able to use a 4th drive.

Kent
Only in the ancient past and/or for el-cheapo mainboards, my friend. :D 

I've had mainboards that could do a combo of 12 IDE/SATA devices. This particular one can only do 8 - four IDE and four SATA2. It all depends what controllers are onboard.

If I put port multipliers on each of the four SATA ports, I could have 128 SATA devices online. Of course I have no use for that many drives, let alone a power supply capable of powering them all, but it is possible.

---

### Post by BCRailrodder on 2006-09-23
> **futz said:**
> Only in the ancient past and/or for el-cheapo mainboards, my friend. :D 

I've had mainboards that could do a combo of 12 IDE/SATA devices. This particular one can only do 8 - four IDE and four SATA2. It all depends what controllers are onboard.

If I put port multipliers on each of the four SATA ports, I could have 128 SATA devices online. Of course I have no use for that many drives, let alone a power supply capable of powering them all, but it is possible.

As I mentioned (IMHE :) ) - unfortunately, this is what I tend to use.

Sounds like I do need to do a bit more investigation into the newer drives and boards.

Sorry that I wasn't of any help. :( 

Kent

---

