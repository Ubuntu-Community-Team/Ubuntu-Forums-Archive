---
title: "cd rom not recongnized after initial boot"
date: 2005-01-21
forum: Installation &amp; Upgrades
---

### Post by jmsavoy on 2005-01-21
After I boot the warthog cd and load the kernel ... I get asked what language I want to use. Then it ask me for drivers from a floppy for a cd drive because it cannot find my cd rom drive.

I've had FC3, NLD 9, and Gentoo on this box with no issues (at least not like this one ).

My cdrom is an IDE drive. My hard disk is SATA. P4/HT cpu. 1gb ram. Intel ICH5 chipset (i865).

Any ideas? This has got to be simple, and I'm sure somebody else has seen it.

---

### Post by chryz on 2005-01-21
It might be that I was simply unlucky, but I had the same problem when I tried installing Ubuntu with Norwegian selected as language - tried it twice with the same error. Tried again but simply zipped through the menus selecting english as default, and suddenly it worked... might be worth trying out.

Just switched from Mandrake 10.1 AMD64, and have to say that after working through a couple of bugs more I got down to actually using it - to be honest this is miles ahead of Mandrake.

---

### Post by ?eter on 2005-01-23
I'm Having the same problem on my system,the LiveCD boots fine (albeit very slowly) but I can't install from the install CD because it does not find the Cd-ROM. There is a bug in the Ubuntu Bugzilla (bug 1440) that deals with Cd-Rom issues on SATA drives,but the resolutions discussed are very technical (too technical for a newbie like me who last used a command line shell in dos 6.2 c.1996) and seemed to create other issues.

Also, I have successfully installed Mandrake 9 on this machien with identical setup in the past.

I hope someone has a solution for us,or at least that this bug is fixed for the 5.04 release.

?eter

---

### Post by arthureggplant on 2005-02-09
When your in the install process, do this:

Stollen from here: [https://bugzilla.ubuntu.com/show_bug.cgi?id=1440](https://bugzilla.ubuntu.com/show_bug.cgi?id=1440)

1. boot up installer as normal
2. Choose Language
3. Skip to tty2 by hitting alt-F2
4. do:

    insmod /lib/modules/2.6.xxxxx/kernel/drivers/cdrom/cdrom.ko
    insmod /lib/modules/2.6.xxxxx/kernel/drivers/ide/ide-core.ko
    insmod /lib/modules/2.6.xxxxx/kernel/drivers/ide/ide-generic.ko
    insmod /lib/modules/2.6.xxxxx/kernel/drivers/ide/ide-cd.ko
    insmod /lib/modules/2.6.xxxxx/kernel/drivers/ideide-core.ko

---

### Post by davismbagpiper on 2005-02-11
Thanks for the last tip. I had to use it on a Dell Inspiron 7500 to get the install to work. Thanks again

---

