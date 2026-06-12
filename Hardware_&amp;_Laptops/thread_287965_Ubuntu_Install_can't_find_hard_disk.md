---
title: "Ubuntu Install can't find hard disk"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by Andarki on 2006-10-29
Hello,

I have some problems installing Ubuntu 6.10 on my Medion MD97600 Laptop.

When I boot from the CD, using the standard options I see a progress bar going back and forth, and after some seconds I end up in Busybox with the following message:

/bin/sh: can't access tty; job control turned off



I have tried using [this guide]("http://ubuntuforums.org/showthread.php?t=28948") to install from network instead of CD.
It allows me to select a network card to install from (i choose wired), it asks for a hostname, I get to select a mirror and it does download some files.
Then I get this message with a red background:

No partitionable media were found.
Please check that a hard disk is attached to this machine.

Then, I see a menu which lists the steps in the install.

Some specs:
Its a centrino based laptop, with a 1.8 GHz Pentium-M CPU.
The hard disk is a Samsung MP0804H 80GB.

I did manage to install CentOS 4.4 and Mepis on it, but I would prefer to have Ubuntu installed.

While in Busybox, I noticed that hda/hdb is not present in the /dev folder.
Sounds to me like the installer can't find the hard disk? 

Does anybody have an advice on how to proceed?
Please let me know if I can supply you with any further information.

Best regards,
Anders

---

### Post by drtvasudevan on 2006-11-14
the initial problem of tty  - i too get it. 
re teh netinstall..
i remember reading somewhere that sata hard disks are read as sdx by the installer not hdx

---

