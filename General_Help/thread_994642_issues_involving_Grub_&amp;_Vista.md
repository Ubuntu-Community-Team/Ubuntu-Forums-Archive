---
title: "issues involving Grub &amp; Vista"
date: 2008-11-26
forum: General Help
---

### Post by AdamTraub on 2008-11-26
I installed Ubuntu 8.04 to a thumb drive.  After I installed it, there were some problems.  I put the live CD back into my computer and realized what happened.

Under Advanced on the final step of the installation it installs Grub to the first partition on the machine.  As a result, Linux installed to my thumb drive but the boot loader installed to my machine.  Whenever I try to start my computer, I get: 
Grub error 21.  

As a temporary fix, I installed Linux and Grub to my thumb drive.  After fixing the mem file in my thumb drive, I was able to get my computer to boot into windows.  

I need to remove Grub, or I need to force my computer to utilize it properly.  I can get my computer to boot into Windows with the usb although I oddly can't get it to boot into Linux that way.  I'll worry about fixing the thumb drive later.

A little more background:

1.)  Yes, I realize I should have disconnected the hard drive on my computer before I tried to install Ubuntu to my thumb drive.  

2.)  I'm using 64bit Windows Vista Ultimate Edition.

3.)  I do not have the Windows Vista OS disc.  I got a set of recovery CD's made when I ordered the computer, but there was a mixup, the recovery cd's were for a different computer (they were free... get what you pay for, right?)

4.)  I do a lot of very basic programming with Java and Python.  I also have some knowledge in hardware.  I don't have as much experience working with Operating Systems, so please feel free to dumb down your suggestions as much as you see fit. 

Thanks for reading!!

---

### Post by aikiwolfie on 2008-11-27
So far as I can figure you need to get to the Windows Vista Recovery Environment and run the following commands;
```
bcdedit /export C:\BCD_Backup

&#8226; c:

&#8226; cd boot

&#8226; attrib bcd -s -h -r

&#8226; ren c:\boot\bcd bcd.old

&#8226; bootrec /RebuildBcd
```I think you'll be needing a Vista CD. Contact your PC vendor and get the proper CDs that should have come with your PC. Alternatively you can just install Ubuntu to the hard drive and that will fix the problem.

---

### Post by caljohnsmith on 2008-11-27
You can restore your Windows MBR (Master Boot Record) from the Live CD if you want. Just open a terminal (Applications > Accessories > Terminal) and do:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/[COLOR="Blue"]sda[/COLOR]
```
"sda" should be your internal Windows drive, but if Windows is on a different drive, be sure to change that. You can see what drives you have by doing:
```
sudo fdisk -lu
```
Anyway, give that a shot and let me know how it goes. :)

---

### Post by AdamTraub on 2008-12-08
Thanks for the suggestions.  I haven't been able to get my hands on the proper cd yet (Windows Vista Ultimate 64) so I haven't been able to try fixing the master boot record.  As for repairing the issues through the Ubuntu live cd... I rather hold off on trying that.  I'm a little gun-shy about trying to do anything with the live cd on this computer at the moment. :???:


I think I have an idea that may work out perfectly.  This laptop has 2 hard drives on it (not a partition, but 2 physical drives.)  I think I might simply install linux onto one and keep vista on the other.

---

