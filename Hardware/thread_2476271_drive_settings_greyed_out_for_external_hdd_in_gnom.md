---
title: "drive settings greyed out for external hdd in gnome disks"
date: 2022-06-21
forum: Hardware
---

### Post by marsdenf on 2022-06-21
Using Xubuntu 20.04 on a desktop and a laptop.  When I plug in the western digital my passport 4 tb portable external hdd, and then go to gnome-disks-utility ("disks"), 
and click on "drive options"  (three vertical dots on upper right of window) ,  the following are greyed out:  "smart data and self tests", "drive settings", "standby now"
and "wake up from standby".  How to make these options available for use?

---

### Post by TheFu on 2022-06-23
If you've checked that the BIOS has SMART enabled and it still doesn't work, know that some USB connections don't support SMART. There's nothing you can do to use gnome-disks.

You can, however, try to use **smartctl**, which will allow specifying different types of disk controllers. There is an auto-discovery mode to figure out which control should be specified for all the other test and reporting commands.  Again, if SMART isn't enabled in the motherboard BIOS, this won't work either.

For my backup disks, I have to use the **-d sat** option with some USB disks. Most are ata or scsi.  There are other choices, like usbjmicron or megaraid. The manpage has a list.

---

