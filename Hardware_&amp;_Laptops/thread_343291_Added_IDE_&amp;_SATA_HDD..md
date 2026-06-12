---
title: "Added IDE &amp; SATA HDD."
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by rudied on 2007-01-21
Hi ,

I have installed Ubuntu 6.0.6 LTS on a new 300G IDE HDD. Everything is going great. 

I now want to add 2 other HDD (1 200G SATA = DATA, 1 80G IDE = Win2K & WinXP).If I disconnect the UBUNTU I can use Win2K and WinXP. I need them for testing.

I have set the win (80G) IDE drive as Primary Master, the Ubuntu (300G) IDE as Primary slave and added the (200G) SATA drive. I have also setup my bios to boot from Primary Slave.

When I boot it boots but fails where it tries to mount hda1.

I have now booted with the LiveCD to access the enternet.

hda = 80G IDE
hda1 = Win2k
hda5 = WinXP

hdb = 300G IDE
hdb1 = Ubuntu
hdc = DVD-RAM

SATA ???

It now boots to Grub, I then tried to select different settings but as soon as it tries to mount the Ubuntu it fails.

Any help please ?

Thanks in advance

---

### Post by rudied on 2007-01-22
Just a update :

I can now boot from my HDD again.=D> 

I still have the same configuration as above, I have just disabled my SATA controler. 

The root is still (hd0,0),but I just changed the mount after that to hdb1 instead of hda1.

If i enable my SATA it does not boot. Will try again.

---

### Post by dexter on 2007-01-22
> **rudied said:**
> 
hdb = 300G IDE
hdb1 = Ubuntu
hdc = DVD-RAM

SATA ???

sata disk should show up as sda, sdb, ...

---

### Post by rudied on 2007-02-04
The problem is that as soon as I enable my SATA controller in the bios, Ubuntu does not start.

---

### Post by rudied on 2008-04-10
Just a Update.

The work around is to remove GRUB. Then all is OK.

---

