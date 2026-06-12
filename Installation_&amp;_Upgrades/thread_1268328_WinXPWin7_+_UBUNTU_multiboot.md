---
title: "WinXP/Win7 + UBUNTU multiboot"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by alex51 on 2009-09-16
Hi all
I have got a multiboot computer with two partitions on disk 0:
Win XP
Windows 7 
 
Recently I added second disk and installed ubuntu 9.04 on it. I am complete novice to Linux in general and Ubuntu in particular, so I used all the standard defaults.
Now my multi-boot menu shows 3 ubuntu items and then windows items. So far it works OK, but ...
 
The problem is that my second disk is external eSATA drive. And if it is not turned ON on boot, I cannot even boot my old good XP, because disk 0 boot record was altered during the installation to point to menu.lst file inside Ubuntu partition. So, now my external disk is not removable anymore, which is very sad. Is there any way to move ubuntu's menu.lst file inside Win XP partition so it can be read when external disk 1 is disconnected? Of course, in that case I am not going to select "ubuntu" boot from the menu.
 
If this cannot be done, then I will have to remove whatever changes ubuntu made to disk 0 MBR (luckily, I have recent disk 0 backup) and try to include ubuntu boot option to Windows 7 multi-boot script. I am not sure I know how to do this, but I think it is possible.
 
Any advice, please?
Thank you

---

### Post by earthpigg on 2009-09-16
> **alex51 said:**
> 
Any advice, please?
Thank you

hi,

you will need to use Windows tools to put XP or 7 back in charge of the MBR.

this is for vista, but may do the trick: [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

or you may want to hunt for the win7 equivalent. 


then you will need to install GRUB onto the external hard drive.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

OR

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

except that you will not want to put grub on (0,0).... skim [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") to find relevant information about how to locate what your external USB drive will be.


next time you do this, you have two options:

a) use the 'alternate ubuntu installer', which gives you more options for non-standard configurations such as yours, and read everything very very carefully.

b) using the standard installer and standard default options:

1 - set your bios boot order to be CD, USB, internal hard drive.

2 - physically unhook the windows hard drive.

3 - install ubuntu, following all the default options.

4 - when you want to run ubuntu, plug the external drive in and restart the computer.

---

