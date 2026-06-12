---
title: "Mounting usb drive problem"
date: 2008-09-07
forum: General Help
---

### Post by aero528 on 2008-09-07
Hey, guys.  I'm pretty new to Ubuntu and linux in general.  I just installed Ubuntu 8.04 on my laptop.  Works like a charm except one issue.  The only thing that is really bothering me is the fact that when I plug my usb stick in(formatted in windows with fat), it won't mount it.  I'v searched around some, but haven't found a real answer that works for me.  Is ubuntu this evolved, but still unable to mount FAT windows usb drives?  My laptop is an Ibm X31, so it has no optical drive, and usb is really the only easy way for me to transfer data from my windows desktop/windows school computers to my ubuntu laptop.  Any other ideas for help?  Thanks for whatever you can throw at me!

---

### Post by Washer on 2008-09-07
what error does it give?

---

### Post by aero528 on 2008-09-07
It says this...

"Cannot mount volume.

Invalid mount option when attempting to mount the volume 'SAVAIANOS'."

SAVAIANOS is the name I gave to my flash drive in windows.  Any ideas?

---

### Post by Washer on 2008-09-07
I'm not really a filesystem person... Maybe transfer out your stuff & try formatting it in gparted? Luckily it's being recognized.

---

### Post by crhis on 2008-09-07
Can you access this usb drive in windows

---

### Post by aero528 on 2008-09-07
Yes, I can use it in windows just fine.  I really want to use it to transfer files from my windows desktop to my ubuntu laptop, so formating in gparted wouldn't work in windows would it?

---

### Post by aero528 on 2008-09-07
Nevermind, I got it working.  I typed in mount -t vfat /dev/sdb1 /mnt/usb.  that worked.  I ended up reading one of the help files I found on mounting.  I still don't know how to automount it.  Do I have to modify fstab?  Thanks for the time input, guys, and I hope this helps someone else.  I just coulden't find where( I was typing in sda1, not sdb1).  Is there any way I can easily know where it is for next time I have this kind of problem?

---

### Post by Washer on 2008-09-08
yeah, you find it in gparted, or in the System->administration->system monitor->file systems

I still think it's easiest to format it in gparted. I'm sure it can do the various fats, which will also work in windows

---

