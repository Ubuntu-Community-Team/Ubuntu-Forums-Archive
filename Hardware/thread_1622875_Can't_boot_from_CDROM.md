---
title: "Can't boot from CDROM"
date: 2010-11-16
forum: Hardware
---

### Post by breem42 on 2010-11-16
I don't think this problem is an Ubuntu issue, but maybe someone can help.

I recently bought a system with a Gigabyte GA-880GMA-UD2H (Rev 2.1) MB.  I'm using the onboard Radeon HD 4250.  I downloaded & burned 10.04 (64 bit version), and tried to get it to boot from it.  So far it won't.

First I checked to see that the BIOS settings were correct -- that it would try to boot from the optical drive first.  Yup -- CDROM was first.  Then I changed all boot drives to CDROM.  Still boots to Win7 :confused:.

I've updated the BIOS to version 5.

BTW it won't boot from a GParted CD, or any other disk that my old machine booted from perfectly.  I need to use GParted to make an ext partition.

[This guy]("http://ubuntuforums.org/printthread.php?t=1575460") looks like he has solved the problem.

Thanks in advance for any help.

---

### Post by breem42 on 2010-11-16
BTW -- when I'm in Win 7 the 10.04 disc is perfectly accessible.  So the optical drive is OK.

---

### Post by breem42 on 2010-11-16
OK, so I figured it out.

My DVD drive was not marked as CDROM as I expected, instead listed a code name (like DVD-BLARG -- can't remember what it was at the moment) at the very end of the list.

Easy fix to bios settings.  Now I'm configuring my new Lucid install.

Thanks for your attention.

---

