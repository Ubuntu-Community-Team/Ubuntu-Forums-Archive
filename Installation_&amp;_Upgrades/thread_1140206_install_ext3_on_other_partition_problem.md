---
title: "install ext3 on other partition problem"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by donpedrodos on 2009-04-27
I have one partition wich is running Ubuntu 8.10 with reiserfs.
On another partition, test partition, i normaly run a test system of new releases of ubuntu.

The final release is out, so i try to install on the test partition Ubuntu 9.04 but with file system ext3.

The bootloader that i use is grub, and in the menu list i adjust the UUID for the newly updated partition.

When i now try to boot into the 9.04 Ubuntu parition, i get an error.

ERROR 2 BAD FILE OR DIRECTORY TYPE.

I installed 9.04, but now using reiserfs, and correcting in the menu list the UUID and al works fine.

So what am i missing here.
A partition ext3 next to a partition reiserfs does not work.
A partition reiserfs next to a partition reiserfs does work.

---

### Post by cariboo on 2009-04-27
Did you mark the partition to be formatted as ext3?

---

### Post by donpedrodos on 2009-04-28
I did some installing deleting reformating, but so far without any luck.

This is what i tried:
[LIST=1]
[*]Started Gparted 0.4.3.2 Live CD, formatted partition to EXT3
[*]Installed Ubuntu 9.04 and during installation formated again to EXT3 and gave the root /
[*]Started Gparted 0.4.3.2 Live CD, deleted partition and then format to EXT3
[*]Installed Ubuntu 9.04 and during installation formated again to EXT3 and gave the root /
[*]Started Gparted 0.4.3.2 Live CD, deleted partition and then format to EXT3
[*]Installed Ubuntu 9.04 and during installation did not formated again to EXT3, but only gave the root /
[/LIST]

After installation, checked in my normal Ubuntu 8.10 if partition was OK.
I could access drive and after edit the menu & fstab with the correct UUID of disk, automount inside Ubuntu 8.10 works OK.

But with the grubloader selecting via the boot startup menu, still this ERROR 2 fault.

I think the problem is GRUB, this one is already installed from the release of Ubuntu 6.10 or so.
But how to correct this, i mean, how i update this grub bootloader.

Is there a way to check what grubloader version is installed?

---

### Post by donpedrodos on 2009-04-29
Looks like there is not realy an explenation why this does not work a partition reiserfs next to a partition ext3.

I went back to the thing that works, a reiserfs partition next to a reiserfs partition.

If anyone has a thought about what goes wrong, i am still interested.

---

