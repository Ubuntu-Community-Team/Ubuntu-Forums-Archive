---
title: "More than 4 primary partitions? (GPT)"
date: 2011-07-27
forum: Hardware
---

### Post by azzamite on 2011-07-27
Hi there

I understand that the GUID Partition Table (GPT) can be used to create more than 4 primary partitions among other things, so I'd like to use this partition table instead of the usual (~1980) partition table.

I formated one laptop (HP, turion 64 x2) about 3 years ago with GPT using gparted and didn't work (maybe I didn't do it right?), either I couldn't install any OS at all or they didn't boot, whichever the case I don't remember now...

So I was wondering if there is a way to know if this new system support it before doing it?

The system is a Dell laptop with i7 processor

Cheers

---

### Post by srs5694 on 2011-07-27
You can certainly use GPT for a Linux-only installation, although you need (or at least will benefit from) one of two types of partitions, so be sure to create one (or both, if you're uncertain of which you might need):


[list]
[*]On BIOS-based computers, GRUB 2 uses a [BIOS Boot Partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition), if available, to store part of its boot code. Without this partition, GRUB 2 might or might not install properly, and if it does install, it'll be more fragile than it would be with a BIOS Boot Partition.
[*]On UEFI-based computers, an [EFI System Partition (ESP)](http://en.wikipedia.org/wiki/EFI_System_partition) is required on the boot disk. This partition holds EFI boot files, including the EFI version of GRUB (or ELILO, or whatever other boot loader you use).
[/list]


If you plan to dual-boot with Windows, though, be aware that Microsoft has chosen to support only the older MBR partitioning system on BIOS-based computers and only GPT on UEFI-based computers. Thus, if you intend to dual-boot with Windows, you should select your partitioning system based on the type of firmware you've got. A wrinkle on this is that most (perhaps all) current x86-64 UEFI systems include a BIOS compatibility mode, so the computers can boot in either UEFI or BIOS modes. Manufacturers sometimes hide these options and even downplay the UEFI nature of the firmware, so I've been seeing a lot of posts from people who are confused about how their computers are booting lately. Many of the computers introduced in the last few months are UEFI-based, but few computers sold before 2011 were.

---

### Post by JC Cheloven on 2011-07-27
Hi, I thought that gpt was only for managing large filesystems (larger that 2Tb), so I learned something new myself. Anyway, you may find interesting this article
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)

Ok, let's face it, I mainly posted here porcause me ha likeado your firmatura :)

---

### Post by azzamite on 2011-07-27
> **srs5694 said:**
> 
If you plan to dual-boot with Windows, though, be aware that Microsoft has chosen to support only the older MBR partitioning system on BIOS-based computers and only GPT on UEFI-based computers.

Actually, I need to triple-boot with FreeBSD too...

So you basically say that there exist the possibility that my laptop supports both MBR and UEFI and so I could use either as long as I use the efi version of the boot loader in case of the GPT?

Because, currently I don't have any grub-efi package installed.

I think I'll format an usb key with GPT and install ubuntu there to check if it works...

---

### Post by srs5694 on 2011-07-27
I have no idea what type of firmware you've got. If you want to boot Windows with it, though, you pretty well have to use the type of partitioning system that Microsoft supports with that firmware (MBR with BIOS or GPT with UEFI). AFAIK, there are only three ways around this Microsoft limitation:


[list]
[*]You can use a different partition table type for a disk from which Windows does not boot; the firmware/partition table linkage applies only to the Windows boot disk.
[*]You can [use UEFI DUET](http://www.rodsbooks.com/bios2uefi/index.html) to add UEFI capabilities to a BIOS-based computer. This is a highly advanced/experimental solution, though, and it seems to work best with Intel CPUs rather than with AMD CPUs.
[*]You can use a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) to make up to three GPT partitions accessible to Windows as if they were MBR partitions. Hybrid MBRs are flaky and dangerous, though, so I don't recommend using one unless you've got absolutely no other choice -- say if you need to dual-boot Windows and Linux from a 3 TB disk.
[/list]

---

