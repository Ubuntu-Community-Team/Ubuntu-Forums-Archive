---
title: "Alternative Dual Boot linux/win (nt/2k/xp) with NTLDR !!!"
date: 2005-11-08
forum: Hardware &amp; Laptops
---

### Post by tomski on 2005-11-08
Yep that's right apparently you can use NTLDR (yuk) to dual boot 

windows & linux

i did not write this but tried it and it works i was quite amazed to say the least

Here's how :



Convert a Windows system to dual-boot Linux on a second drive

Monday February 21, 2005 (02:00 PM GMT)

By: Philip J. Hollenback

I was recently assigned the task of converting a system running Windows XP to dual-boot Windows and Linux. The user needed to run Windows most of the time, but occasionally needed to boot Linux to run special applications. The one overriding requirement was to change the existing Windows setup as little as possible. In this case, that meant adding a second hard drive. Easy enough, right? Well, not so fast.

The computer in question was a standard white-box PC with Windows XP installed on its one hard drive. One option was to shrink the exiting Windows partition with NTFSresize ( [http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html) )and install Linux in the resulting free space. However, this was too intrusive. I did not have a backup of the data on the Windows machine, and didn't want to take the time to make one, so I was loath to do anything that could wipe it out.

So I installed and set up a new second drive, then installed Fedora Core 3 in the standard manner. When the installer asked what drive to use, I chose the second IDE drive, hdb. The other key step was to make sure the installer did not install a Linux boot loader on the primary hard drive. While having the installed do this is generally the recommended method of installing a dual-boot Linux/Windows system, I didn't want to do it because of my goal of minimizing changes to the Windows disk.

The Windows bootloader (NTLDR) can be configured to boot Linux partitions, so I decided to use it as the primary bootloader. The default boot option would remain Windows, so if the user took no action on boot, the system would go to Windows as it always had. However, if the user selected Linux in the NTLDR boot menu, it would hand off to the Linux bootloader (GRUB) on the second drive.

The Fedora installer gives you the option of placing GRUB in the master partition of the primary IDE drive (hda) or in the boot partition of the secondary IDE drive (hdb1). I instructed the installer to take the second option. Note that without extra configuration later, this setup will not boot to Linux, because whatever bootloader is on the primary drive -- in this case Windows -- will always be run.

Another option I considered was removing the primary Windows drive and placing the Linux drive in the system as the primary drive. I could then install GRUB on the Linux drive (the primary now) and configure it to also boot Windows on the secondary drive. One caveat here is you must configure GRUB to fool the Windows drive into thinking it is still the primary. Otherwise, Windows gets confused. I elected not do this type of install because it seemed more complicated than installing Linux on the second drive.

Boot sector transplant

The next step in the process is to save a copy of the Linux boot partition. This can be done either with dd in Linux or with the free Bootpart ( [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm) ) utility under Windows. Either program simply takes the first 512 bytes on the disk and puts them into a file. The dd command to do this is dd if=/dev/hdb1 of=bootsect.lnx size=512 count=1. Once you have this file, copy it to a diskette or some other removable media so you can then copy it to the Windows drive for NTLDR.

I happened to use Bootpart because I forgot to use dd before I booted the system back to Windows. If you use Bootpart you don't have to copy the boot sector to a diskette, as you are already in Windows. To complete the transplant, place the file you created with dd or Bootpart on the Windows drive as C:\bootsect.lnx.

Now it's time to tell Windows about Linux. Again, there are two ways to go about this. If you are doing everything manually, fire up a text editor in Windows and edit the file c:\boot.ini. Add the line c:\bootsect.lnx="Linux" to the end of the file.

The Bootpart way to do this is simpler: run Bootpart with the command bootpart Linux c:\bootsect.lnx "Linux". Bootpart will take care of adding the proper entry to boot.ini for you.

Testing and final thoughts

Your system should now be correctly configured. To test it, reboot the machine. After the BIOS screen, the first thing you will see is the NTLDR menu asking which OS you wish to boot. If you do nothing you will go to Windows. If you choose Linux on this screen, NTLDR will use bootsect.lnx to hand off the boot process to Linux, and start booting from your second hard drive. The next screen you will see will be your Linux bootloader screen. From this point on, your system boots the same as any other Linux machine.

