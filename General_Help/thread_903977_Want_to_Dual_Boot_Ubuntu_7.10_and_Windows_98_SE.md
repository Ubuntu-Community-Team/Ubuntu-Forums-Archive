---
title: "Want to Dual Boot Ubuntu 7.10 and Windows 98 SE"
date: 2008-08-28
forum: General Help
---

### Post by muboger on 2008-08-28
After installing Ubuntu 7.10 it worked well - immediately.  But rebooting did not give an option to run Win 98SE.  Restored MBR with FDISK, but then had no option to select Ubuntu.  Is there a way to dual boot Win 98 and Ubuntu?  Thanks!

---

### Post by falcon61102 on 2008-08-28
When you restored Win98's MBR you overwrote the GRUB.  The simplest way to get back to where you want to be would be to download the Super Grub Disk:
[www.supergrubdisk.org](www.supergrubdisk.org)

Using that you should be able to reinstall the GRUB and configure it to boot both systems.

The other option would be to boot from the Ubuntu LiveCD and reinstall the GRUB there, then manually edit your menu.lst to show Win98 in the startup menu.

Either option should work for you.  If you need help with either way, post here.

---

### Post by muboger on 2008-08-29
I'll try it this weekend.  Thank you for replying!

---

