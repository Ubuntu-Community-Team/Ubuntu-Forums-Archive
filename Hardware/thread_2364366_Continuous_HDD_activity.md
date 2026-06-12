---
title: "Continuous HDD activity"
date: 2017-06-22
forum: Hardware
---

### Post by lwalper on 2017-06-22
Primary reasons I recently switched to Ubuntu: 1) nearly continuous HDD activity in Win10; 2) ??failing hard disk; 3) got new 1Tb HDD, created a mirror copy of my old drive,

** Installed new drive - it would not boot.
** Re-installed old HDD - it would not boot either.
** Re-installed new HDD and installed Ubuntu with full drive format and EXT2 file system

System runs fine, but I'm still having nearly continuous HDD activity. What's the deal? Obviously not an OS problem. Have I got some underlying hardware issue and need to junk this laptop and pony up the $$ for a new one?

---

### Post by Autodave on 2017-06-22
Possibly bad motherboard, but not very likely.  What version did you install? What are the specs of the machine? Xubuntu or Lubuntu would place a lot less load on that machine than Ubuntu: especially if it is a few years old. Also, if you really have a small amount of RAM, that could be causing RAM to swap out and that will keep the HD from resting much.  Please post back specs and version installed and we will be able to help further.

---

### Post by lwalper on 2017-06-22
Thanks. It's a Toshiba Satellite with 4Gb RAM, and some amount of SSD, (32Gb I think). A couple of years old. It was running fine with Win10 installed until maybe three months ago when the HDD began flailing like crazy. Windoze forums have not really been much help - lots of complaints posted about the problem since it seems pretty common, but no real answers. Tried disabling various drivers and such like with no improvement, so I've installed Ubuntu 16.04. Installation went without a hitch, but as I write this the drive is accessing continuously. It will occasionally go quiescent, but that's rare. I was wondering about motherboard, BIOS (UEFI), drive controller or something, or maybe a BIOS setting?

---

### Post by lwalper on 2017-06-23
Well, I've made a change in the BIOS - seems the "Fast Boot" option had somehow gotten turned off, don't know how since I never go there. Enabled that option (which may route all that HDD activity to the SSD) and seem to have stopped the excess HDD activity. Go figure??? Will see how it works.

---

### Post by Autodave on 2017-06-23
Interesting. I (and I am sure a few others here) would love an update on this please.

---

### Post by lwalper on 2017-06-26
Well, seems that "fix" didn't actually fix anything. HDD still flailing like crazy. Does occasionally stop, but not often.

---

### Post by QIII on 2017-06-26
I'm not sure why you chose something as ancient as ext2, but you might try ext4.  It will most certainly be more efficient.

---

### Post by lwalper on 2017-06-26
My bad . . . it is ext4. Interestingly, when I shut down and restart, the restart doesn't sound like the HDD is even running. Opened a document in LIbreOffice - same quiet result. Opened the browser (Firefox this time, Chrome in the past) the drive starts acting up again. Well, as I write this it has now stopped for 30 seconds or so. Curious?? It's almost like it's trying to defragment the drive and constantly moving files around.

---

### Post by QIII on 2017-06-26
If you just recently installed (that is, within hours or so) and you have a large drive, I suspect two things were going on:

1. Indexing
2. Building the inode table.

Depending on what you are doing with your machine while all that is going on, it can take a while.

---

### Post by lwalper on 2017-07-06
It's been a couple of weeks now and still doing the same thing. Several software updates and restarts later ...

---

### Post by lwalper on 2017-07-15
Must have been a motherboard/BIOS problem. Finally came up with a "can not find bootable drive" or some such thing. Not the blue screen of death, but its equivalent. Now I have a good used Toshiba laptop available for parts ;). Anybody need a screen or 4Gb RAM?
 Removed the new 1Tb SATAe drive and put it in my desktop machine. Works like a charm.

THX for your assist!

---

### Post by Autodave on 2017-07-15
I sometimes have the same problem with Firefox. And I have no idea why. I will just be online and not watching and videos, but I will have all 8 cores running over 80% and the SSD running like mad. Got off of Firefox, CPU usage drops to1-2%, drive light normal, no added stuff to SSD: still same amount free.  Weird.

---

### Post by kurt18947 on 2017-07-16
> **lwalper said:**
> Must have been a motherboard/BIOS problem. Finally came up with a "can not find bootable drive" or some such thing. Not the blue screen of death, but its equivalent. Now I have a good used Toshiba laptop available for parts ;). Anybody need a screen or 4Gb RAM?
 Removed the new 1Tb SATAe drive and put it in my desktop machine. Works like a charm.

THX for your assist!

Interesting lesson here (to me at least). If I see a lot of disk activity for no apparent reason, I'll make sure that my backups are current. Thank you.

---

