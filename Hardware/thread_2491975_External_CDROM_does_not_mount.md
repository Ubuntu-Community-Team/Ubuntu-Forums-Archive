---
title: "External CDROM does not mount"
date: 2023-10-26
forum: Hardware
---

### Post by jeffbarish2 on 2023-10-26
I have a USB CDROM drive connected to a Raspberry Pi 4 running Ubuntu 23.10. No device gets created for it (/dev/sr0, /dev/cdrom, /dev/dvd). lsusb displays information about the drive. Likewise, lshw -C disk displays information about the drive, but the first line says "UNCLAIMED". dmesg has information about the drive too, but there is also a message "Power-on or device reset occurred". Same thing when I try a CDROM drive from a different manufacturer. When I run Raspberry Pi OS instead on the same hardware, the CDROM drives mount without issue.

---

### Post by jeffbarish2 on 2023-10-31
I can load the module for the cdrom manually, but it does not get used.

I am also finding that the sound card in my system does not work. There are dtbo files in /boot/firmware/overlays, so it seems as if some developer intended for Ubuntu to support the sound card. I tried adding [FONT=monospace][COLOR=#000000]dtoverlay=hifiberry-dacplus to /boot/[/COLOR][/FONT][FONT=monospace][COLOR=#000000]config-6.5.0-1006-raspi [/COLOR][/FONT](even though I am not supposed to edit the file). It had no effect. It also had no effect to add a config.txt file to /boot with the same line. There must be a configuration file that needs to be modified to enable these devices.

---

### Post by ra3wilson on 2023-11-19
New to Linux and Ubuntu Studio 22.04 LTS, and I've got the same problem here with my USB CDROM.  [FONT=courier new]blkid[/FONT] command lists it as "Bus 001 Device 005: ID 0e8d:1887 MediaTek Inc. Slim Portable DVD Writer".  Likewise,[FONT=courier new] lshw -C disk command[/FONT] shows "[FONT=courier new]logical name: /dev/cdrom"[/FONT]  and  "[FONT=courier new]logical name: /dev/sr0" [/FONT].  I'm dual-booting with Windows10, and the drive has worked flawlessly for 6 years.  But in Ubuntu, I can't get it to show in Dolphin or in System Settings (Removable devices), and I can't get any applications to acknowledge it's there.

I've tried plugging it straight into the single USB-A port on the side of the laptop, and also into a USB-C hub (where it has worked for 6 years in Windows).  Ubuntu recognizes, mounts and uses a Seagate 4TB USB drive plugged into the same USB-C hub in the adjacent port.  Dolphin automatically shows the Seagate drive.

Following a thread on another forum, I managed to create a /media/cdrom/ folder in root, but it's empty and I don't remember the command I used.  There is no  /dev/cdrom/  folder.  I've tried numerous reboots with audio CDs and data discs in the drive, and nothing works.  Any help would be appreciated.

-Randy

---

### Post by ra3wilson on 2023-11-22
Resolved?  The problem *~may have~* been one of the disks I was trying to mount was a CD-RW or CD-R that had not been "closed" properly, although the same disc read fine in Win10.  Or the problem may have been in the drive.  Nonetheless, while trying to sort it out, the drive started not latching when I closed it.  In Win the drive would read if I physically held the tray closed with my fingers, but as soon as I let go it would pop open.  I bought a new drive ($19), plugged it in, put the same CD in and Ubuntu still didn't read the files on the disc, but immediately asked if I wanted to *write* files to the disc.  I tried another audio CD, and voila', system read the disc and now is working just fine thank you.  Next, a commercial CD (app install) read fine.  All good now and leery of the next mystery to solve.
-R

---

