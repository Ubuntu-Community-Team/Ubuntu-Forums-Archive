---
title: "Some Basic Questions about UEFI on dualboot"
date: 2012-08-15
forum: Hardware
---

### Post by venky96 on 2012-08-15
So I read a lot about UEFI and it really got me hooked. 
In my bios options it allows me enable UEFI and look up for UEFI shell.

1)I Understand I need a shell file for that and it seems like tianocore is best option.But I think i'll get an official efi file from ASUS. I HAVEN'T DONE ANY OF THE BELOW STEPS,I JUST WANT TO VERIFY BEFORE I ATTEMPT THEM.

2)The disk has to be parted in GPT.Also,I need to Create an EFI partition - How Do I do that? 

3)After that I create that partition I need to place the EFI shell in that partition and when I attempt to launch EFI shell from BIOS it will launch the EFI shell. 

4)What happens after this? I'm currently confused. I know it doesn't have many advantages since I don't have disk space larger than 2 TB but I want to learn about it. 


I want to Dualboot Windows 7 and Ubuntu 12.04. 
Any links to HOW-TO's would be awesome. Also,I still dont understand what would happen after I launch the EFI shell. Any useful guidance would be Appreciated since I seriously want to pursue attempting to use UEFI.

---

### Post by oldfred on 2012-08-15
UEFI is a bit more complex, and with Ubuntu what video driver you have also can be an issue. Often nomodeset is required to boot liveCD/USB or first install.

Most that have reported success have partitioned in advance and then used manual install. Windows also needs extra partitions.

Some Windows info.
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Arch has some really good info on UEFI and related issues:
Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)
Recompiling GRUB not required with newest versions of grub.
Creating efi partition & folders in advance works.Must be 64bit version to have UEFI 

Both Windows and Ubuntu will from an UEFI boot menu offer two choices, one UEFI/efi and the other BIOS/legacy/AHCI or whatever your system calls it. Both Windows & Ubuntu have to be either UEFI or both BIOS mode. You cannot mix them without major issues. Whichever mode you boot installer in, will be how it installs.

GUIDE: (U)EFI installation Also full install post #52 superfreak on pg.6
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)

UEFI dual boot two drives
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)
UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)
UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)
Dual Video Intel & nVidia
[http://ubuntuforums.org/showthread.php?t=1994622](http://ubuntuforums.org/showthread.php?t=1994622)
Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)
(Phoenix Tiano). The every-other boot problem is a bit decieving: What happens is it hangs on a warm/reboot. Boots work every time from cold/power-up. Yes, a stand-alone install of Win 7 SP1 has the exact same problem as Ubuntu. I suspect this is a Phoenix/Acer issue but who knows.

Grub used to have a bug where it erased the efi partition when installing so be sure to back that up before installing Ubuntu if you install Windows first.

You can use gparted to create a gpt drive. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning. But I have BIOS and have to have a bios_grub partition which you do not need if booting with UEFI.

In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

---

### Post by venky96 on 2012-08-15
Thankyou very very much for your answer.Now im starting to understand the technology behind UEFI. Thanks a lot. Couldn't be more thankful.

---

