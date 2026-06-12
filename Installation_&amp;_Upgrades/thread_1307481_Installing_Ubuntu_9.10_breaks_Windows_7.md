---
title: "Installing Ubuntu 9.10 breaks Windows 7"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by statictonic on 2009-10-31
deleted

---

### Post by tommcd on 2009-10-31
I have seen other threads like this. To get Windows 7 to boot, boot up the Windows 7 DVD and restore the master boot record:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Then to get Ubuntu back (with the ability to boot Windows7 hopefully) reinstall grub2 from the Ubuntu 9.10 live CD:
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)

---

### Post by statictonic on 2009-12-03
deleted

---

### Post by wilee-nilee on 2009-12-03
You probably have 2 HD and the ubuntu is in one of them have you tried setting the boot from the ubuntu installed HD.

So do you have 2 HD's?

---

### Post by statictonic on 2009-12-03
> **wilee-nilee said:**
> You probably have 2 HD and the ubuntu is in one of them have you tried setting the boot from the ubuntu installed HD.

So do you have 2 HD's?

This is a single HDD, Win7 is the first partition as ntfs, then the partition Ubuntu makes for itself as ext4 and then the linux swap partition.

GRUB2 loads, but when I goto Windows 7 it'll bsod and fail to load shortly after the windows logo splash screen, the repair your computer section of windows will load, but it does not recognize a windows install.

When I mount the ntfs partition in ubuntu everything is still on that partition just fine and it's a boot partition according to gparted.

---

### Post by statictonic on 2009-12-03
Once I remove all Ubuntu partition, the Windows 7 Repair utility can see the C: drive again and I'm able to fix Windows 7 boot, however this obviously means I no longer have Ubuntu on the system...

---

### Post by wilee-nilee on 2009-12-03
So if grub is the bootloader have you tried in the terminal.
sudo update-grub
There are situations that I have seen on the forum where grub is not pointing to the correct partition so this may be the problem.

So I also notice that in your 1st post the link is to a kubuntu install, so besides Intrepid are you using Kubuntu?

---

### Post by statictonic on 2009-12-03
deleted

---

### Post by statictonic on 2009-12-03
deleted

---

### Post by wilee-nilee on 2009-12-03
I think we probably need to know the computer, I have seen posts about HP and another manufacturer having problems.

Ext4 and W7 have no issues they are on different partitions unless it is a wubi install

---

### Post by phillw on 2009-12-03
> **wilee-nilee said:**
> I think we probably need to know the computer, I have seen posts about HP and another manufacturer having problems.

Ext4 and W7 have no issues they are on different partitions unless it is a wubi install


he he - having problems ?.... I take it you're referring to the fact that certain manufacturers have recovery s/ware that stamps all over grub2 by over-writing the MBR. Untill the Grub2 team can come up with a method to stop a completely different operating system breaking the rules and messing with the MBR, I fear this is a call for help we will see more frequently.

[http://ubuntuforums.org/showthread.php?p=8433673#post8433673](http://ubuntuforums.org/showthread.php?p=8433673#post8433673)

Has one work-rouind, and 

[http://ubuntuforums.org/showthread.php?t=1343378](http://ubuntuforums.org/showthread.php?t=1343378)

has a different attack.

Our views on the rights and wrongs of the problem mean that we have to 'tame' the other operating system - or use a different boot-loader. ::SIGH::

I'd prefer to offer the option of 'taming' the errant processes being called by manufacturers within the Win environment, but we have to keep our options open until something more permanent is found. (Shooting a certain W. Gates, is not an option - lol)

Phill.

---

### Post by statictonic on 2009-12-03
deleted

---

### Post by oldfred on 2009-12-03
If you have lots of memory 4GB or more you probably can run without swap if you never hibernate and do not run memory intensive applications. Many users with lots of memory report little or no use of swap. I have heard of a way to put swap in a file similar to windows but do not know the details.

The only time I have heard of something like this where swap caused a problem was that the boot flag somehow was on the swap partition. But the boot flag should only be on the windows partition and must have been if you booted it ok in the beginning.

---

### Post by wilee-nilee on 2009-12-04
> **phillw said:**
> he he - having problems ?.... I take it you're referring to the fact that certain manufacturers have recovery s/ware that stamps all over grub2 by over-writing the MBR. Untill the Grub2 team can come up with a method to stop a completely different operating system breaking the rules and messing with the MBR, I fear this is a call for help we will see more frequently.

[http://ubuntuforums.org/showthread.php?p=8433673#post8433673](http://ubuntuforums.org/showthread.php?p=8433673#post8433673)

Has one work-rouind, and 

[http://ubuntuforums.org/showthread.php?t=1343378](http://ubuntuforums.org/showthread.php?t=1343378)

has a different attack.

Our views on the rights and wrongs of the problem mean that we have to 'tame' the other operating system - or use a different boot-loader. ::SIGH::

I'd prefer to offer the option of 'taming' the errant processes being called by manufacturers within the Win environment, but we have to keep our options open until something more permanent is found. (Shooting a certain W. Gates, is not an option - lol)

Phill.

Fortunately I have had no problems with dual booting MS and Linux on any computer ever, but I am careful in what I do, and own computers that are not HP or other problematic ones. It is a bummer to see people have problems though where there should be none, in just a basic booting system. I say let them boot so the OS can fail.

---

### Post by stanvan on 2009-12-05
I had similar problem with HP (p6230y) that had Win7 preloaded on single HD... no OS would boot after intalling Karmic/Grub2.  My solution was to install Jaunty instead with old Grub and all was fine.  Then did distro upgrade to Karmic which kept old Grub.  Works for me, and easier to edit menu.lst anyway.  I installed Karmic/Grub2 on two laptops (HP/Vista and Gateway/Win7) prior to this with no incident.

---

