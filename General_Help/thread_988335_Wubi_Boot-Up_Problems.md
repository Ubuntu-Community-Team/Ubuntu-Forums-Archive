---
title: "Wubi Boot-Up Problems"
date: 2008-11-20
forum: General Help
---

### Post by shoot2kill on 2008-11-20
i installed ubuntu through the new wubi installer to a second hard drive on my system.

I have recently been troubleshooting my windows problems which involved changing the msconfig boot-up settings, and reset them to default settings not thinking about it deleting the boot-up option for the Ubuntu OS.

does anyone know what file i have to edit, and what needs putting so that windows gives me the option of booting into Ubuntu.

I am currently on a slow-ish internet and do not want to download a full live CD, and fix the grub that way. and re-installing Ubuntu is not an option either due to files that need backing up..

any help appreciated...

---

### Post by caljohnsmith on 2008-11-20
If you are using Win XP, all you need to do is open your boot.ini via [these instructions]("http://support.microsoft.com/kb/289022") from Microsoft, and add the following line to the end of that file:
```
C:\wubildr.mbr="Ubuntu"
```
And hopefully that should work just fine; let me know how it goes.

---

