---
title: "&quot;fstab&quot; file editing"
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by doctorbrowder on 2007-09-05
I'm trying to install the scanner driver for a Brother DCP-130C. I got as far as Step 9 in the instructions given in this Howto posting <http://ubuntuforums.org/showthread.php?t=462498&highlight=Brother+dcp-130C>. When I attempt the command

echo 'none /proc/bus/usb usbfs auto,devmode=0666 0 0' >> /etc/fstab

it comes back with "permission denied". Does anybody know how to get around this? Thanx!

---

### Post by agemon on 2007-09-05
only root has write permissions on fstab. So, to add the line, simply type `sudo` (no quotes) before the comand. eg:
sudo echo 'none /proc/bus/usb usbfs auto,devmode=0666 0 0' >> /etc/fstab

or, you could just type `sudo nano /etc/fstab` (or `sudo gedit /etc/nano`, if you prefer GUIs) and edit it from there but ALWAYS MAKE A BACKUP BEFORE EDITING

PS: you'll also have to type sudo before `mount` and `umount`, generally speaking, if a program show an error like 'permission denied' or, 'need root privileges', you have to run it as root (using sudo of course)

---

### Post by geraldm on 2007-09-05
permissions:
It is a bad practice to set a scanner's permissions to "0666" as other's permissions become rw.
Some scanners risk damage when driven beyond their effective length of scan.
It is much better to use other's permissions = 0 (no access) and change the group to
"scanner" or any group where those who use the scanner are restricted to permitted users.

Gerald

---

