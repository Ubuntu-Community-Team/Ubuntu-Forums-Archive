---
title: "Ubuntu / Kubuntu / Linux In General and M.2 NVMe"
date: 2018-05-05
forum: Hardware
---

### Post by DeadlyOats on 2018-05-05
So, I bought a brand new Samsung 960 Pro M.2 drive....

*sigh*

I have to go through contortions to install Windows 7 on it.  I had Microsoft email files to me, which I then have to include in a Win7 installation disk that I have to make myself, after extracting the files from my Win7 installation disk.  I think Microsoft emailed me an incorrect file, so I'm stuck on the Windows front.

What about Ubuntu, Kubuntu, or Linux in general.  Can Linux see and install on an M.2 NVMe drive without me having to do contortions and acrobatics with the command line?

EDIT:

I forgot to mention, I have a Kubuntu 17.04 install DVD...

---

### Post by oldfred on 2018-05-05
Is this an UEFI system? You may need to install in UEFI boot mode. 
Older system may not support NVMe.  And some have had to have UEFI updated to work correctly. Make sure you  have newest UEFI from your vendor.

Windows 7 may need drivers, but default install mode from DVD is BIOS only. You have to copy to flash drive and move boot files around to make it UEFI bootable.
Windows in UEFI mode only boots from gpt partitioned drives and only from MBR partitioned drives with BIOS. So if partitioning in advance, be sure to use correct configuration.

Many have installed on M.2 drives and some are the newer NVMe type. 
But depending on system, you may need boot parameters or other settings.

What brand/model system?
What video card/chip?

Have you tried live installer in live mode to see it it correctly sees your drive.

If UEFI see link in my signature. Nothing special on NVMe as far as I know.

 Support for NVMe in grub-mkdevicemap fixed in 2014
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1275162](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1275162)
spec entry for nvme devices (UEFI v2.4A 9.3.5.22)
[https://ubuntuforums.org/archive/index.php/t-2292993.html](https://ubuntuforums.org/archive/index.php/t-2292993.html)
> finally got my 2 SM951's dual booting Win10 and Ubuntu 15.10....and what a pain it was. 


With just SATA drives in UEFI and ASUS z97, I had many UEFI settings I changed, but did not have the issues above user seemed to have.  Newer versions seem much better, but also newer UEFI from vendors.

---

### Post by DeadlyOats on 2018-05-05
> Windows 7 may need drivers, but default install mode from DVD is BIOS only. You have to copy to flash drive and move boot files around to make it UEFI bootable.
 Windows in UEFI mode only boots from gpt partitioned drives and only from MBR partitioned drives with BIOS. So if partitioning in advance, be sure to use correct configuration.

..........

*sigh*

I did not know this....

I'll have to learn how to make a "flash" bootable Windows 7 installer....  I'll have to learn about gpt partitioning....

*sigh*

Hey, wait a minute!  Does that mean that Kubuntu 17.04 won't install via DVD either?  It has to be via Flash?


As for my PC hardware:

Asus X99-E WS motherboard.  It has the option to use BIOS or UEFI....  It has a NVMe compatible M.2 drive slot.

As for video card,  It's an nVidia 1080 TI graphics card.  I'm using an Intel i7 CPU.

---

### Post by oldfred on 2018-05-05
All Ubuntu installers are now hybrid. Many tools use dd under the hood and just image the DVD to flash drive. Or DVD & flash drive are the same.
And DVD and standard flash drive can be booted with UEFI or BIOS, it is then a choice in the UEFI menu as it sees both boot loaders, one in MBR for BIOS and one in /EFI/Boot/bootx64.efi for UEFI boot.

        How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
[https://superuser.com/questions/676249/clean-install-of-windows-7-pro-64-bit-on-a-uefi-laptop-with-gpt-partition](https://superuser.com/questions/676249/clean-install-of-windows-7-pro-64-bit-on-a-uefi-laptop-with-gpt-partition)
You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
Convert Windows 7 install to UEFI This user said he need the repair/recovery from his Windows 8 to convert Windows 7
[http://ubuntuforums.org/showthread.php?t=2304736](http://ubuntuforums.org/showthread.php?t=2304736)

Your nVidia card will need the nomodeset boot option. Some have had issues installing and use the internal Intel video to install, but I do not think the X99 has that option.


 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 

Only install nVidia drivers from Ubuntu, not directly from nVidia. If you must have latest nVidia driver there is a ppa. But if one driver installed, you must totally remove/purge old driver first. And reboot using nomodeset again.

Best to review link in my signature & then many links to more info if needed.

---

### Post by DeadlyOats on 2018-05-05
oldfred, you are seriously, awesome!

Thank you SO very much!

I have a lot of studying ahead of me, and I thank you for providing me with the resources.

Again, you have my deepest thanks!

---

### Post by QIII on 2018-05-05
Just to encourage you in your endeavors, the machine I am on right now -- my daily driver -- is running on an NVMe device.

---

### Post by pqwoerituytrueiwoq on 2018-05-07
I was able to install 18.04 to a M.2 SSD with no issue (Z97 platform)

The only issue i had was my bios said not detected under drives, but it shows it under the m.2 slot and in the boot drive list, so works...

if your have issues installing with your 1080ti you could just use a older lower end card you have lying around, like a gt 530, 610, etc. any old card supported by the same drive as the as the 1080ti then you swap the card after installing the driver

as for your issue installing windows there is a windows usb creator tool ms distributes, i would assume you use that and add the file they sent

---

### Post by alextdel on 2018-05-07
[I][B]Dual boot, two SSDs both NVMe
[/B][/I]
I have two NVMe M.2 drives, both installed from USB memory sticks images that I made from downloaded .iso files and the RUFUS application - made the USB images on a windows machine
My install is ...
**1. **250 GB Samsung EVO SSD M.2
Runs the Windows 10 install - installed first - in UEFI mode - look for the Windows partition that is FAT formatted as this holds the boot manager - UBUNTU will find this 
**2. **512 GB Samsung PRO SSD M.2
Runs my Ubuntu 18.04 install - UEFI mode - when installing from the USB drive, up I chose the custom partition selection (last selection on the screen) and selected the whole NVMe device to install to make sure the boot device was selected as the FAT formatted boot partition on the Windows drive M.2. (make sure you know which device and partition you are looking at) - Ubuntu had automatically found the correct partition for the boot sector (boot device) but I wanted to check.
[I][B]
-----
Note - for single NVMe drive dual boot install [/B][/I]
1. Install windows on the drive in UEFI mode - you will have probably three partitions made - 1. Recovery partition 2. Boot partition - this is the FAT formatted partition 3. The big Windows partition (C drive)
2. Shrink the Windows partition to allow space for your Ubuntu partition(s)
[You don't need to set up the partitions manually as below - you can just tell Ubuntu to install into a single partition that takes up the entire free space] 
I set up a single 256 GB SSD installation drive with the Ubuntu system as ...
 **a.** root partition '/' of 40 GB [which is quite big, you only need 20 to 30 I think]
 **b.** swap partition of about 8 GB [this is a bit 'old school' as if you have lots of memory you don't need this and also Ubuntu will use a swap file if needed - I believe] and
**c.** a '/home' partition of whatever is remaining of the space ) 
-----

I did try a Manjaro Linux install prior to Ubuntu and couldn't get Manjaro to see the Windows partition but I think I stuffed up the UEFI installs and had UEFI linux images and MBR-non UEFI Windows running - which is a recipe for confusion unless you really know what you are doing - which I don't.

Good luck but basically it is possible and works well even on multiple NVMe drives.
:)

---

