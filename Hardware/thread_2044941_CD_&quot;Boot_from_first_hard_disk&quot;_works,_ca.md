---
title: "CD &quot;Boot from first hard disk&quot; works, can't boot to HD without CD."
date: 2012-08-20
forum: Hardware
---

### Post by Jeandré on 2012-08-20
Just did a clean install of Xubuntu 12.04 amd64 on a new Western Digital wd30ezrx 3TB hard disk - no errors during install. The mainboard is an Intel dq35mp (dq35mpe) (which ran Ubuntu 10.04.4 with Xfce fine).

When trying to boot to the hard disk, it stops at "no bootable device -- insert boot disk" (after I disabled "Boot to network" in the BIOS).

When booting with the Xubuntu install CD (alternate ISO) from which I just installed*, I enter on "English" from the language menu, and then select "Boot from first hard disk", from which Xubuntu boots fine - I can save files and access them again when booting the same way later.

Anyone know how to not have to boot off the CD? I think it's a problem with the Intel mainboard not wanting to boot from the wd30ezrx, not a Xubuntu problem - but since the Xubuntu install CD can access the hard disk I'm hoping someone knows how to get past the Intel problem.

*I have to choose option 1 when asked to "Select CD-ROM Boot Type" after listing two options with no text (option 2 doesn't work).

---

### Post by cbanakis on 2012-08-20
If your system has more than 1 hard drive in it, the installer may have loaded the boot loader on the wrong hard drive.

You can confirm this by going into your BIOS, and changing the 1st boot drive to the others in your system.

If that works, you could leave it that way, but I would recommend re-installing the right way.

Easiest way to force it to install on the right drive, is to physically un-plug the other drives till after install completes.

Obviously, it would be easier than that, if you know what your doing in the advanced install options.

But un-plugging the other hard drives would be the "Lazy Easy Way"

Let me know if this helps.

---

### Post by Jeandré on 2012-08-20
> **cbanakis said:**
> If your system has more than 1 hard drive in it

I only have the 1 hard drive in: the Western Digital wd30ezrx. I actually only have 1 SATA data cable - I wanted to get another to later put my old hard drive in to copy from it rather than copy from my slow backup drive over USB2.

---

### Post by cbanakis on 2012-08-20
Hmmm....

If you had a flash drive, or any kind of storage connected to your computer other than the 1 WD HD, it could have put the boot loader on there?

Someone in the forums had a similar issue, and it turned out, they had their CF card from their camera plugged in, and thats where the boot loader got installed.

Otherwise...

Did you partition the drive manually during install?

Or did you just do automatic?

Doing automatic should work perfect if the system only has 1 drive, and your installing off a cd.

---

### Post by cbanakis on 2012-08-20
Another thought...

I don't mean to make a "Is the computer plugged in?" type of suggestion, but...

Did you change your BIOS to boot from CD so you could install, and then maybe forget to change it back?

---

### Post by oldfred on 2012-08-20
Since it is a 3TB drive, it should be gpt partitioned. Did you or the installer create the 1MB bios_grub partition for grub2 to install correctly.

May be best to run the BootInfo report from Boot-Repair.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by Jeandré on 2012-08-21
> **cbanakis]If you had a flash drive, or any kind of storage connected to your computer other than the 1 WD HD, it could have put the boot loader on there?[/QUOTE]

Nothing else connected other than power, monitor, mouse, keyboard, iBurst modem, and speakers.

[QUOTE=cbanakis]Did you partition the drive manually during install? Or did you just do automatic? Doing automatic should work perfect if the system only has 1 drive, and your installing off a cd.[/QUOTE]

Automatic: guided using entire disk, SCSI1 (0,0,0) (sda)

[QUOTE=cbanakis said:**
> Did you change your BIOS to boot from CD so you could install, and then maybe forget to change it back?

The BIOS default boot order was CD, HD, Ethernet. My first reboot after installation, CD removed, gave an error about not being able to boot to network (can't remember the exact error message). I disabled "Boot to network", and then got "no bootable device -- insert boot disk". The boot order then was CD, HD, meaning it should try the HD if it couldn't boot from CD. After reading your message I swapped it tho to HD, CD, but the same error without a CD (I've swapped it back to CD, HD).

[QUOTE=oldfred]Since it is a 3TB drive, it should be gpt partitioned. Did you or the installer create the 1MB bios_grub partition for grub2 to install correctly.

May be best to run the BootInfo report from Boot-Repair.[/QUOTE]

That it's 3TB may very well be the problem, because my old small Seagate drive is fine on the PC.

I'll try Boot-Repair Wednesday.

---

### Post by Jeandré on 2012-08-21
> **oldfred said:**
> Did you or the installer create the 1MB bios_grub partition for grub2 to install correctly.

I remember only 3 partitions made with the guided partitioning of the entire disk: #2 being ext4, and #3 being swap. Maybe I'll try reinstalling Wednesday with manual partitioning, after looking up gpt.

---

### Post by oldfred on 2012-08-21
I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

In GPT fdisk (gdisk), give bios_grub a type code of EF02. 
Or with terminal:
sudo parted /dev/sda set <partition_number> bios_grub on

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
If you're using UEFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP)
If a new drive, to be safe, create both of these partitions, in addition to your regular Linux partitions. But the efi partition has to be first. Do not configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.

---

