---
title: "I installed Windows, now I don't get to choose OS at startup"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by hubertofliege on 2009-10-02
I installed Ubuntu on a blank hard drive and  partitioned it, then I installed Windows 7.  The problem is that windows doesn't offer the option to choose an operating system at start up, it just goes into Windows.

A few searches have convinced me that I need to download a new boot loader, (possibly GRUB?).  I'm a little cautious to do so, however.  I've heard its possible to mess up a BIOS chip.  How do I go about installing a new boot loader?

---

### Post by ErikEhlert on 2009-10-02
What happened is Windows 7 completely wiped your Hard Drive and devoted it entirely to Windows, you will probably have to re-installl Ubuntu then either DualBoot, but if that doesn't work you will have to install it inside Windows 7.

---

### Post by Bucky Ball on 2009-10-02
Grub will already be there, you're just not getting to it (it is installed when you are installing Ubuntu). 

Try hitting the escape key before it boots into Windows. If the grub is set to 'hidden', this will unhide it. Let us know.

This does depend on whether you still have Ubuntu there as mentioned. Is it showing a partition where Ubuntu should be in Disk Management in Windows?

Incidentally, ALWAYS install Windows OS FIRST. It is a whole lot easier. Then the Ubuntu grub will pick them up when you install Ubuntu LAST. You can do it other ways but for the inexperienced it is a lot more straightforward (reason being Windows wants to be on first physical drive, first partition and if it's not you need to trick it by 'mapping' the drive in the Grub menu.lst file).


What is showing in disk management?

---

### Post by jpaugh64 on 2009-10-02
> What happened is Windows 7 completely wiped your Hard Drive and devoted it entirely to Windows, you will probably have to re-installl Ubuntu then either DualBoot, but if that doesn't work you will have to install it inside Windows 7.It wouldn't be surprising if Windows overwrote any existing non-Windows installation. However, there is some hope, at least, that the Windows installer wasn't that stupid or jealous. 

> Try hitting the escape key before it boots into Windows.More than likely, though, if Windows' boot manager is starting up at ALL, then Grub isn't even getting the chance. Incidentally, you CAN use a free (at least as in price) Configuration tool to add Linux OS entries into the Windows boot loader, so that it displays a menu and offers you a choice of operating system. (That is, if Ubuntu is still there.) The tool works on Vista, but I'm not sure about Windows 7--I haven't gotten too excited about 7 yet, or tried it. It's called EasyBCD, and it has a special "NeoGrub" bootloader for booting *nix OSes. Here's their website for it: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by Bucky Ball on 2009-10-02
Another tool is Super Grub Disk:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Burn the ISO and boot from it and it has been known to do miracles! If there are bootloaders there, it will find them and set up grub for you.

---

### Post by presence1960 on 2009-10-02
Let's not speculate, instead let's see exactly what is going on here! 

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by ghostborg on 2009-10-03
I used the Wubi installer to install ubuntu within Windows which also gives you a OS choice at boot time. It works great. This gives me a chance to see how the laptop works with Ubuntu and also the ability to boot Winblows all without messing with partitions. It looks so far like I will be just making it a full Ubuntu system.:guitar:

---

### Post by presence1960 on 2009-10-03
> **ghostborg said:**
> I used the Wubi installer to install ubuntu within Windows which also gives you a OS choice at boot time. It works great. This gives me a chance to see how the laptop works with Ubuntu and also the ability to boot Winblows all without messing with partitions. It looks so far like I will be just making it a full Ubuntu system.:guitar:

That is great, but that is not of any help to the OP. The OP already partitioned his/her disk and installed Ubuntu & Windows 7.

---

