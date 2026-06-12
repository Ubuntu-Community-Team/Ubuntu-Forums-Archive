---
title: "Partition &gt;30gb?"
date: 2008-08-28
forum: General Help
---

### Post by Gabt on 2008-08-28
Hey, 

Ive installed my ubuntu via wubi, as it was the only way i could install ubuntu, i kept getting hda: drive not ready for command upon using a disk. Both x32 and x64 cd's. Anyway, i used wubi, and i picked the max parition size, 30gb. But its installed onto a 149gb parition, is there is any to "stretch" the linux filesystem to use all that space? This is going to be my initial OS, dont plan on uninstalling it. Windows is installed on another HD, but during the wubi install i chose the free HD, the 148gb. I can live with keeping windows to ensure ubuntu boots, ive read my virtual disks are there, and i cant delete windows, thats fine. But i want more space in ubuntu as its my primary OS, allready down to 6gb and i wanna get ALL those games in the repo :P :D

Cheers.

---

### Post by arch0njw on 2008-08-29
Use the GParted Live CD to "stretch" the mount.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Gabt on 2008-08-29
Ive allready tried using Gparted thats included on 1 of my other distro CDs.
It only resizes the physical partition, im looking for a way to expand these virtual disk wubi uses.

---

### Post by DanJC on 2008-08-29
I'd like to do this too, there's a whole bunch of free space that wasting away on Windows that I'd like to use for this.

---

### Post by Gabt on 2008-08-29
Bump.

---

### Post by arch0njw on 2008-08-29
> **Gabt said:**
> Ive allready tried using Gparted thats included on 1 of my other distro CDs.
It only resizes the physical partition, im looking for a way to expand these virtual disk wubi uses.

I'm not sure what you mean by the virtual disk that wubi uses.  There are primary and logical partitions.  Then there is LVM -- logical volume management.  If you are using LVM, gparted cannot help you; and neither can I :(

In a terminal, please run "sudo fdisk -l" and post it here.  Thanks!

---

### Post by ac1d6urn on 2008-08-29
Wubi guide recommends [upgrading to a standard install on a new partition via LVPM first]("https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?") - they've got a pretty good set of instructions on that too.  Have a look.  

If you're still running into an hda error, there's an alternative solution on that page right below on how to add a new virtual drive to wubi for your software installs.

---

### Post by Gabt on 2008-08-29
> **arch0njw said:**
> I'm not sure what you mean by the virtual disk that wubi uses.  There are primary and logical partitions.  Then there is LVM -- logical volume management.  If you are using LVM, gparted cannot help you; and neither can I :(

In a terminal, please run "sudo fdisk -l" and post it here.  Thanks!

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7fd607a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19189   154135611    7  HPFS/NTFS
/dev/sda3           19190       19457     2152710   82  Linux swap / Solaris

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc64ec64e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10010    80405293+   7  HPFS/NTFS

```




> **ac1d6urn said:**
> Wubi guide recommends [upgrading to a standard install on a new partition via LVPM first]("https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?") - they've got a pretty good set of instructions on that too.  Have a look.  

If you're still running into an hda error, there's an alternative solution on that page right below on how to add a new virtual drive to wubi for your software installs.
Thanks, ill look into that. Theres certainly no error with either of my hard drives, i know this because ive ran multipl tools to check. Ive also installed Gentoo linux with ease, any windows version. Its just ubuntu cds that wont work, after alot of fiddling, ive come to the conclusion that my onboard IDE chip is unsupported, or bugged. I have a few I/O buffer errors too, but i fixed those turning off un-needed pnp devices in the BIOS.

---

### Post by Gabt on 2008-08-29
Ok, LVPM didnt work. It then failed to mount the root device, i managed to put thing back to the way they were tho. Seems im going to have to keep using the virtual disks and keep my windows installation, how do i go about making this virtual disk bigger?

---

### Post by Crafty Kisses on 2008-08-29
I'm pretty sure you can allocate more space in Ubuntu once your in there.

---

### Post by Gabt on 2008-08-29
Care to share?

---

### Post by ac1d6urn on 2008-08-30
> **Gabt said:**
> Ok, LVPM didnt work. It then failed to mount the root device, i managed to put thing back to the way they were tho. Seems im going to have to keep using the virtual disks and keep my windows installation, how do i go about making this virtual disk bigger?

[Try the following (from Wubi Guide):]("https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?")

[INDENT]Download [wubi-add-virtual-disk]("https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=wubi-add-virtual-disk"), open a terminal and run: 

sudo sh wubi-add-virtual-disk /home 15000

Where the first argument is the directory to move to a new dedicated disk, and the second argument is the size in MB. 

The 2 directories you are most likely to migrate are /home (if you have a lot of user data) and /usr (if you installed a lot of software). 

You should now reboot. If you are happy with the result, you can now remove /home.backup. To undo the changes remove /home, copy rename /home.backup to /home and remove the /home line in /etc/fstab.[/INDENT]

Since you need more space for software, try moving /usr (instead of /home) to a new 15-30 gig virtual disk.

---

### Post by Gabt on 2008-08-30
That just broke my install :/

---

### Post by ac1d6urn on 2008-08-30
> **Gabt said:**
> That just broke my install :/

What error message are you getting?

---

### Post by Gabt on 2008-08-30
Couldnt log in. Said sumthing about my /home folder being ignored and i didnt have permissions, i booted failsafe xterm, and took ownersship over the dir needed., managed to pass THAT error, then was hit with another. Just reinstalled.
Not trying anything else, thanks anyway.

---

