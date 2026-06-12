---
title: "MSI P67A C43 B3 UEFI boot compatible?"
date: 2015-03-25
forum: Hardware
---

### Post by fwrun2011 on 2015-03-25
Hi;
I have a mutli-boot system with this MSI P67A C43 B3 mobo. The OS's I have installed are Ubuntu 14.04.2 amd64 (2 installs at present), and Windows 7 Ultimate x64.
I would like to make some changes to my hard drive/partition system. Currently I have a 1TB SATA drive with standard MBR partitions (two primary, and several in extended space). I am using ext4 for the Ubuntu, and ntfs for Windows.
I would like to change the partition type to GPT, but I am reading conflicting information about whether or not Windows 7 x64 will boot on a GPT drive. Some articles say that only the x64 version will, and starting with Win 8, all versions will boot on GPT.

Now, I am trying to find whether the MSI P67A C43 B3 board will fully support UEFI booting. The specs say that is does have UEFI BIOS, and I can apparently boot from UEFI USB drive. I am able to boot from a 2GIB usb stick with an image of Ubuntu 14.04.2 on it - but then, I have not actually installed Ubuntu onto that usb stick. I simply created a bootable usb drive with the .iso image for Ubuntu. 
In the BIOS, the only setting for UEFI I see is the USB thumb drive I have installed.

I do know that I can boot from a GPT disk into Ubuntu 14.04.2 - or at least I believe I am booting from that disk. When I installed Ubuntu onto this GPT disk, I did select the same disk for boot at the bottom of the screen.

Even if I cannot boot Windows on the GPT disk, I think I can still put Ubuntu on the GPT, possibly create a dedicated GRUB2 partition on that drive, and then install Windows on another HDD (MBR) and chain-load from GRUB.

Thanks for your help.

FW

---

### Post by oldfred on 2015-03-26
Windows only boots from gpt partitioned drives with UEFI.
Both Windows and Ubuntu only boot from MBR drives with BIOS.
UEFI and BIOS are not compatible, they write UEFI/BIOS data differently to drive for operating system to use, so you have to reboot to switch. Or you cannot use grub to choose any system not installed in same boot mode.
You can have systems in different boot modes, but it can be a hassle to reboot and switch modes. Some auto switch, know mode installed, others may require you to turn on/off UEFI or CSM mode for system to boot in correct mode.

Windows has supported UEFI boot since Vista x86_64    . But some have said the default DVD Windows 7 is only BIOS and you have to copy it to a flash drive and make a couple of updates to make it a UEFI installer. Windows 8 can be installed in UEFI or BIOS mode, but all pre-installed systems are UEFI.
Both Windows & Ubuntu install in the same mode as you boot install media.

You can also boot Ubuntu in BIOS Mode from a gpt partitioned drive. My old BIOS system booted XP on a MBR partitioned drive and Ubuntu in BIOS mode from gpt partitioned drives (several drives all gpt).

I use gparted to partition drive in advance. You can also use gdisk.
 Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

I also add both an efi partition for UEFI boot at beginning of drive as that can be difficult to add later and a bios_grub partition for BIOS boot. Then I can install either way, or change later.


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)


 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)


 Convert Windows BIOS to UEFI - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)

---

### Post by fwrun2011 on 2015-03-26
Thanks; That is very informative.
I am still not sure whether or not my mobo fully supports UEFI.
It does have several UEFI options:
I can boot into a UEFI shell.
I can boot UEFI if I have a USB device containing the proper files. Perhaps I can install Lubuntu onto that 2GIB flash stick to check if it will boot UEFI from there.

I don't really *need* to use GPT, but this is a learning experience, and I would like to try it. At this point, the computer is not doing anything useful anyway, so why not 'play around' with things. All of my data is backed up.

FW

---

### Post by oldfred on 2015-03-26
If you can boot Live installer in UEFI mode then it is UEFI capable. And to install in UEFI mode you have to boot installer in UEFI mode. If drive is gpt and you have an efi partition, Boot-Repair can convert a BIOS boot install  to UEFI boot, but better to install UEFI from the start.

You can do a full install to external device, but a full install requires a larger flash drive 16GB or more. And then you cannot save a lot of data to flash drive. I now format all my larger flash drives as gpt.

 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

        [http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

    
       Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode](https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode)
[http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/](http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/)
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)

---

### Post by fwrun2011 on 2015-03-26
Thanks.
I am going to attempt to put GRUB2 on the flash drive as UEFI boot and see what happens.

Edit: My system is apparently not capable of booting UEFI. Even when I plug in the USB flash drive containing Ubuntu 14.04.2 with proper EFI folder, and set BIOS to boot from it, the result is always a BIOS boot. I was mistaken to say that I had the option to boot a UEFI USB device. The only UEFI boot option I have is to go into the shell that is built-into the BIOS. From there, I may be able to configure hard drives to boot in UEFI, but I kind of doubt it. I think that my mobo, being a few years old was a very early implementation of UEFI.

In any case, I am going to move onto something else, since I really did not need UEFI in the first place - especially since I still have Windows installed on the system.

FW

---

