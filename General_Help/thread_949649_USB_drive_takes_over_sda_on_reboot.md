---
title: "USB drive takes over sda on reboot"
date: 2008-10-16
forum: General Help
---

### Post by Redline21 on 2008-10-16
I have an external USB hard drive (NTFS) attached, which is listed as sdd. If I reboot my server, the USB drive switches to sda, which obviously messes up what was sda. Is there a way to control this or force the USB drive to always go to sdd or to load after my hard drives? I am running 8.04 server.

---

### Post by logos34 on 2008-10-16
Make sure you are using UUIDs in /boot/grub/menu.lst (->'kernel' line) and /etc/fstab.  Also, change the mount point to something like /media/usbdrive

---

### Post by Redline21 on 2008-10-17
Yes, it appear to be...menu.lst has "root=UUID=..." and fstab has two entries for "UUID=...". However I have no idea what this means or what bearing it has on anything. Can you please explain?

My mount point is /media/usbfiche (the USB drive contains micro-fiche files).

---

### Post by jerome1232 on 2008-10-17
It means your mount points shouldn't get messed up, the uuid's always point the correct partition regardless of device flip flops.

(ie sda flips to sdb, the uuid's will still point to the correct spot)

As long as you use uuid's it doesn't matter if your drive switches every boot. 

Many bios's will put usb drive's before regular internal hard drives so that if it happens to be bootable, it will tried before the internal hard drives. This is why it becomes sda.

---

