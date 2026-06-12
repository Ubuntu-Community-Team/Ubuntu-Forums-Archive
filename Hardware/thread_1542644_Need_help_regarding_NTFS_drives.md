---
title: "Need help regarding NTFS drives"
date: 2010-07-30
forum: Hardware
---

### Post by Toastados on 2010-07-30
Hi,

I'm pretty new to ubuntu and linux in general. I'm building a home file server running xubuntu 9.10 (I had some difficulty getting the 10.04 versions of both ubuntu server edition and xubuntu to work, but that's another story) and have slowly got most things up and running.

I have xubuntu running off an 80GB sata drive and that is working fine. However I'm having trouble locating my secondary 1TB NTFS drive. It shows in bios but doesn't show in Places or on Gparted. Also NTFS configuration tools in >>System has greyed out the "enable write support for internal devices". I've read through a handful of different threads but nothing has seemed to help.



One of the threads I read mentioned posting what shows in the terminal upon entering

sudo fdisk -1
 
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


Any advice would be much appreciated.

---

### Post by heyandy889 on 2010-07-30
I came across a wonderful program called lshw-gtk. It gives you a graphical list of the hardware on your computer. 

[quote=undecim]
```
sudo apt-get install lshw-gtk
```Once lshw-gtk is installed, press Alt+F2 and paste this command
```
gksu lshw-gtk
```Also, remember that you can copy and paste the    information from a terminal straight into your post rather than    retyping them. Just highlight the text you want to copy with your   mouse,  then you can either right-click and choose "copy", or if you are   more  of a keyboard person, press Ctrl+Shift+C (Ctrl+C doesn't work   because  the terminal uses it for other things). You can then paste the   text  you've copied into your post with the right-click menu or Ctrl+V.
[/quote]
I found the answer on this thread [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475). The part I quoted is from the first post under "Hardware Information."

---

### Post by Toastados on 2010-07-30
Thanks for the reply.

That's a pretty handy program. I installed it but I'm still having no luck seeing the drive in question. There are 3 IDE interfaces showing, one is bold. I'm not sure if they relate to the actual drives in the machine though, as I only have 2 drives plugged in.

It's strange, as I thought that the more recent versions of ubuntu would automount NTFS drives. I'm 100% certain that the drive is not faulty, as it's recognised by the bios and works fine in my windows machine.

Any ideas?

---

### Post by Toastados on 2010-07-31
*bump*

---

### Post by jerenept on 2010-07-31
sudo fdisk -l
thats a common "L"

---

### Post by Toastados on 2010-07-31
:oops: Whoops. I haven't felt like such a noob in a long, long time. 

I'm at work at the moment, I'll post the results after I get home in a couple of hours.

---

### Post by Toastados on 2010-07-31
Here's the result of sudo fdisk -l


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ebb7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9367    75240396   83  Linux
/dev/sda2            9368        9729     2907765    5  Extended
/dev/sda5            9368        9729     2907733+  82  Linux swap / Solaris


I've also run testdisk and that too is only showing the 80GB drive the OS is on.


Edit:

I've been able to get fdisk to recognise the drive. After 3 attempts at shutting down and reconnecting the sata cable and psu connector, it finally found it. Weird.

Edit:

NTFS configuration tools found the new HDD automatically. Sorted :)  Would be interesting to find out why it didn't show up after the initial connection.

---

