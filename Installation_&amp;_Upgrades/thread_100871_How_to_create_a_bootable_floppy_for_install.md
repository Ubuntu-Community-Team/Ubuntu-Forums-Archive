---
title: "How to create a bootable floppy for install?"
date: 2005-12-08
forum: Installation &amp; Upgrades
---

### Post by tim.n9puz on 2005-12-08
I would like to use an old Pentium II system as a server box to learn and experiment. The machine BIOS and/or its CDROM drive are old enough that it will not boot from the CDROM. Once the machine is up and running I can mount the disc fine, I just can't boot from it (the machine has RH 8.0 installed at present.)

How do I go about creating a floppy that will boot and then hand off the installation process to the Ubuntu 5.10 CD-ROM disc?

---

### Post by dsjas297 on 2005-12-09
I had the same problem. I solved it by using the Recovery is Possible Linux rescue system boot floppy. You can get it [here]("http://www.tux.org/pub/people/kent-robotti/looplinux/rip/").

Boot your computer up with the floppy in the drive and select "Boot from CD".

---

### Post by JoshHendo on 2005-12-09
[QUOTE=dsjas297]I had the same problem. I solved it by using the Recovery is Possible Linux rescue system boot floppy. You can get it [here]("http://www.tux.org/pub/people/kent-robotti/looplinux/rip/").

Boot your computer up with the floppy in the drive and select "Boot from CD".[/QUOTE]
Err, don't you mean boot from floppy? It won't do much booting from a CD :\

---

### Post by tim.n9puz on 2005-12-10
Sounds like this image may just do the trick. Downloading now...

---

### Post by tim.n9puz on 2005-12-10
Well, looks like I struck out again. When I enter the "sbm" command the CDROM drive does not show up in the list of possible devices.

This a *really old* PC. It has an IDE card in it for the drives because the BIOS is old enough that it doesn't handle anything over a few GB.

It may finally be getting time for this old dog to retire.

---

### Post by dsjas297 on 2005-12-10
Well, I mean boot the computer with the floppy in it. When it has booted, a menu appears with the option "Boot from CD", which allows booting from the CD.

---

### Post by UbuWu on 2005-12-10
[https://wiki.ubuntu.com/SmartBootManagerHowto](https://wiki.ubuntu.com/SmartBootManagerHowto)

---

