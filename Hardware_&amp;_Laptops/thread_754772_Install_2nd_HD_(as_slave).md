---
title: "Install 2nd HD (as slave)"
date: 2008-04-14
forum: Hardware &amp; Laptops
---

### Post by HanZZZO on 2008-04-14
In my PC (with only Ubuntu 7.10) I did installed a second HD.
With the start up of my PC, the 2nd HD is recognized as Slave of the Master.
But Ubuntu 7.10 did not see the HD

How to install this second HD further?

---

### Post by jespdj on 2008-04-14
How do you know that Ubuntu doesn't see the HD?

You need to partition and format a new harddisk before you can use it. Use a program like Gparted to do this.

---

### Post by HanZZZO on 2008-04-14
No Result
I do not see the 2nd HD (80 Gb)

---

### Post by fela on 2008-04-14
run ```
ls /dev
``` in a terminal (apps > accessories > terminal), making sure the only storage devices in/plugged into the machine are the two hdds. If there's a hdb or a sdb in the output, it must be 'recognizing' the harddisk.

---

### Post by az on 2008-04-14
sudo lshw -C disk -short

(that will LiSt HardWare, looking only at disks and give the summary)

---

### Post by HanZZZO on 2008-04-14
hans@ubuntu-desktop:~$ sudo lshw -C disk -short
[sudo] password for hans:
H/W path               Device      Class       Description
==========================================================
/0/100/1f.1/0.0.0      /dev/sda    disk        74GB MAXTOR 6L080J4
/0/100/1f.1/0.1.0      /dev/cdrom  disk        DVD DC DW1670
/0/100/1f.1/0.1.0/0    /dev/cdrom  disk        
hans@ubuntu-desktop:~$ 


Also I do not see the other HD :(

---

### Post by az on 2008-04-14
> **HanZZZO said:**
> 
With the start up of my PC, the 2nd HD is recognized as Slave of the Master.


Are you sure?  Because lshw is telling you that there is no device there.

Some BIOSes require you to rescan, update or autodetect the drives when you add a new drive.

---

### Post by HanZZZO on 2008-04-14
hans@ubuntu-desktop:~$ sudo lshw -C disk -short
[sudo] password for hans:
H/W path               Device      Class       Description
==========================================================
/0/100/1f.1/0.0.0      /dev/sda    disk        74GB MAXTOR 6L080J4
/0/100/1f.1/0          /dev/sdb    disk        74GB MAXTOR 6L080J4
/0/100/1f.1/1          /dev/cdrom  disk        DVD DC DW1670
hans@ubuntu-desktop:~$ 

I controlled the connections again and now I'm happy to see 2 HD's

On the desktop, menu, Locations/Computer I see als the drive (E:)

I had to mount the drive now

???

---

### Post by HanZZZO on 2008-04-15
Solved

---

