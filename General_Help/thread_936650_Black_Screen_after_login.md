---
title: "Black Screen after login"
date: 2008-10-03
forum: General Help
---

### Post by bri764 on 2008-10-03
I just installed Ubuntu Studio on my computer and everything seemed to go fine.  Everything loaded fine until after the login in screen.  Then it just went to a plain black screen with nothing but a mouse cursor.  It even played the startup music as it loaded this.  Any ideas as to what the problem is?

---

### Post by brucenduane on 2008-10-03
I had a similar problem with Ubuntu 8.04.1 which is the base for UbuntuStudio.

How I solved my problem of no background and right click menu.

I did 16 installations of Ubuntu 8.04.1 and Ubuntu Studio over the last two week.

I rebooted 5-6 times.  Sometimes this fixed the problem.  Gnome did not like something -- I never found out what.

The UUID value can be found by 
$ sudo blkid

I checked that /boot/grub/menu.lst was had the correct UUIDs
$ gksudo gedit /boot/grub/menu.lst

I checked that all the partitions had the correct UUIDs in fstab
$ gksudo gedit /etc/fstab

I checked that all the mount points existed in /media directory
$ ls -l /media/

If these are all correct, it usually worked after 2 reboots.

Sorry there are no specifics here, it seemed like magic to get it working.

I made all the changes to my system from a running Ubuntu 7.10 system because all my systems were on portable USB drives.  I mounted the USB drives into my running 7.10 system to make the changes.

-bruce.

---

