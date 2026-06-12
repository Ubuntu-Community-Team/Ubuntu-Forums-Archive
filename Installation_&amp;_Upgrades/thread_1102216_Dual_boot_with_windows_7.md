---
title: "Dual boot with windows 7 ???"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by ocoinnigh on 2009-03-21
i have installed ubuntu 8.10, then installed windows 7, reinstalled the grub .. now when attempt to boot windows i get a possible virus error and it will not boot. cmos antivirus has been disabled ... anyone else have this problem or have any possible solutions?

thanks in advance.

---

### Post by LiamWilson on 2009-03-21
It would have been wise to install Windows 7 before you installed Ubuntu, then grub would have configured for you.

---

### Post by cariboo on 2009-03-21
You may want to check your Windows 7 iso for viruses. There is nothing in Ubuntu that will give you a virus alert, so it has to Windows 7 that is giving you the alert.

Jim

---

### Post by ocoinnigh on 2009-03-21
we have successfully installed this release on a few other computers including our laptop which we installed both operating systems using the same steps..? it is an official beta release form microsoft and is virus free ... the warning is occuring in the boot screen but only warns about the virus after installing the grub from the live cd.

---

### Post by ocoinnigh on 2009-03-21
should i have installed windows first?

---

### Post by Mark Phelps on 2009-03-21
> **ocoinnigh said:**
> i have installed ubuntu 8.10, then installed windows 7, reinstalled the grub .. now when attempt to boot windows i get a possible virus error and it will not boot. cmos antivirus has been disabled ... anyone else have this problem or have any possible solutions?

thanks in advance.

Neither GRUB nor Ubuntu come with any antivirus protection builtin; so it's not possible to get such a message from either of them.

What are you using to boot Win 7? I don't understand how the standard MS boot manager is able even to detect a CMOS virus, let alone present a warning message about such.

My suggestion, is that if, as you say, the Win 7 Beta is legit, you get onto the TechNet forums and post your message there.  They have MVPs that read those forums all the time.  Perhaps one of those folks can tell you what's happening with the MS boot loader such that it will present a virus warning.

---

