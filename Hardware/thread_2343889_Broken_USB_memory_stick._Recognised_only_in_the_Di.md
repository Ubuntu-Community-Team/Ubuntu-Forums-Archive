---
title: "Broken USB memory stick. Recognised only in the Disks utility. (im new to linux)"
date: 2016-11-20
forum: Hardware
---

### Post by ed.g.ar on 2016-11-20
Hello! Just got Ubuntu to dualboot with my windows 10, and dont know much of how Linux works. Tryed to find solution for my problem on youtube and google, but with no luck.




So iv encountered a problem. I was using Windows 10 and the power went out while i was transfering files in the usb. tryed to do all the commands in Windows to fix it, but nothing worked.

In windows it was recognised as an unusable partition with 0b space.

In linux, 
it shows up in **disks** and the light on the usb stick is glowing. size is: "-" , Device is: "/dev/sdb" , contents are: "-"

but in gparted utility app it does not show up.

Also when clicking on gears for the USB stick, in disks utility, it only shows EDIT MOUNT OPTIONS


I dont care about the data on the usb stick. I just wanted it to work.


If its not possible, and it should go to the bin, please say so.

---

### Post by ed.g.ar on 2016-11-20
when i mess in the terminal, i managed to get this message.

Device size reported to be zero.  Invalid partition specified, or
    partition table wasn't reread after running fdisk, due to
    a modified partition being busy and in use.  You may need to reboot
    to re-read your partition table.

also when i write sudo mount /dev/sdb  - it comes out as 
mount: mount point /mnt/usb-GENERIC_USB_Mass_Storage_001D0F0CAA76F980B59D09D5-0:0 does not exist

----
wrote more commands that i dont know what they do, 
 sudo mkdir /media/usb
ubuntu@ubuntu:~$ sudo mount -t vfat /dev/sdb1 /media/usb
mount: special device /dev/sdb1 does not exist
ubuntu@ubuntu:~$ sudo mount -t vfat /dev/sdb /media/usb
mount: /dev/sdb: **can't read superblock**

---

### Post by sudodus on 2016-11-20
I think you can restore this drive to something useful with ***mkusb***.

- You can wipe the first megabyte and after that use gparted to create a new partition table, or you can let mkusb do the whole job via one of the alternatives in the wipe menu.

- But the main task of mkusb is to create a boot USB drive from an iso file with a linux distro.

See these links and links from them for more details,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

