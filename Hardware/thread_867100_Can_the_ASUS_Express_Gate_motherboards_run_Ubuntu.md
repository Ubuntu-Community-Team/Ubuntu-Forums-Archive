---
title: "Can the ASUS Express Gate motherboards run Ubuntu?"
date: 2008-07-22
forum: Hardware
---

### Post by metalf8801 on 2008-07-22
Is anyone using a Asus motherboard with Express Gate powered by Splashtop?  If you are using a ASUS motherboard with Express Gate and you tried to install another Ubuntu can you tell me which modal you are using and weather or not it worked? 

Thank you 
Dan

---

### Post by reformedgeek on 2008-07-22
Can't see it being a problem.  The Splashtop software is built into ROM.  Booting from an Ubuntu CD will still allow you to install the OS onto a hard drive or USB drive.

---

### Post by Forrest319 on 2008-07-26
> **reformedgeek said:**
> Can't see it being a problem.  The Splashtop software is built into ROM.  Booting from an Ubuntu CD will still allow you to install the OS onto a hard drive or USB drive.

I just go at P5Q mobo and Express Gate installs via an .exe and the Driver DVD.  The manual recommends that you install Express Gate on you C Volume.  I've been trying to find someone running only Linux who has got it working.

---

### Post by n8boyce on 2008-09-06
I have the express gate working on my P5Q-e motherboard running Ubuntu 8.04.1
The only downside is I have the leave the usb plugged in all the time.

I used the grub script from this site to install the image on a usb flash drive.
[http://www.phoronix.com/forums/showthread.php?t=11653](http://www.phoronix.com/forums/showthread.php?t=11653)

TIPS
Find the image file on the asus disk that cam with the mb
find /media/cdrom/  -name *.IMG -print

Disable hal while running the script
sudo /etc/init.d/hal stop

Find the usb flash drive
sudo fdisk -l

I set the BIOS to recognize USB storage devices as a hard drive. (not sure if this was needed)

Grub stage one and stage two locations
/boot/grub/stage1 
/boot/grub/stage2 


ISSUES
After booting into express gate clicking the power down button appears to sync the usb and saves my settings but doesn't poweroff the box. I end up having to physical push the power button to shutdown.

---

### Post by ktechman on 2008-12-05
Is there a how-to for installing express-gate or is someone working on one?

             Thank you for your reply Ktechman

---

### Post by cpdavngr on 2008-12-10
On a side note, has anyone tried installing Express Gate using WINE?

---

### Post by Rudedawg on 2009-02-03
I'm trying to set up a dual hard drive dual boot 64bit system. My MB has express gate and I'm getting some weird error after I select something form the ubuntu cd menu.

---

### Post by devolnx on 2009-02-11
Just thought I would point out this thread as I have just got Express Gate working on a ASUS P5Q / 9500GT system.

Hope it helps. [http://ubuntuforums.org/showthread.php?t=1049170](http://ubuntuforums.org/showthread.php?t=1049170)

---

### Post by indianolajohn on 2009-04-16
They put the source code on the asus site

Description Express Gate Source code V1.4.6.2 or earlier versions.  
 
 
 
 File Size  280.24 (MBytes) 2009/03/27 update  
 
 
 
 Download from   Global China

---