And there you have it: a Windows machine that boots Linux as well. The advantages of this setup are:

    * The Windows configuration remains essentially untouched.
    * No changes to the Windows hard drive boot sector are necessary.
    * Removing Linux from the machine is simple: physically remove the Linux disk and remove the Linux entry from boot.ini under Windows.
    * Windows users have a tendency to reinstall the OS from time to time. If that occurs on this system, the Linux disk would be untouched (although you might not be able to boot to it until you copy the boot sector again and fix boot.ini).

While this configuration isn't ideal for everyone, it is a great way to add Linux to an Windows machine with minimal disruption of an existing Windows installation.


Good eh just thought this may help people more akin to the windows enviroment.

:razz: 

i found it here 

[http://enterprise.linux.com/enterprise/05/02/16/1919205.shtml?tid=129&tid=49](http://enterprise.linux.com/enterprise/05/02/16/1919205.shtml?tid=129&tid=49)

have fun

[ED] 
you may find this helpfull to copy the files from a reiserfs partion within windows

put this in program files
[http://p-nand-q.com/download/rfstool/rfstool-0.14.zip](http://p-nand-q.com/download/rfstool/rfstool-0.14.zip)

and put this in the same directory
[http://yareg.akucom.de/download.cgi/YAReG-0.9.9.zip](http://yareg.akucom.de/download.cgi/YAReG-0.9.9.zip)

if you have problems with those try this
[http://www.wolfsheep.com/map/rfsgui-2.0.zip](http://www.wolfsheep.com/map/rfsgui-2.0.zip)
[ED]

---

### Post by ThomThom on 2005-11-09
[QUOTE=tomski]
The Fedora installer gives you the option of placing GRUB in the master partition of the primary IDE drive (hda) or in the boot partition of the secondary IDE drive (hdb1).[/QUOTE]

Does the Ubuntu installer give you the same option?

---

### Post by tomski on 2005-11-09
yes it does if you select to 'manualy edit the partitions'

---

### Post by fakie_flip on 2006-11-04
You described doing the process with Fedora Core release 3. I have "Damn Small Linux Not" installed to the second hard drive. I have not been able to boot it. The installer asked me if I wanted Grub, and I choose Grub. I am not sure exactly where Grub was installed. It's not on hda because I still go to the ntloader and boot windows normally. I did find the /boot/grub/ and all the files to go with it including menu.lst on hdb1 after mounting it on the DSL-n live cd (same cd used for install). I did use dd and follow all of the directions the same. I put linux.img, the image of linux's boot sector in my removable pen drive and then copied it over to c:\ in windows. I tried changing "c" in c:\ to "C" in boot.ini, but that did not make any difference. I tried doing dd again to start the process over again and even reinstalling "Damn Small Linux Not" again. I am stumped in finding the problems because I followed the direction. I had no choice where to install Grub with DSL-n, and it wasn't clear where it did go, however, the /boot is on the same partition mounted with / and it looks like all the Grub files are there. Before I forget to say, DSL-n shows in the ntloader. Windows boots normally if I choose it or let it go automatically. If I choose DSL-n, I get a black screen that does not change with a blinking white underscore at the top left. I was wondering what would happen if I used dd to make a copy of the boot sector for windows, so I did, copied it over and added the entry to boot.ini. When I choose that, it would take me back to the ntloader as it should and the timeout starts back at 8, what I had it set to. Here is what I added to a bottom line in boot.ini on a line by itself: c:\linux.img="Damn Small Linux Not". I also tried "grub-install /dev/hdb" and the grub notation, hd1 instead. Nothing changed. I ran it as root.

---

### Post by nothingworks on 2006-11-04
> **tomski said:**
> yes it does if you select to 'manualy edit the partitions'
it does, but you need to type in the partition manually.
i.e where it shows hd0, change it to /dev/hgb2 (depends on where you want grub installed)

I'm not sure if entering /dev/hdb2 would work, so i installed grub on the mbr, next removed it with the xp cd (fixmbr, fixboot), next I ran the live cd again, and manually put grub on hdb2.

With bootpart and ntldr, ubuntu starts correctly now.

I hope nobody mentions using the alternate cd, because it is text based, and generally useless.
It detected only my primary hdd, and was forcing me to use the full disk for ubuntu!!! lol

---

