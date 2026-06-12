---
title: "XP does not install after ubuntu/Vista"
date: 2008-01-19
forum: Hardware &amp; Laptops
---

### Post by virtualcoder on 2008-01-19
Hi all,
  I've been trying to triple boot my system using vista, ubuntu, and xp.
I've succeded in installing Ubuntu, and Vista came with the laptop by default. Now when I'm trying to install XP, I run into different types of problems. I'm not sure whether the problem is with GRUB or something else.

 My system specifications are :

HP Pavilion, model dv6500 notebook, core2duo
2.2Ghz, 2Gb Ram, 250 GB hard drive, Vsita pre-installed.

I bought an external hard drive for the purpose of installing multiple operating systems, and its specs are:

Maxtor One Touch III, 500GB external hard drive.

I've been experimenting a lot with getting these systems installed, so the current existing partitions (in order) are:

(Approx Sizes)
Internal Hard Drive (250GB total):
180GB NTFS Windows Vista
6.5GB NTFS System Backup
0.5GB ext3 Grub installed
50GB NTFS Failed XP install

External Hard Drive (500GB):
125GB ext3 Ubuntu
125GB NTFE Failed XP install
250GB Free space


First I tried installing XP on the external hard drive in the second partiion.
XP detected that partition, and it copied its setup files to the partition.
Then when it restarted the system, well firstly grub didnt show windows XP on the list. So I tried adding the entry for XP manually, something like:

title Windows XP
rootnoverify (hd1,1)
savedefault
makeactive
chainloader +1

So when I choose this option in the GRUB menu, it just gives me a blank screen.
I gave up on this option and used some free space to make a fourth partition on the internal hard drive.
I gave it a size of 50gb, but the problem was that XP did not detect that paritition or any other partition on the internal hard drive.

I read something about Windows being picky about being installed only on the primary paritition, if that is the case, and maybe thats why that it detects Windows Vista installed on the primary partition of the internal hard drive, so its not listing any of the parititions of that hard drive in the first place.
On my external hd, linux is installed on the primary partition, so that might be why it is showing all partitions for that hd.

If all this is true, I could instead re-install Linux onto the fourth partition of the internal hd, and try installing XP on the first partition of the external hd.

I dont want to experiment anymore, since I've spent a lot of days trying to install all these systems and I'm running out of time since I need to use these OSes.

If someone knows what problem I'm facing then please help me out, Thanks a lot!

If I'm posting this msg in the wrong place then please excuse me and direct me to the right place.

---

### Post by ryanVickers on 2008-01-19
So silly of me, but it seems as though you have created a **500Mb** partition *just* for _Grub_??

Please explain.... :shock:

---

### Post by virtualcoder on 2008-01-20
It was a mistake, but at the time I was having a hard time installing Ubuntu, so I decided to be on the "very" safe side and dedicated 500mb instead of 100mb.

Next time I'll know what to do correctly! :)

---

### Post by ryanVickers on 2008-01-20
well, you don't have to dedicate *anything* is my point - grub is only about 20Mb... it's in /boot/grub :p

---

