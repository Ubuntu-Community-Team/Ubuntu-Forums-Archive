---
title: "Transfer ubuntu boot from HDD to SSD"
date: 2014-07-16
forum: Hardware
---

### Post by maazmahmood on 2014-07-16
I have my computer dual booted into Windows 7 and xUbuntu 14.04 (THEY ARE ON PHYSICALLY SEPARATE HDD). Obviously it boots to the GRUB menu from there I select xUbuntu or Windows 7. Now I'm thinking about getting a SSD for my Linux Hard drive, and someone at work suggested ghosting the two drives. My only concern is since the bootloader is on Linux I don't want my Windows to be gone too. So will ghosting work? If so, is there a guide for 14.04 that'll help? If not, then what will?

---

### Post by oldfred on 2014-07-16
I always suggest that you have each systems boot loader on that systems MBR (or efi if new UEFI system) so each drive can boot its system without other drive.
So do you currently have grub on sda and that is Windows drive? Better to reinstall Windows boot loader to Windows drive and grub to Ubuntu drive.

Some have used clonezilla, but I suggest new install.
Are you keeping current hard drive installed? If so it can cause issues.
You cannot have duplicate UUIDs and have to edit fstab, reinstall grub and make a few other corrections if you image copy to new drive. And if keeping old drive have to change the UUIDs of one or the other.

I prefer a new clean install. SSD also require a few changes anyway.
And if you copy /home over you will have all your settings and data the same.
And if you export a list of installed applications and use it to reinstall to SSD then systems will be identical.
If keeping old install you can also go back and get anything you may happen to forget. Sometimes you may have customized grub or manually edited hardware configuration and those settings would be in /etc.

If you have fairly quick Internet, a new install does not take long and is straight forward. You also then have automatically housecleaned system also.

       Install to external drive. Also any second drive. Or any install with Something Else
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

    
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Also depending on size of SSD, you may want to split install and data. Some use a separate /home, many of us use separate data partitions. Then system is on SSD and data is on hard drive.
      
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by maazmahmood on 2014-07-16
My SSD will replace my current Linux HDD.  I do not have the EFI setup, is there a way to set it up now? I honestly don't know where grub is located, if it's located on the same drive as Linux, then no, Grub is not installed on the same physical drive as Windows boot. To be sure, how do I check where grub is installed?

By the way, how would I go about restoring the windows boot?

---

### Post by oldfred on 2014-07-16
I suggest Boot-Repair as that is the easiest. But do not click auto fix when you have more than one drive.
Use the advanced mode and choose operating system and drive to install boot loader. 
Then set in BIOS Ubuntu drive as default.

If in your working Ubuntu install you can easily install grub to sdb.
       sudo grub-install /dev/sdb
            sudo update-grub
    
But grub remembers where it was installed. You may need to update the drive used. (also another setting to change on clone).
       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc (BIOS) or dpkg-reconfigure grub-efi-amd64 (UEFI)
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

    Best to run the BootInfo report from Boot-Repair and it will show where boot loaders are and document many other settings and show details needed for booting. The first part of the BootInfo report is jsut bootinfoscript, a bash file. I use it everytime I run my rsync backup to document current configuration of system.

       Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/latest/download](http://sourceforge.net/projects/bootinfoscript/files/latest/download)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If not reusing hard drive you probably can use clonezilla. I have not used it but many have posted it works. I still think a clean install may be easier, but do not know details of clonezilla reinstall.

 [http://clonezilla.org/](http://clonezilla.org/)
fsarchiver
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page) 
[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

---

### Post by maazmahmood on 2014-07-16
So from boot repair I can select windows 7 loader, and install it on windows drive, right? And if I wanted to boot to Win 7 I'd have to go into BIOS and boot to that directly?

**UPDATE** Just looked at the link you provided regarding boot repair. It brings me to another question. If I select repair windows boot files. Will that restore windows boot loader onto the Windows HDD?

---

### Post by oldfred on 2014-07-16
In advanced mode you can reinstall a Windows type boot loader for BIOS/MBR type systems.
Boot-Repair does not work from inside Windows (it is running Linux scripts) and can only do very minor Window fixes. You need your Windows repairCD or flash drive to do most repairs for Windows.

If you want the original Windows boot loader on the Windows drive, you can use repair console from f8 or your Windows repair flash drive and run this from Windows repair terminal mode.
       [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
    
       BootRec.exe /fixMBR

 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

