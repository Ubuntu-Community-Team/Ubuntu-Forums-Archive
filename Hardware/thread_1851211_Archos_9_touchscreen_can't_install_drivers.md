---
title: "Archos 9 touchscreen can't install drivers"
date: 2011-09-27
forum: Hardware
---

### Post by emptiness on 2011-09-27
I've been following this guide for 11.04:
 [http://www.archoslounge.net/forum/entry.php?b=244](http://www.archoslounge.net/forum/entry.php?b=244) 
and this guide for 10.04:
[http://www.ossramblings.com/installing-ubuntu-archos-9-tablet#comment-1028](http://www.ossramblings.com/installing-ubuntu-archos-9-tablet#comment-1028)

I've been able to successfully get everything running except for the touchscreen. Every time I run the setup utility this is what I get:

(*) Linux driver installer for eGalaxTouch controller 

(I) Check user permission: root, you are the supervisor.
(I) Begin to setup the eGalaxTouch driver.
(I) Extract eGalaxTouch driver archive to /usr/local/eGalaxTouch32.
(I) Create eGalaxTouch utility shortcut in /usr/bin.
(I) Create TKCal tool shortcut in /usr/bin.
(I) Check X window version: 1.7.x
(I) Copy X module: x17/egalax_drv.so to /usr/lib/xorg/modules/input.

(Q) Which interface controller do you use?
(I) [1] RS232 [2] PS/2 [3] USB : 2
(I) Using interface: PS/2

(I) Configure PS/2 aux driver.
(I) Removed eGalaxTouch driver archive from /usr/local/eGalaxTouch32.
(I) Removed eGalaxTouch utility shortcut.
(I) Removed TKCal tool shortcut.
(I) Removed X module.
(E) No PS2 mouse driver found.

Any help would be appreciated, I've been trying for a couple of days now.

---

### Post by Mehdiing on 2011-10-11
I've the same problem, do you have found a solution?

---

### Post by Jose E on 2011-12-31
Add i8042.nomux to line GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub

---

### Post by n3wb1439 on 2012-03-30
I have dealt with this for days and finally came up  with a fix.  just choose 3 to configure fore usb.  The mouse mod is found and all the files are copied correctly... except change the line:
Option "Device" "/dev/serio_raw0" instead of Option "Device" "usbauto"
in your /etc/rc.local. Reboot.

---

### Post by Mehdiing on 2012-05-07
.

---

### Post by ghannibal on 2012-08-31
I have the same problem with last eGalaxTouch driver. I resolved it with download the same version describe in guide : eGalaxTouch-3.01.4001-32b-k26

---

