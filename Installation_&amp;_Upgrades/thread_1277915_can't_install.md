---
title: "can't install?"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by baffle-boy on 2009-09-28
i'm running windows XP, and i wanted to have a dual boot ubuntu/xp, so i downloaded the wubi installer and ran it, it all seemed fine until... i rebooted my computer and saw NO OPTION to boot into ubuntu.  have no idea what to do, i think it may be because ubuntu wasn't downloaded completely (the progress bar at top never finished and still said it was downloading), so how do i download the OS separately and install the file when its already on my computer? please help soon, i kind of want to use ubuntu >.>

---

### Post by Mercury_Alpha on 2009-09-28
Wubi installs Ubuntu inside of Windows' NTFS partition, which is why you can't see it in a boot menu. As far as I know, a Wubi version of Ubuntu can only be used from within Windows. It's designed to be a taste test of the operating system.

If you want to dual boot, you'll need to boot the computer with an Ubuntu CD (or on a USB stick, of your computer supports that). This process will create separate partitions for Ubuntu that will show up in a boot menu when you start your computer.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by baffle-boy on 2009-09-28
oh, ok i was under the impression it could do a full install... well, i suppose ill get right on that then, it will work if i burn it to a dvd-r right?

---

### Post by Mercury_Alpha on 2009-09-30
It fits on a CD, so you can just burn it on one of those (unless you only have DVDs).

---

### Post by oldos2er on 2009-09-30
Wubi should've installed Grub4Dos bootloader, which gives you a choice of OS at boot time. 

 If you want to install Ubuntu to its own partition, you need to boot from the LiveCD first.

---

### Post by tkelito on 2009-10-01
> **Mercury_Alpha said:**
> Wubi installs Ubuntu inside of Windows' NTFS partition, which is why you can't see it in a boot menu. As far as I know, a Wubi version of Ubuntu can only be used from within Windows. It's designed to be a taste test of the operating system.

I am on a computer currently that has XP and 9.04 which was installed via Wubi.

Wubi is a full install of Ubuntu, on restart it allows you to choose which OS you want (in my case XP or 9.04).  Something went wrong during the OP install, Wubi is NOT just a test version of Ubuntu.  Actually the only difference between it and a clean install is that Ubuntu does not natively support NTFS so their is a slight performance loss because the OS is operating out of a container file on the C:\ drive of XP and not off it's own dedicate partition on the drive using Ext3.  Other than that, it is the same thing.

Sound to me like your download was fubar'ed, I would make sure you get a full version of the x86 or the x64 version you require and you can go ahead and try doing the install with Wubi.

It should install as an application in your Add/Remove or Programs/Features (depending on XP or Vista) and you choose the size of the container you want to dedicate.  Mine is set to 30GB which is more than enough for my install as I do not house files locally.  After you go through the GUI in Windows and install Wubi and the OS.  Restart and you should have the choice to boot Windows or Ubuntu.  Choose Ubuntu, finish getting it setup and you are ready to go with your dual boot system without have to setup the partitions manually.

Enjoy.

---

