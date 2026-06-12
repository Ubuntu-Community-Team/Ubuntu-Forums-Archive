---
title: "RAID1 not recognized after update"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by kkaal on 2009-04-29
I updated my Kubuntu_64bit 8.10 to 9.4. The update seemed to run quite well (no errors).

Then I found out that it did not mount my RAID1 array. 
This array is hardware configured and 8.10 had no problems with it. Now, GParted sees both harddisks as separate disks (/dev/sdb and /dev/sdc)

GPated:
> /dev/sdb1: Warning:
e2label: No such file or directory whily trying to open /dev/sdb1
Could not find valid filesystem superblock
dumpe2fs 1.41.4 (27-Jan-2009)
---
/dev/sdc1 ... same error


I tried to mout it by hand, but it did not work. And it does not have the /dev/md0

The ATI RAID configuration program in the computer setup shows the RAID array and tells me that is functions.

Any thoughts what I could do?

---

### Post by kkaal on 2009-05-02
No guru there to give me hints?

I lost all my data with the last update. I did nothing wrong. Used standard functions only and can't use my harddisks neither as RAID1 array nor as single harddisks.

So, if now ubuntu really crashed my harddisks, can anybody tell me what options I still have? Or do I have to give up and format the 2 disks. Was it not wise to try to improve my security with the RAID 1 installation on firmware level??

I really thought, with Ubuntu / Linux, I would be on the safe side of life. But with any update, I get nasty problems. My Win collegues have a real bunch of problems (so do I), but they NEVER lost data because of the OS malfunction.

Please try to answer some of my questions.

Thanks.

---

### Post by kkaal on 2009-05-06
Can at least somebody answer this question:

Do I need to file this case as a bug? And: how do I do that?

Thanks

---

