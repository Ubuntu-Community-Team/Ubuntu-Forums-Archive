---
title: "[SOLVED] hardy dont installs but gutsy does"
date: 2008-08-13
forum: Hardware
---

### Post by syms on 2008-08-13
hardy freezes when installing files to hdd, but gutsy installed everythink ok on that machine. in other words hardy freezes when it needs to copy files. i think the problem is that hardy detects my hdd as scsi device, but it is ide :confused: and gutsy detects good that its ide device. there is problem, but what can i do? i really want hardy. or this is bug? the hdd is wd wd800jb hdd 80 gb ide 8mb 7200 rpm

---

### Post by scragar on 2008-08-13
if you have the hardy alternate disk you could install gutsy then upgrade to hardy without having to download anything, otherwise if you want hardy you may be forced to just upgrade from the internet, sorry(I think if you download the iso you can mount it and upgrade from the iso instead of a full CD, don't quote me on that though)

---

### Post by syms on 2008-08-13
thanks for info, but i hate upgrades. is there any way to change my hdd driver in hardy? i could change it from scsi device to ide device

---

### Post by evets25 on 2008-08-13
They changed the way hard drives are detected in hardy, so that could have something to do with it. IIRC, even IDE drive will show up like "sda" instead of "hda". This COULD be your problem, but it could not be. It defiantly sounds like a driver-related problem though, 

Try some of the different boot options, perhaps they might help.

---

### Post by syms on 2008-08-14
i fixed it, i just needed press f6 in menu and typed acpi=off then it installed system good :)

---

