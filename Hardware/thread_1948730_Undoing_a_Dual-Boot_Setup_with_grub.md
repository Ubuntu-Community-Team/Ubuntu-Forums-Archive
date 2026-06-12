---
title: "Undoing a Dual-Boot Setup with grub?"
date: 2012-03-28
forum: Hardware
---

### Post by todd1049 on 2012-03-28
A few years ago, I set up an Acer Travelmate laptop (Core II Duo, 120 GB HD) in a dual-boot setup with Windows Vista and ubuntu 8.04.  I have since upgraded to ubuntu 10.04.  This involved me partitioning the hard disk into four partitions (Vista NTFS, two FAT32 partitions, and one ubuntu ext3), with grub as the boot manager.  I now have a newer laptop and want to give the old laptop to a friend.  Before giving the computer away, I want to have the computer serve just as a single-boot machine with the newest version of ubuntu.  Undoing the partitioning and installing one OS will be not too hard -- I can simply undo what I did earlier with the Vista partition tool.  But can I, or how can I, remove grub?  I figure there is no point in leaving grub on there, and it might even be counterproductive.  Has anyone out there done this before?  And if so, how does one do it?  Thanks for the help!

---

### Post by Bucky Ball on 2012-03-28
You want to leave just Ubuntu and get rid of Windows? Ubuntu needs grub to boot. Easy way:

* Boot from LiveCD (so all partitions are unmounted)
* 'Try Ubuntu' and when at the desktop open Gparted
* Delete the Win partitions and set the boot flag on the Ubuntu / partition
* Apply your changes
* Exit Gparted, reboot

This should do it but if the machine doesn't boot on reboot report back what happens and we can reinstall grub to the Ubunut partition if required.

---

### Post by troymius on 2012-03-28
I think that if you make a clean install of Ubuntu and during that installation you specify that the whole disk will be 1 OS then the grub config file (/boot/grub/grub.cfg) will be made such that it won't ask for anything and just boot the one OS. In other words you will not even notice that grub is there.

If you don't do a clean install you can achieve the same by modifying grub.cfg but in such case the windows partitions will still be there unless you do something with them.

---

### Post by todd1049 on 2012-04-22
Hi Troymius and Bucky Ball, thanks to both of you for your responses.  Just in case you or anyone else was curious (and still following this thread), here's what happened so far.  I booted up in Vista after emptying any data off the ubuntu partition, and after emptying the two FAT32 partitions entirely.  Then I launched Vista's partition manager, and de-allocated the ubuntu partition and the two FAT32 partitions.  After doing so, I was able to merge them all with the Vista NTFS partition, essentially getting the disk all into one partition as it was when I bought it.  Everything seemed OK, and I could still work in Vista with no problems.

So I shut the computer down, and a few hours later, booted it up again.  My usual grub boot screen did not appear, and Vista did not boot either.  Instead, all I got upon boot-up was a command-line interface screen with the following two lines:

     error:  no such partition
     grub rescue>[cursor blinking here]

It does make me wonder what I would have had to do if I wanted Windows to boot on this machine again.  Luckily, as Troymius noted, I was planning a clean install in any case, so I won't have to find out!  I have not yet actually done the clean install I wanted to do.  If anything unusual comes of that, I'll post another message.

---

### Post by oldfred on 2012-04-22
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - also METHOD 3 - CHROOT:

this is a worthwhile tool to have in your computer repair box.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

You can use Windows repairCD or USBs to fix Windows or load a boot loader that works like Windows in just jumping to the partition boot sector.

Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

And it is always a good idea to have a repairCD or USB flash drive for the current version of every system you have installed. Normally you will have the Ubuntu liveCD unless you upgraded. And you can make Windows repair CDs.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by ahallubuntu on 2012-04-22
It seems like your original question was how to get rid of the Grub *MENU* upon boot.  As noted above, you always need Grub to boot Ubuntu.  The menu may come up automatically only if more than one operating system is detected.

At this point, if you are trying to install Ubuntu fresh and use the entire hard drive, just boot up the installer CD and tell it to use the entire hard drive.  It will delete all the partitions and start over.  I'm not sure how the latest Ubuntu versions handle a Grub menu, but a recent install of 12.04 server beta does bring up the Grub menu by default but only for about 1 second.

---

