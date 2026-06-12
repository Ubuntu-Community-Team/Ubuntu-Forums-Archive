---
title: "Second Hard Drive Causes Boot Issue"
date: 2006-07-26
forum: Hardware &amp; Laptops
---

### Post by pclogic on 2006-07-26
I just got done installing a second hard drive in my Ubuntu server 2.6.15-23-server.  I ran the command "[FONT="System"]sudo /sbin/mkfs.ext3 -m 0 -j /dev/hdb1[/FONT]" to format the lone partition on that drive as type ext3.  When I boot starting with my server completely shut down, it boots correctly.  However, when I reboot using the command "[FONT="System"]sudo shutdown -r now[/FONT]" or start up after using the command "[FONT="System"]sudo shutdown -hP now[/FONT]", the boot freezes directly after the BIOS loading ends and before GRUB should begin.  Here are my config files:

file: /boot/grub/device.map
[FONT="System"](fd0)   /dev/fd0
(hd0)   /dev/hda
(hd1)   /dev/hdb
[/FONT]

command: df -ahT
[FONT="System"]Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hda1     ext3     36G  789M   34G   3% /
proc          proc       0     0     0   -  /proc
/sys         sysfs       0     0     0   -  /sys
varrun       tmpfs    125M   60K  125M   1% /var/run
varlock      tmpfs    125M  4.0K  125M   1% /var/lock
procbususb   usbfs       0     0     0   -  /proc/bus/usb
udev         tmpfs    125M   84K  125M   1% /dev
devpts      devpts       0     0     0   -  /dev/pts
devshm       tmpfs    125M     0  125M   0% /dev/shm
/dev/hdb1     ext3     19G  129M   19G   1% /data1
[/FONT]

file: /etc/fstab[FONT="System"]
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb1       /data1          ext3    defaults        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0[/FONT]

I have tried commenting out the /etc/fstab entry for hdb1.  I have also tried booting with just the entry for hda in /boot/grub/device.map.  Any help as to what might be going on here would be appreciated.

Thanks,
Jason

---

