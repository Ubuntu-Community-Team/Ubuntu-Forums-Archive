---
title: "First linux system; what do you think? Compatabilty &amp; more."
date: 2012-07-21
forum: Hardware
---

### Post by thatrandomn00b on 2012-07-21
As the title states, I decided to build my first system and also to move to Ubuntu from windows. Anyway, here are the specs:
Intel Core i5 3570K
Asrock *z77* extreme4
Kingston 8GB HyperX Genesis 1600MHz CL9 (Kit of 20)
Western Digital 2TB Caviar Black SATA III
Intel 120GB SSD 330 Series 2.5¨ SATA III Bundled Desktop Kit 
(Corsair Professional HX650W
Cooler Master HAF 912 Plus)

**Would this system be Ubuntu/ Linux -compatible?**

To the best of my knowledge it would be, but I'd like someone to confirm that. Info, especially on the compatibility of the motherboard with linux has been scarce.

[B]Do I need a graphics card?
[/B]Is there one you would suggest?[B]

Am I missing anything? Do you have any suggestions to make it better?

[/B]Thanks in advance? I'm not really sure how to close this...

---

### Post by ahallubuntu on 2012-07-21
Can you post the exact model number of the motherboard?  When I google for "Asrock extreme4" I get more than one model (different chipsets, one a P67, one a Z68 - the latter one is still in stock at NewEgg, the former isn't).

The motherboard chipset is probably the most important thing in determining compatibility.

---

### Post by thatrandomn00b on 2012-07-21
> **ahallubuntu said:**
> Can you post the exact model number of the motherboard?  When I google for "Asrock extreme4" I get more than one model (different chipsets, one a P67, one a Z68 - the latter one is still in stock at NewEgg, the former isn't).

The motherboard chipset is probably the most important thing in determining compatibility.
Oh yeah, sorry about that, it's z77.

---

### Post by UltimateCat on 2012-07-21
These websites might be of help to you-

[http://www.newegg.com/](http://www.newegg.com/)

And; Tiger Direct also-

[http://www.tigerdirect.com/applications/Category/guidedSearch.asp?CatId=28&name=Video-Cards&cm_sp=Masthead-_-Comp](http://www.tigerdirect.com/applications/Category/guidedSearch.asp?CatId=28&name=Video-Cards&cm_sp=Masthead-_-Comp)

I lot of folks are using the HD Graphics these days and Nividia G-force are good cards as well.

Good luck

---

### Post by ahallubuntu on 2012-07-21
> **thatrandomn00b said:**
> Oh yeah, sorry about that, it's z77.

It looks like some people have had issues with this chipset.  Read here for example:

[http://ubuntuforums.org/showthread.php?t=1995945](http://ubuntuforums.org/showthread.php?t=1995945)

In a couple of cases, upgrading to the 3.3 version of the kernel fixed freeze issues people were experiencing.  So be prepared for the possibility; at least there is a work-around if that happens to you.  I think with newer hardware you run more of a risk of compatibility issues not yet fixed in the Ubuntu repositories.

---

### Post by oldfred on 2012-07-21
Another somewhat newer article on z77, but a different vendor's motherboard.
[http://www.phoronix.com/scan.php?page=article&item=ecs_z77h2a2x&num=1](http://www.phoronix.com/scan.php?page=article&item=ecs_z77h2a2x&num=1)

Since it is very new hardware it is surprising that it works as well as it does.

You have lots of new system issues. UEFI install or BIOS install. gpt partitioning or MBR. IF dual booting with Windows and using gpt you have to use UEFI to boot. SSD configuration is also somewhat different. I only made a few settings, used gpt but do not dual boot on same drive with Windows and have only BIOS.
AsRock calls BIOS mode AHCI.

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution, Arch has good technical info.
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives) - SSD

[https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT](https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT)

---

### Post by thatrandomn00b on 2012-07-22
> **oldfred said:**
> Another somewhat newer article on z77, but a different vendor's motherboard.
[http://www.phoronix.com/scan.php?page=article&item=ecs_z77h2a2x&num=1](http://www.phoronix.com/scan.php?page=article&item=ecs_z77h2a2x&num=1)

Since it is very new hardware it is surprising that it works as well as it does.

You have lots of new system issues. UEFI install or BIOS install. gpt partitioning or MBR. IF dual booting with Windows and using gpt you have to use UEFI to boot. SSD configuration is also somewhat different. I only made a few settings, used gpt but do not dual boot on same drive with Windows and have only BIOS.
AsRock calls BIOS mode AHCI.

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution, Arch has good technical info.
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives) - SSD

[https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT](https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT)
I won't be dual-booting with Windows, either. (There is a chance of a dual-boot with another Linux distribution in the future, but a really small one, as if I want to explore other distros I'll run them in a VM. But, I'm getting ahead of myself.)

So, since I won't be dual-booting with windows, what do you suggest? (I'm reading the links you gave me, and trying to make sense of them, but it may take a while. Thank you, by the way.)

---

### Post by oldfred on 2012-07-22
This user has a similar card. Had some issues & seems to have worked them all out.
[http://ubuntuforums.org/showthread.php?t=2020496](http://ubuntuforums.org/showthread.php?t=2020496)

If only Ubuntu I prefer to keep system partition small and have separate /home or what I do move all data out of /home and keep /home inside / with only the hidden user settings and no data. I do this primarily because I am multi-booting versions of Ubuntu. So it may not apply to you.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
If gpt(not MBR) partitioning include these first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

If you're using UEFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning. You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS. You can boot via bios AND efi (after setting up your efi boot entry using efibootmgr or via efi shell and running the efi binary)

---

### Post by thatrandomn00b on 2012-07-22
@oldfred

So if I'm understanding you right, this is what I should/could do:
(I'll be using GPT since it's newer and because it appears I have no reason not to.)
In order have the ability to use either EFI, or BIOS: 
I should create an ESP partition first and depending on the tool I use, I should give it a flag/code. Then a 1 MB bios_grub partition, so that I'll be able to use BIOS as well. 

Do you suggest I put these on the SSD?

Then, for Ubuntu:

25 GB  / partition (on the SSD?)
 
A Swap partition, on the HDD. I'll be using 8GB of RAM, so about 8GB swap, or is that overkill? I guess if I need to hibernate, I can always add a Swap file, right?

Finally a separate /home partition, on the HDD? That is unless I manage to do what you suggested and keep /home in / and create a /data partition to put files such as music, videos etc. in it.

Am I missing anything?

By the way, where is /boot located? Should I make a separate /boot partition on the SSD?

Thanks for your patience.

Edit: Would the Intel 4000 HD be enough to run Virtual Box, or do I need a Graphics card?

---

### Post by oldfred on 2012-07-22
You should not need a separate /boot leave than in /.

My 60GB SSD with two / partitions. My /home is inside /. I am not using the efi now but may move drive to new system soon, so I created it. I am using the bios_grub for grub to install with gpt in BIOS mode.
```

fred@fred-Precise:~$ sudo gdisk -l /dev/sde
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sde: 117231408 sectors, 55.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 85A657E7-D379-4592-B060-E8EA09953D80
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 117231374
Partitions will be aligned on 2048-sector boundaries
Total free space is 3645 sectors (1.8 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          616447   300.0 MiB   EF00  
   2          616448          618495   1024.0 KiB  EF02  
   3          618496        58925055   27.8 GiB    0700  Precise
   4        58925056       117229743   27.8 GiB    0700  Quantal

```

I used gparted to partition it and the installer to format the / partitions. With an SSD I boot in 10 sec from grub menu to working system. About 20 seconds total with BIOS & grub loading, so I have no reason to hibernate. I have 4GB of RAM and almost never use swap (a good thing) but I have my swaps on each of the rotating drives.

Supposedly the HD4000 graphics are decent, but I do not know.

---

### Post by thatrandomn00b on 2012-07-22
@oldfred

Thank you, I think I've got it. Separating /data from /home will probably give me some trouble, but hopefully I'll manage.

One last thing, we does everyone seem to favor installing from a CD over installing from a USB, is there a problem with doing that?

---

### Post by oldfred on 2012-07-22
Some have issues with either one. 

I used to use CDs but I like to have a repair disk or two or three and was going thru many CDs on every update. So I converted to flash drives. Flash is usually quicker, also. I still make one CD, have several repair  ISOs on flash drives, but then I can update to the newest versions easily without wasting CDs.

I have gone one step further (A bit advanced and you need grub2 as your boot loader) now that I know grub2 can loopmount the ISO directly. Or you can install from a rotating drive to your SSD. When I did that I never saw an install go so fast even with the extra downloading of the updates.

---

### Post by thatrandomn00b on 2012-07-22
> **oldfred said:**
> I have gone one step further (A bit advanced and you need grub2 as your boot loader) now that I know grub2 can loopmount the ISO directly. Or you can install from a rotating drive to your SSD. When I did that I never saw an install go so fast even with the extra downloading of the updates.
  It does sound advanced, but I'm curious, so, do you have any links going into more depth? Also, what program would you suggest using to "burn"(can't recall the right term) the .iso to the USB?
Or, maybe I should make a new thread for this?

Edit: I've been rereading your suggestions and I don't understand something: If I use gparted to partition my disks and create both esp and bios-grub, which one should I give a boot flag?

---

### Post by oldfred on 2012-07-22
The esp gets the boot flag or in gdisk it is ef00. A bios_grub is ef02. Other codes for data partitions in gdisk. But I use gparted to create, but gdisk to review and if need be repair gpt partitions.

There are a bunch of links to ways to directly boot ISO. I did it before there were scripts. Learned from one early script, drs305's instructions, and Herman's site on many boot issue with lots of detail.

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

Pendrive also has page on booting ISOs
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

Also 
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by thatrandomn00b on 2012-07-23
I think I've understood as much as I possibly can before getting my hands on the system and trying to install. There may be a couple of things I need to read on, such as optimizing partitioning for a system with both HDD and SSD and on how to use gdisk, but I guess if I run into problems, I'll ask on a thread dedicated to partitioning.

Thanks to everyone who replied, and especially to oldfred for all your help and useful links.

(Will be marking thread as SOLVED, in a bit.)

---

