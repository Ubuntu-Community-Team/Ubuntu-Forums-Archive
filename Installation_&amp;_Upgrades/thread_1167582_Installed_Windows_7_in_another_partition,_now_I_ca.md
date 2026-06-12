---
title: "Installed Windows 7 in another partition, now I can't start Ubuntu"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by picardo on 2009-05-23
I installed both Windows 7 and Vista on other partitions, after installing Ubuntu. Now when I reboot only boot options are those two systems. 

Ubuntu's startup dialogue is completely gone. 

What should I do?

---

### Post by The Funkbomb on 2009-05-23
The issue here is that Window's boot manager will wipe out Ubuntu's boot manager.  Ubuntu, likewise, will remove Win7's boot manager.

What you need to do is get a program called EasyBCD 2.0 Beta.  Google it.  It'll show up but you need to register on the forums to get the latest build.

Install Windows first.  Then install Ubuntu.  When you're installing Ubuntu, click the advanced option and choose another place it install Ubuntu's grub.  For example, on my machine, Ubuntu is installed in SDA6 I believe.  I installed the Grub boot loader in SDA6 as well.

Now, back over to windows.  Run EasyBCD and set that up.  There are options where you can choose the location of the Ubuntu GRUB.  Just choose the correct area where you installed it and uncheck the mark that says something like, "Grub is installed in the Boot Sector" or something like that.

Here is what happens.  On my machine, I have a dual boot of Win 7 and Ubuntu 9.04.  When I boot up, it gives me a choice of Ubuntu or Win 7.  If I choose Win 7, it goes right into Windows.  If I choose Ubuntu, it loads Ubuntu's GRUB and then I just choose the first option and then Ubuntu boots up fine.

I hope this helps.

---

### Post by zvacet on 2009-05-23
[Reinstall grub.]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by presence1960 on 2009-05-23
> **zvacet said:**
> [Reinstall grub.]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

+1

I know quite a few people use EASY BCD but I tried it and wound up asking  why? GRUB is easy to setup and is a great bootloader. Follow the instructions zvacet posted. Then you can add your windows partitions to the GRUB menu by editing your menu.lst file.

---

