---
title: "Grub as a bootloader ? Very confused :("
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by badspell68 on 2009-02-20
I have had Ubuntu on my Dell Laptop for some time and recently added XP on a separate partition. Can’t figure out what to write in Grub to allow it to boot XP too?

---

### Post by hlmindustries on 2009-02-20
[http://www.linuxquestions.org/questions/linux-software-2/how-do-i-add-windows-xp-to-grub-boot-loader-375198/](http://www.linuxquestions.org/questions/linux-software-2/how-do-i-add-windows-xp-to-grub-boot-loader-375198/)

that should answer a few questions..

---

### Post by badspell68 on 2009-02-20
Still having problems getting Grub to start windows. I now have what is listed below in grub for windows and it does not work. I also added the partition info hoping it will help (sort of new at this):

Title              Microsoft Windows XP Prof
root               (hd0,2)
#makeactive
#chainloader        +1


My partitions list like:
/dev/sda1     etx3        /                (this is ubuntu)
/dev/sda2     fat32      /media/disk-1    (this is XP)
/dev/sda3     fat32      /media/disk       (storage)
/dev/sda4     extended                    (don't know what this is)
/dev/sda5     linux-swap

---

### Post by dakiro on 2009-02-20
just add this to boot.lst (probably in /boot/grub

title find and load NTLDR of Windows NT/2K/XP
fallback 1
find --set-root /ntldr
chainloader /ntldr
savedefault --wait=2

---

### Post by badspell68 on 2009-02-20
what is boot.1st

---

### Post by badspell68 on 2009-02-20
Also, if I try booting the win partition it I receive a message that says there is not a bootable OS on the partition. It was working just after the install and before I got grub up and running again??

---

### Post by unutbu on 2009-02-20
badspell68, please follow these instructions [http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)
to run boot_info_script.sh. The output from this script will help us understand your boot setup.

---

### Post by cariboo on 2009-02-20
Windows always wants it's boot files on the first partition of the first hard drive, I would suggest backing up your important data, and then reinstall. Partition your hardrive using the Windows installer, only partition enough space to install Windows and leave the rest of the drive blank, then install Ubuntu and use the installer to partition the rest of the hard drive.

You can also resize your Ubuntu partition, and create a very small boot partition for Windows boot files. This could lead to problems though if you already have 4 primary partitions. You will also have to create a new /boot/grub/menu.lst to reflect the changes you have made.

Jim

---

### Post by badspell68 on 2009-02-21
Is there a simpler way? I have Ubuntu on the first partition and windows on the 3rd now. I updated grub and when I try to boot from hd3 I receive a message error 12: Invalid device

??

---

### Post by meierfra. on 2009-02-21
Grub starts counting at zero. So if windows is on the third  partition you have to use "root (hd0,2)". If this does not solve your problem, follow the advice from post 7.

---

### Post by TimDaniels on 2009-02-22
> **cariboo907 said:**
> Windows always wants it's boot files on the first partition of the first hard drive, [.....] 

Windows NT/2K/XP/Vista wants its boot files in the partition marked "active" in the hard drive that has priority in the BIOS's Hard Drive Boot Sequence.  In some BIOSes, the Hard Drive Boot Sequence is a list that can be completely arbitrary - settable by the user in the BIOS.  In other BIOSes, the hard drive having boot priority is the specific hard drive set as the "enabled" hard drive in the BIOS.  In either case, the "active" partition can be **any** partition on **any** hard drive in the system, and it does not need to be the 1st partition on any hard drive, and the hard drive containing the boot files does not need to be the physically "first" hard drive, but rather the first in the Hard Drive Boot Sequence or that hard drive which has been set as the boot "enabled" hard drive.

I've heard that earlier Windows OSes assumed that the first partition on the first hard drive would contain the boot files, but that was a long time ago and at a time when PCs usually had only 1 hard drive.

*TimDaniels*

---

### Post by TimDaniels on 2009-02-22
> **badspell68 said:**
> I have had Ubuntu on my Dell Laptop for some time and recently added XP on a separate partition. Can&#8217;t figure out what to write in Grub to allow it to boot XP too?

When you installed WinXP, the installer replaced the Ubuntu MBR (which normally contains Grub) with Microsoft's MBR.  You can either replace Grub in the MBR and put an option in Grub's boot menu to pass control to XP's load manager (ntldr), or you can add an option in XP's boot menu (\boot.ini) to pass control to Grub (which you can place in the Ubuntu partition).  The following website should help:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm).

*TimDaniels*

---

### Post by badspell68 on 2009-02-22
Thanks!

Thant did it.

---

