---
title: "Grub Issues During Dual Boot"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by IAmNotAUser on 2009-11-10
I was running 2 distributions of Ubuntu on my netbook, and they were fine.

I have the following partitions from then:
/home
/ - distro1 - also mounted inside /mnt in distro2
/ - distro2 - also mounted inside /mnt in distro1
/GRUB - grub legacy - holding my customised menu.lst for chainloading the distros
swap

in the following order:
hd0,0 - GRUB
hd0,1 - Home
hd1,0 - distro1
hd1,4 - distro2

However, I have changed one of my distributions (complete erase of distro2 partition and reinstall) and now whenever I attempt to boot, if I select distro1 first then it boots fine. If I select distro2 first then I get a grub Error 13: "Invalid or unsupported executable format". If I then press any key and go back to the grub menu, if I chose distro1 I get Grub Error :18 Selected cylinder exceeds maximum supported by BIOS.

I've tried re-reinstalling distro2 to no avail.

I'm not installing the bootloader during install (turned off in advanced options).

What am I doing wrong? And why does the Error 18 appear only after I have selected distro2 and then try distro1?

---

### Post by oldfred on 2009-11-11
Does you grub have chainboot entries or specific ubuntu boot entries. I have an old grub partition and chainboot with old grub in each partition and chainboot from the old grub to new grub in the Karmic partition. Grub2 complained when I installed it but works in the partition.

If you have the ubuntu entries it sounds like typo:
[http://members.iinet.net.au/~herman546/p15.html#13](http://members.iinet.net.au/~herman546/p15.html#13)

Generally you only get 18 with older computers but Herman has some other exceptions:
[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

---

