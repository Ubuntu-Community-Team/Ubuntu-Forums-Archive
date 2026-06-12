---
title: "Is there a way to install Ubuntu without GRUB taking over booting of the computer?"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by NormR2 on 2009-10-22
I have a system with more than one version of Windows XP in different partitions. I chose which one I want to boot by using a tool to set the Active partition to the one I want to boot. Then every time I turn on the system the Active partition boots.
There is NO menu I have to wait on or make a choice from. 

When I want to work with the OS in another partition, I set the Active partition to the partition with that OS and reboot and it boots without any menu.

Is there a way I can install Ubuntu in a third partition without GRUB taking over the booting?  

Or if GRUB is installed, can I remove it and leave the Ubuntu system intact and bootable when I set its partition Active?

Another related question:
I had Ubuntu installed in a partition on another computer with XP in an different partition and wanted to use the Ubuntu partition for another OS. I formated the partition and installed the new OS, and had a big problem getting rid of GRUB with the Ubuntu system gone. 
What could I have done to gotten rid of GRUB?

Thanks,
Norm

---

### Post by itsjareds on 2009-10-22
You have two options:

1) Reinstall Windows XP's bootloader in place of GRUB. You can do this from a Windows XP Install/Recovery CD.

2) Set GRUB's timeout to 0 seconds, this does not remove grub but just sets grub to automatically boot the partition labeled as default in grub's config. Instructions on how to do this vary if you are using grub or grub2.

For your second question, I would do #1.

---

### Post by jeremyswalker on 2009-10-22
Well, I'm not exactly sure how the tool works that you are referring to. However, you can install grub to a partition rather than the MBR. I know that with grub you can chainload to another device (in this case you would point the MBR grub to the Ubuntu partition with grub installed). I'm not sure how this would work with your tool, though.

---

### Post by earthpigg on 2009-10-22
i am not a big fan of WUBI, but it will indeed allow you to "install Ubuntu without GRUB taking over booting of the computer."

***something*** needs to be in charge of your computer booting up.

given standard x86 or x86-64 architecture, your options are the various linux/BSD-centric bootloaders (GRUB, GRUB2, LILO, etc) and Microsoft's bootloader.

you will generally need to be using Microsoft tools to work with the Microsoft bootloader (WUBI is a notable exception to that.) tools intended to work with Microsoft's bootloader may or not easily play well with *nix...

---

### Post by NormR2 on 2009-10-23
To jeremyswalker

Yes that sounds like what I'd like to do: Preserve the MBR so that I manually control which partition is booted by setting the Active partition.  BTW I do that with Partition Magic.

How do you write the GRUB to a partition vs it replacing the MBR?

Then if I want to remove Ubuntu from my system, there wouldn't be a problem with having to restore the MBR that GRUB destroyed.




To itsjareds:
"Reinstall Windows XP's bootloader in place of GRUB." Does that mean that Ubuntu can be placed in a partition the same as Windows and that the MBR program will read find the Active partition and then read the boot record from that partition and pass control to it to boot the OS (Ubuntu) in that partition.
If that is the case, then GRUB would be optional since the MBR program can start Ubuntu without GRUB.

Thanks,
Norm

---

### Post by inertz on 2009-10-23
Normally i will create 1 primary partition say around 200MB for /boot. Then install the bootloader at the partition instead of MBR. Set the partition active so it will boot to that partition first.

---

### Post by jeremyswalker on 2009-10-23
You can install it to the partition during the install process. Installing from the LiveCD, there is an **Advanced...** button on the last screen. I *think* there is an option in there where to install the bootloader. If not, then you will probably have to use the Alternate CD or install grub via the command line.

---

### Post by markbuntu on 2009-10-23
That is all the Advanced button does, allow you to set where grub is installed. Do not miss it. It is a small button the screen after the partitioner. On the lower right side.

---

### Post by NormR2 on 2009-10-24
Thanks to everyone for your help.
I'll be sure to look for the "Advanced" button.

Norm

---

### Post by atoztoa on 2009-11-11
Yeah, you can do that...

You need to use Windows NTLDR bootloader...

Try this thread... [http://ubuntuforums.org/showthread.php?t=208951](http://ubuntuforums.org/showthread.php?t=208951)

My experience...

[http://www.atoztoa.com/2009/11/booting-ubuntu-910-part-1-downfall.html](http://www.atoztoa.com/2009/11/booting-ubuntu-910-part-1-downfall.html)
[http://www.atoztoa.com/2009/11/booting-ubuntu-910-part-2-koala-reborn.html](http://www.atoztoa.com/2009/11/booting-ubuntu-910-part-2-koala-reborn.html)

_ATOzTOA
[www.atoztoa.com](www.atoztoa.com)

---

### Post by oldfred on 2009-11-11
Only windows uses the active partition to define what partition to boot from. I install grub in the partition (PBR) for chainbooting, but still have to have grub in the MBR as that is what the BIOS uses to launch booting of the system.

I think if you set grub up correctly you would find it easier that resetting the boot flag to change operaing systems. You can have grub hidden and set to reboot to last used system very quickly and only if you hit the shift key will it give you the menu. From the menu you can choose any of the operating system installed, no need to open partition editing tools to reset boot flag.

Any time you uninstall an operating system you have to install a new boot loader to the MBR. The same for windows particularly Win7 & Vista with multiple windows as they somehow combine boot into one.

---

