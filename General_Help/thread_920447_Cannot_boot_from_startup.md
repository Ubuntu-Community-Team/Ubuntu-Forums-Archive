---
title: "Cannot boot from startup"
date: 2008-09-15
forum: General Help
---

### Post by Dalston on 2008-09-15
Hello as the title suggests I have a problem booting from disk,  I have 8.04 installed which was updated from 7.10 and 7.04.  I am trying to reinstall xp because theres a few apps that dont work well in wine.  My problem is that when I change the bios to boot from disk i dont get the option 'press any key to boot from disk' it just goes right ahead and starts loading Ubuntu.  I have tried 2 different copies of xp that I know 100% work because I tried them on a another system.  I have tried setting the boot devices to boot from disk in the bios to no avail. Sometimes I get the error 'cannot boot from cd error 5' and sometimes it just starts loading the Ubuntu as normal.  Also the original 7.04 Ubuntu disk wont boot either so im thinking its a bios problem of some sort.  It would be great if someone could help me.  If you need more info let me know. Thanks in advance.

---

### Post by anotherdisciple on 2008-09-15
Have you tried using a live cd? See if the windows partition is there and has something in it... then just reinstall grub... it should automatically detect XP.

---

### Post by Dalston on 2008-09-15
At the moment its a Ubuntu only machine, it doesnt have a windows OS on it at all.  And even with the live cd it doesnt Boot from disk.

---

### Post by anotherdisciple on 2008-09-15
ahhh... I misunderstood... but now I get it.

Usually "boot from disk" means boot from hard disk. I would think that the option would be more like "boot from CD-ROM" or "boot from CD Drive"... or are the options "boot from HD", "Boot from Disk"...

I guess if you could list off the options I may be able to better help you.

---

### Post by Dalston on 2008-09-15
Yeah sorry what I meant was boot from cd drive.

---

### Post by anotherdisciple on 2008-09-15
What are the other options though?

---

### Post by Dalston on 2008-09-15
Ok I restart and press f12 then i get the following option:

+Removable
+Hard Disk
+CD Rom
lagacy LAN

I choose cd rom and the disk in the drive starts spinning like it's gonna boot and then...

Grub loading stage 1.5

and then it loads up ubuntu.

---

### Post by anotherdisciple on 2008-09-16
Okay... I have to start asking dumb questions because I don't see what the problem is. So... what does the front of the disk that you are trying to boot from say exactly? Who makes your bios? Dell? HP? etc...

Most of the time you can hit a button and choose what device to boot from, but there is also an option in the bios to choose what devices to boot from, and in what order to try them. Try setting that to boot from cd, then the hard drive.

If I can find out what BIOS you are using that may help me guide you a little better. I don't see why it's not working. Unless if you have a bad cd, or the cd isn't bootable, but you said you have used it on another computer?

---

### Post by Dalston on 2008-09-16
Ok I tried putting the 1st 2nd and 3rd devices to boot from cd and disconnected the hard drives that were not relevent to the install and it worked. Thanks for your help.

---

### Post by anotherdisciple on 2008-09-16
haha... wow.. that was complicated!

---

