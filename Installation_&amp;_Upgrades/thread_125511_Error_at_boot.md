---
title: "Error at boot"
date: 2006-02-04
forum: Installation &amp; Upgrades
---

### Post by RKF on 2006-02-04
1. At boot the progression stops at "fsck failed".

then using the repair tools/suggestion, at each entry get "bad command" hae to use the CTRL D to progress.

2. Currently running 3 HDs. One has the operating system (Ubuntu only - no MS) and then there are the data drives used with the MS OS. One has NTFS and the other has FAT32.   The NTFS is SATA and the FAT32 is IDE My understanding is that Linux is supposed to see and read NTFS and be able to interact with FAT32.  

3. It can't see my Canon WiFi Pixma IP5200R printer or any of its installation software, and Canon say they have none for Linux or Unix.

4. Where do I find anti-virus and firewall software?

Apart from those small faults it is up and running - Any clues please?

A criticism of the ubuntu so far - apart from the installation problems, which no doubt will be overcome :)  Good thing it is free. As far as I can see everything in the visible file system is written in "computer geek" and as is a lot of the the "help" the little that there is. At this stage I see little for Bill to be afraid of.  Mind you the email and the browser work fine.

Maybe I have been using MS stuff for too long - since 3.11

Cheers 

RKF

---

### Post by alamba on 2006-02-04
Hi,
New packages can be installed from system>>administration>>synaptic. There are number of anti-virus out there, clamAV being one of them. You really don't need anti-virus on a linux system but would still like to install one out of social responsibility so as to not forward windoze viruses to other users.

Ubuntu already has IPtables integrated, install firestarted to configure it with rules, etc. That would be your firewall.

Boot with a Live CD and run fsck /dev/hda1 (assuming hda1 is the harddisk on which fsck fails). WARNING: please make sure that the partitions u're running fsck is NOT mounted. I ruined my server install by doing that.

Not clue about your wifi printer.

A

---

### Post by alamba on 2006-02-04
oops..sorry...firestarter not firestated*. That's the second time I'm making this mistake today!! Called it firefox the first time!! Maybe age finally is catching upto me.

---

