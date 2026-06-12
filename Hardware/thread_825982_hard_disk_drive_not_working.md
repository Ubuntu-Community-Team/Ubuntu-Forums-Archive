---
title: "hard disk drive not working"
date: 2008-06-11
forum: Hardware
---

### Post by mike_pasara on 2008-06-11
Hi there.

I'm having an issua with my external hard drive not reading very fast.

I formatted my western digital in fat 32 a few weeks ago for my ps3. I haven't been able to reach usb 2.0 speeds in over a week now. It takes forever to transfer files.

So I pulled the drive out of the external to the desktop computer so i can plug it in and transfer the files form 1 hard drive to the other. Now i've noticed the computer read that the drive is there, it also has power too. 

Ubuntu or xp will not read the drive though. they recognize it's there but not letting me access it... jumpers are in the proper position and everything. I'm out of ideas. Anyone?

PS. the drive is ide not sata

---

### Post by mike_pasara on 2008-06-11
I thought i would add that I just put the drive back into the enclosure and it does not want to read any more. When I go to device manager in vista it allows me to see it as a 2.0 device but when I try to populate the volume it says "Volume information for this disk cannot be found." In the General tab it claims the device is working properly

---

### Post by mike_pasara on 2008-06-13
anyone have any ideas at all?? it's taking forever to transfer everything over usb 1.1 i still have 100gigs of movies.

---

### Post by Odrodzona-Sarmacja on 2008-06-15
use "gparted" (linux) or/and "partition magic" (windows) to check it

then run in terminal
-sudo blkid (shows all your partitions)
and
-mount (shows all your mounted partitions with additional info about them)
to check if harddrive is being mounted correctly
-gksudo mousepad(or other text editor) /etc/fstab
to fix any issues detected with blkid/mount earlier
-sudo mount -a (to mount harddrives specified in fstab)
(sudo umount <mount point>, if you need to remove something
sudo mkdir /media/<dirname> if you need to create some dir for mount point)

Good luck!

---

### Post by mike_pasara on 2008-06-18
I don't have ubuntu installed right now, i am always between windows and linux. could i do this stuff with live cd?

> **Odrodzona-Sarmacja said:**
> use "gparted" (linux) or/and "partition magic" (windows) to check it

then run in terminal
-sudo blkid (shows all your partitions)
and
-mount (shows all your mounted partitions with additional info about them)
to check if harddrive is being mounted correctly
-gksudo mousepad(or other text editor) /etc/fstab
to fix any issues detected with blkid/mount earlier
-sudo mount -a (to mount harddrives specified in fstab)
(sudo umount <mount point>, if you need to remove something
sudo mkdir /media/<dirname> if you need to create some dir for mount point)

Good luck!

---

### Post by Odrodzona-Sarmacja on 2008-06-21
In livecd you can check if Ubuntu would detect this device with "blkid" typed in terminal, which you should access from its program menu. If Ubuntu is capable of detecting that device it should be in list, but if it is not... then maybe it is damaged. If it is in list, then I guess at least on Ubuntu (installed on hd) you could try to mount it like I wrote before.

---

