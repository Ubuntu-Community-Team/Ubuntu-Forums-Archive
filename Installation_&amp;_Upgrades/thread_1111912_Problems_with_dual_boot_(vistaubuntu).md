---
title: "Problems with dual boot (vista/ubuntu)"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by Shuichiro on 2009-03-31
Hi there, newb here. I partitioned off a section of C:\ and installed ubuntu 8.10 with Vista already installed. When I boot unbuntu and bring up GRUB there isn't a listing for Vista and now I can't get into it. Thanks for any help!

---

### Post by Surkow on 2009-03-31
You can manually add Vista to the Grub bootloader.

The following will open the configuration file:
```
sudo gedit /boot/grub/menu.lst
```

At the bottom of my menu.lst file it shows:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

Replace (hd0,1) with your hard drive and partition number where Vista is installed (0 from hd0,1 is my first hard disk and the 1 tells me Vista is installed on the second partition of that hard disk).

---

### Post by Shuichiro on 2009-03-31
added the new entry - says I do not have the permissions necassary to save the file.

---

### Post by Shuichiro on 2009-03-31
ok I guess I need to open a terminal; how do I get there to input the above?

---

### Post by PetterDK on 2009-03-31
Uhm you should have permission to save that file if you did

sudo gedit /boot/grub/menu.lst

---

### Post by Mark Phelps on 2009-03-31
First, do a "sudo fdisk -lu" (that's a lower-case L, not a one).  This will list your partitions.

If Vista is installed on the first partition, you should see something like:

/dev/sda1 ... HPFS/NTFS

In that case, use (hd0,0) in your menu.lst stanza for Vista

Also, you MUST use "sudo" because ROOT owns the file, not you.  So, you have to edit the files as ROOT.

---

### Post by Shuichiro on 2009-03-31
there is a HPFS/NTFS partition on /dev/sda2

ok, so where do I go from here?

---

### Post by Shuichiro on 2009-03-31
added entry for (hd0,1) and I get "error 13: Invalid or unsupported executable format"

---

### Post by Mark Phelps on 2009-04-01
OK, post the results here of doing "sudo fdisk -lu" (that's a lower-case L, not a one) in a terminal.  Need to look a the layout of your partitions.

---

