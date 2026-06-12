---
title: "Hard drive problems (RAID/LVM2)"
date: 2006-09-16
forum: Hardware &amp; Laptops
---

### Post by daijavad on 2006-09-16
Greetings comrades!

About 6 months ago I installed Ubuntu on my workstation on a software RAID1 (2x250GB disks), with LVM2 on top. This has worked fairly well, and I've since upgraded to Ubuntu 6.06 without problems. However, a couple of weeks ago, I was browsing the web as usual and needed to start OpenOffice Calc. The computer totally froze. I was unable to do CTRL-ALT-BKSPC or CTRL-ALT-DEL. Nothing seemed to work, so I did a cold restart. The computer booted, but when doing "Checking filesystems..." during boot it gives me messages like: "Rescheduling sector 57152" (see picture for details) seemingly infintely (>30 min) when connected to the IDE-controller and a few times when connected to the "RAID"-controller, before it gives me a kernel panic message.

I have both disks on the same cable connected to one of my on-board "hardware"-RAID controllers. What I have tried so far:

[LIST]
[*]Connecting the cable to the other RAID-bus, and the normal IDE-controller. (difference described over)
[*]Disconnecting either disk in the array (no effect whatsoever)
[*]Booting with a Ubuntu live CD (works, but fails to mount the array)
[/LIST]

I thought RAID1 should be pretty safe way to guard my data, so I'm both a bit disappointed and deprived now. I hope some of you may have some ideas as to what is wrong, and what I can do about it.

Regards,
Daijavad

---

### Post by Velox Letum on 2006-09-16
Have you tried removing one (or both) of the disks from your array and using it in a different computer?

---

