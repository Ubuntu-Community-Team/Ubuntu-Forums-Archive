---
title: "HELP! I can't boot into anything now!"
date: 2006-01-11
forum: Installation &amp; Upgrades
---

### Post by javaru on 2006-01-11
well... im using a kanotix live disc

I tried and failed to install kubuntu on a flash key.... but i installed GRUB on my (only) harddrive and now windows wont boot either. I get an error number 21. Is there a way to reinstall GRUB or another boot loader from kanotix? 

i tried 
sbin/grub-install /dev/hda
but it complained about read-only file system

THANKS

---

### Post by Sef on 2006-01-11
I found this post on another forum:

> GRUB Error 21 problem solved 

thanks to David Balazic for pointing me in the right direction!

 i changed the CMOS settings to detect the HD's in my system...

this is what i did:

entered Standard CMOS Setup


set the Primary Master to:

    Type = User,  Mode = LBA

by scrolling through the options

 

then set the Primary Slave to:

    Type = Auto, Mode = Auto
 

Link:  [http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html]("http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html")

Hope this helps you

---

### Post by javaru on 2006-01-11
thanks for the reply but.... whats CMOS... 

a link would be great

---

### Post by Sef on 2006-01-11
To get CMOS, you would need to you would need to get into the BIOS.

If unsure how to do that, read this post:  

[http://www.computerhope.com/issues/ch000192.htm]("http://www.computerhope.com/issues/ch000192.htm")

CMOS, itself, refers to nonviolatile BIOS memory.

Expanded definition here: [http://en.wikipedia.org/wiki/Nonvolatile_BIOS_memory]("http://en.wikipedia.org/wiki/Nonvolatile_BIOS_memory")

---

