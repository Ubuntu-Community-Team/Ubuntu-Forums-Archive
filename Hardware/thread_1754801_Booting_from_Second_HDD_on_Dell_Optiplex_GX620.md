---
title: "Booting from Second HDD on Dell Optiplex GX620"
date: 2011-05-10
forum: Hardware
---

### Post by Monkadelicd on 2011-05-10
I can't seem to find a setting to get my Dell Optiplex GX620 to boot from the second HDD. 

It is detected and works fine(1 working NTFS partition, 1 ext4 Partition with Ubuntu 11.04, and 1 swap partition) but I can't boot from it.

I installed Grub2 to sdb3 (ext4 partition with Ubuntu installation) and my PC always boots straight to Windows without any boot loaders showing.

Does anyone know if I can use EasyBCD to add a Linux entry to the Windows boot loader? I have downloaded it and messed around a little but haven't made any changes to my MBR yet.

Any help would be greatly appreciated.

---

### Post by oldfred on 2011-05-10
I do not know about EasyBCD, supposedly it works.

Does your BIOS support choosing which drive is the boot drive. Only old systems that were IDE/PATA booted from primary master set with jumpers on hard drive or location on  cable (cable select). Any BIOS that supports SATA drives has a way to boot a second drive. And do you have a one time boot key, mine is f12.

But to get booting from a second drive to work you have to install grub2's boot loader to the MBR of the second drive.

If you can boot into your system, you do not have to use LiveCD, but do need to get grub to remember where to reinstall on updates.

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

You do not install grub2 to a partition as it is less reliable unless you absolutely have to. Since you have 2 drives, install grub2's boot loader to the MBR of the second drive and change BIOS to boot that drive.

---

### Post by Monkadelicd on 2011-05-10
My issue is how, if at all possible, to enable booting on a different HDD than the first one. 

As far as I can tell there is no setting to choose. I can select bootable devices and set order but I can't select specific HDDs just onboard SATA HDDs.

---

### Post by oldfred on 2011-05-10
If you have SATA drives there is a way. Some have it totally different BIOS entry - even on different page, and other have it when you select hard drives it opens another windows on which hard drive is first.

---

### Post by Monkadelicd on 2011-05-10
In Dell's System Setup document the BIOS options are all explained. For some ridiculous reason there is no way to boot from anything other than the primary drive be it hdd or odd.

I know you would think that any computer with SATA support would allow you to choose but it's just not possible with the Dell BIOS on the GX620. It's just not dual boot friendly.

Is there another way to dual boot?

---

### Post by oldfred on 2011-05-11
I just looked at a manual and it says f12 to boot USB and f2 to get into BIOS and BIOS has this:

Dell™ OptiPlex™ GX620
User's Guide 

NOTE: These options appear as **[B]Drive 0**[/B] through **[B]Drive 3**[/B] for the desktop, mini tower, and small form computers and **[B]Drive 0**[/B] though **[B]Drive 5**[/B] for the ultra small form factor computer. 

It almost looks like it is configured for one IDE and one SATA drive, but I did not read all the details. That could be an early BIOS, but you can only change boot order with SATA in BIOS as there are no jumpers.

---

### Post by Monkadelicd on 2011-05-12
[B]This is from Dell's Documentation:
[/B]

**Boot Sequence**

    This feature allows you to change the boot sequence for devices.
    **Option Settings **


[LIST]
[*]**Onboard or USB Floppy Drive —**  The computer attempts to boot from the floppy drive. If the floppy disk  in the drive is not bootable, or if no floppy disk is in the drive, the  computer generates an error message.
[*]**Onboard SATA Hard Drive**  — The computer attempts to boot from the primary serial ATA hard drive.  If no operating system is on the drive, the computer generates an error  message.
[*]**Onboard IDE Hard Drive**  — The computer attempts to boot from the primary IDE hard drive, if  applicable. If no operating system is on the drive, the computer  generates an error message.
[*]**Onboard or USB CD-ROM Drive**  — The computer attempts to boot from the CD drive. If no CD is in the  drive, or if the CD has no operating system, the computer generates an  error message.
[/LIST]

---

