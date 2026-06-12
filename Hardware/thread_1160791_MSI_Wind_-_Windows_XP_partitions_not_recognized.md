---
title: "MSI Wind - Windows XP partitions not recognized"
date: 2009-05-16
forum: Hardware
---

### Post by sophia42 on 2009-05-16
I'm trying to create a dual-boot MSI Wind netbook - first by pulling the original 80GB drive and then installing a 160GB (Fujitsu) drive.  Using Clonezilla, I can clone the three partitions from the original drive back onto the 160GB drive, resulting in a bootable Windows system - a hidden FAT32 Windows restore partition; the main C: OS_Install partition (ca. 32 GB) and a D: 40GB partition.
I've then tried installing Ubuntu 9.04 net-remix several different ways, with the same result: the grub bootloader doesn't see the Windows partitions and I can't get it to go to a bootable partition, despite many edits of /boot/grub/menu.lst following directions and tips in the forums.
The Ubuntu partitioner doesn't recognize the Windows partitions as ntsf partitions for some reason - perhaps because the original set-up uses a GUID partition map that fdisk doesn't play nicely with?
After manually creating an ext3 partition from  the available drive space, if I then use the installer, it will recognize that there are several operating systems on the machine, including the Windows partitions.  When i choose the option to install Ubuntu in the remaining partition, so that i will be able to use the systems side by side - i.e., choose which OS to boot into at start-up - again, i end up with a grub menu that doesn't include a Windows partition, much less anything I can point to to boot the Windows OS.
There seems to be a preference for keeping the manufacturer's original restore (FAT) partition, and I'd prefer not to install Windows afresh, given the drivers and multiple programs already installed and working on the original 80GB disk.
Any solutions?  Thanks in advance for any help and advice.

---

### Post by sophia42 on 2009-05-18
I can tell you what doesn't work ...
It doesn't work to try to create a recovery disk on a bootable USB drive - in order to use a MS MBR repair utility after the Ubuntu install writes a new bootloader, etc.  At least, not in any way that I've been able to discover, including MSI Wind's "Burn Recovery CD" nor dd through a command line on a Macintosh.
It may be that Super Grub Disk (<http://www.supergrubdisk.org/>) would work - but in the meantime, I'm trying out wubi (installing Ubuntu within Windows - ??) to see how that works.  I gotta believe that there's a hit on performance - and so far, the install is _much_ slower than a direct one (nearly 3 hours estimated vs. a few minutes) - but we'll see.
If anyone has any other suggestions, I'd be happy to try them!  Thanks -

---

### Post by sophia42 on 2009-05-18
And Wubi runs into a dead-end as well - everything seems to go just fine: I assigned the Ubuntu installation to a new Windows partition ... but upon reboot, after "checking installation," and after partitioner started up - error message: no root file system detected (endless loop - shut down).

No good help found in the forums (so far).  I tried using UNetbootin Super Grub Disk to see about repairing the GRUB - no luck.

Back to square one ...

---

### Post by sophia42 on 2009-06-08
and ... nothing else seemed to work either.
Whatever specific way MSI sets up its disk to hold a hidden recovery partition along with the two windows partitions (C: and D: ) seems to be simply incompatible with the standard ways Ubuntu 9.04 writes a partition table.  And despite a very long time searching through both Ubuntu and MSI forums, I've not seen anything that suggests a fix - at least those I tried did not work.

So ... a clean install of Windows XP Pro is underway; I'm assured that once a basic and standard Windows installation is in place, Ubuntu 9.04 will install nicely thereafter.  Keeping my fingers crossed ...

---

