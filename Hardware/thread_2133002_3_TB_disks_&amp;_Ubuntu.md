---
title: "3 TB disks &amp; Ubuntu"
date: 2013-04-06
forum: Hardware
---

### Post by Nwwmac on 2013-04-06
I'm considering building my next PC. I would like to have Ubuntu on an SSD and my files on a large disk. I know that 2T disks are not a problem, but what about 3T? Will it make any difference that the OS is on the SSD? 

If there is any command line kung fu to be done, where would I find that information? 

Any help would be appreciated. ;)

---

### Post by oldfred on 2013-04-06
Whether system is UEFI or BIOS, both SSD & hard drive should be gpt partitioned. Hard drive will have to be gpt to see more than 2TB. You can use gparted to create gpt partitioning or download gdisk which is fdisk for gpt partitioning.

       MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

            GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

            GPT Advantages (older but still valid)  srs5694 post #@:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

      
 Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
Arch suggests gpt for SSD. Only if installing Windows on older system may you want MBR as Windows only boots from gpt with UEFI. 
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by Nwwmac on 2013-04-06
This will be a Linux machine so Ubuntu would be the only OS. Can I do the formatting from the installer, or do I need to use Gparted from the install disk? It sound like you're suggesting it will straightforward if I use the standard tools (which am planning to do, ie. Gparted and EXT4).

---

### Post by oldfred on 2013-04-06
All new computers are now UEFI but have the BIOS mode. Many are more familiar with BIOS.

IF you want UEFI, but you may not have secure boot?

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

