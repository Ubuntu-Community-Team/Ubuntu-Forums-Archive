---
title: "USB Harddrive versus USB keyboard."
date: 2020-12-19
forum: Hardware
---

### Post by dabrovnijk on 2020-12-19
I have a USB harddrive that mounts when booting except when I have a USB keyboard connected, if I disconnect the keyboard the drive mounts as usual.

I don't understand why and what can I do to make sure that the USB harddrive is connected even if I have the keyboard (or any other USB devices attached)

This is normally not a problem as I use the computer as a headless ubuntu server, but if I connect usb devices to the computer I would like to be sure that the hardrive is mounted  after a reboot.

---

### Post by Autodave on 2020-12-19
This could possibly be a hardware problem like a power supply.  Can you try a powered USB hub for at least a couple of the USB items?  If the powered hub fixes your problem, then that would mean that your power supply's 5V line is either weak or overloaded.

---

### Post by ajgreeny on 2020-12-19
What do you get as output if both are attached and you run command ***lsusb***?
After that attach each without the other to see if there is a device clash, ie, both trying to use the same usb device number.  I'm not even sure that is a possible situation but I'm just *grasping at straws* here.

---

### Post by dabrovnijk on 2020-12-19
(I am sorry for that I was quite frustrated this morning and did not really investigated anything.)

It seems that the internalhardrive and the USB harddrive shifts places with each other /dev/sda <-> /dev/sdb depending on if I have or do not have the usb keyboard connected

Mounting with uuid solved the problem so I changed fstab. 

#/dev/sda1      /mnt/sharedrive ext4    defaults        0       0
/dev/disk/by-uuid/b8c405a1-02aa-4849-af6a-2e7136eb1d5b      /mnt/sharedrive ext4    defaults        0       0

I assume that it is normal. 



[FONT=Calibri]**Without USB keyboard**
[/FONT]
**[FONT=Calibri]$ mount[/FONT]**
[FONT=Calibri]/dev/sdb2 on /boottype ext4 (rw,relatime)[/FONT]
[FONT=Calibri]/dev/sdb1 on/boot/efi type vfat(rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)[/FONT]
[FONT=Calibri]/dev/sda1 on/mnt/sharedrive type ext4 (rw,relatime)[/FONT]
[FONT=Calibri]
**$ lsusb**[/FONT]
[FONT=Calibri]Bus 002 Device 002:ID 0bc2:2323 Seagate RSS LLC Expansion+[/FONT]
[FONT=Calibri]Bus 002 Device 001:ID 1d6b:0003 Linux Foundation 3.0 root hub[/FONT]
[FONT=Calibri]Bus 001 Device 001:ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=Calibri]
**With USB keyboard and before reboot**[/FONT]

**[FONT=Calibri]$ mount[/FONT]**
[FONT=Calibri]/dev/sdb2 on /boottype ext4 (rw,relatime)[/FONT]
[FONT=Calibri]/dev/sdb1 on/boot/efi type vfat(rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)[/FONT]
[FONT=Calibri]/dev/sda1 on/mnt/sharedrive type ext4 (rw,relatime)[/FONT]

**[FONT=Calibri]$ lsusb[/FONT]**
[FONT=Calibri]Bus 002 Device 002:ID 0bc2:2323 Seagate RSS LLC Expansion+[/FONT]
[FONT=Calibri]Bus 002 Device 001:ID 1d6b:0003 Linux Foundation 3.0 root hub[/FONT]
[FONT=Calibri]Bus 001 Device 002:ID 413c:2003 Dell Computer Corp. Keyboard[/FONT]
[FONT=Calibri]Bus 001 Device 001:ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]

**[FONT=Calibri]With USB keyboard and after reboot[/FONT]**

**[FONT=Calibri]$ mount[/FONT]**
[FONT=Calibri]/dev/sda2 on /boottype ext4 (rw,relatime)[/FONT]
[FONT=Calibri]/dev/sda1 on/boot/efi type vfat(rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)[/FONT]
[FONT=Calibri]
[/FONT]**[FONT=Calibri]$ lsusb[/FONT]**
[FONT=Calibri]Bus 002 Device 002:ID 0bc2:2323 Seagate RSS LLC Expansion+[/FONT]
[FONT=Calibri]Bus 002 Device 001:ID 1d6b:0003 Linux Foundation 3.0 root hub[/FONT]
[FONT=Calibri]Bus 001 Device 002:ID 413c:2003 Dell Computer Corp. Keyboard[/FONT]
[FONT=Calibri]Bus 001 Device 001:ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]

---

### Post by ajgreeny on 2020-12-20
I am delighted that you figured out a solution to this problem, but it does show why it can be very important to ensure that the /etc/fstab file uses UUIDs and not /dev/ naming for the device in question.

It is a known potential problem when using /dev/ naming that they can change when new devices are attached; UUIDs will always remain constant, normally until the disk is formatted.

---

