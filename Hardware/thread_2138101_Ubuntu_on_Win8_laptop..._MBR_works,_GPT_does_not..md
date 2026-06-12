---
title: "Ubuntu on Win8 laptop... MBR works, GPT does not."
date: 2013-04-23
forum: Hardware
---

### Post by Roasted on 2013-04-23
i have an ASUS S56C. It came pre-installed with Windows 8. I disabled Secure Boot from the BIOS and installed Ubuntu Linux 13.04 via LiveUSB flash drive. The installation succeeded, however afterwards I was unable to boot up properly. In fact, the drives just were not being seen whatsoever in the BIOS. I noticed a pattern through experimenting... If I installed Ubuntu on a drive with an MBR table, it installed and booted fine. If I installed Ubuntu on a drive with a GPT table, it installed fine but wouldn't be visible to the BIOS to boot afterwards.

While on one hand, I could use MBR, I'd really like to figure out how to get GPT working. Some discussions with both Windows channels and Linux channels reveals one similarity - everybody believes that the operating system has nothing to do with it, and that the issue is largely between the BIOS and the hardware itself. For what it's worth, I did successfully flash the latest BIOS without issue.

I tried several different partitioning schemes but have yet to find one that worked using GPT as my partition table. I set a 1MiB partition, unformatted, and flagged it as bios_grub, but that did nothing. I also tried to set a separate /boot partition @ 500MB, but that too did nothing. Overall, GPT was an instant road block, whereas MBR worked fine. But.... why? Does anybody have any idea as to why this is or what I can do to get GPT working?

---

### Post by audunpoi on 2013-04-23
I don't know if this is related to GPT but you try "boot-repair"?
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Roasted on 2013-04-23
Thanks for your suggestion, but I ended up doing a little trial run. I decided to give Ubuntu the chance to utilize their guided installer and see what it does. I've done manual partitioning for years now, so I wasn't sure what the guided partitioning was capable of. I let it go through the ropes and sure enough, with Secure Boot Control - Disabled and Launch CSM - Enabled in the BIOS, using GPT partition tables, Ubuntu booted without issue. This surprised me because this very setup before failed for some reason.

I fired up GParted and saw that Ubuntu set up its own FAT32 partition mounted at /boot/efi. That was the winning ticket. I ended up redoing my install and choosing manual partitioning and set up my scheme to look like what GParted presented to me after Ubuntu did it on its own via guided method the first time around. Sure enough, it worked fine.

Note: Don't confuse "labels" with "mount points." Earlier I tried to do an install and it failed, but /boot/efi as the label does nothing when its mount point should be /boot/efi! Also, I noticed that in the advanced menu, instead of selecting FAT32 and /boot/efi for the mount point you can just select EFI Boot Partition as the file system type. That seemed to do what I needed without issue.

I am suddenly despising Microsoft and their ridiculous Secure Boot a lot less thanks to the hard work of the developers who made this capability happen with ease. It's clear I was just overcomplicating it at first. :)

---

### Post by oldfred on 2013-04-23
I only have BIOS and have been using gpt partitioning since 10.10. I have to have the bios_grub partition.

With the new UEFI systems you need the efi partition and it should be first. But UEFI only boots from the efi partition and you only can create an efi partition in gpt partitioning. With gparted you use the boot flag, or you can use gdisk which is the fdisk equivalent for gpt drives.

How you boot installer is how it installs. So if you boot in UEFI mode it will install in UEFI mode, if you boot in Legacy/CSM/BIOS mode it will install in BIOS boot mode, but Ubuuntu may boot from either MBR or gpt partitioned drives with BIOS mode.
Windows only boots from gpt drives with UEFI, but a BIOS Windows will read NTFS partition on a gpt drive (except XP).

       three Linux partitioning tools: the fdisk family [fdisk, sfdisk, and cfdisk], the libparted family [GNU Parted, GParted, Palimpsest Disk Utility, and several others], and the GPT fdisk family [gdisk and sgdisk]. 

gdisk is in the repository, but if using gpt, I would suggest installing gdisk.
sudo apt-get install gdisk


            GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)


 An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning. You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS. You can boot via bios AND efi (after setting up your efi boot entry using efibootmgr or via efi shell and running the efi binary)

---

### Post by Roasted on 2013-04-23
> **oldfred said:**
> 
How you boot installer is how it installs. So if you boot in UEFI mode it will install in UEFI mode, if you boot in Legacy/CSM/BIOS mode it will install in BIOS boot mode, but Ubuuntu may boot from either MBR or gpt partitioned drives with BIOS mode.

When you say BIOS mode, you mean "the mode your BIOS is in when Secure Boot is disabled", correct? Is the EFI partition still relevant even when in BIOS mode? Reason I ask is on this particular model laptop (ASUS S56C), these were my findings:

Ubuntu 13.04 - No EFI partition - GPT Table - Installs fine, won't boot.
Ubuntu 13.04 - No EFI partition - MBR Table - Installs fine, boots fine.
Ubuntu 13.04 - EFI partition - GPT Table - Installs fine, boots fine.

*all of the above is with Launch CSM enabled and Secure Boot Control disabled*

In my case, it seems as if the EFI partition was needed regardless if I wanted to use GPT tables. MBR was fine without EFI, but GPT needed it. And like I said, I never had Secure Boot Control enabled through any of this. It was the first thing I disabled.

---

### Post by oldfred on 2013-04-23
Not sure about your UEFI. Some seem to have Secure boot on/off, UEFI on/of or when off then in CSM mode. Some have CSM on which means no UEFI mode at all or the old BIOS mode.
        UEFI Compatibility Support Module (CSM)
Or there is not really a BIOS anymore with UEFI although many including me are still calling it that.

But some seem to have a UEFI or CSM auto mode. Where which ever it finds it uses, but Secure boot has to be off.

And it could be something specific about your UEFI. Vendors have hard coded changes against UEFI specifications either accidentally or intentionally.

I would have like to see BootInfo before and after each install as that shows all the details of where boot files are.
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

