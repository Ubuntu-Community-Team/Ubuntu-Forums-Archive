---
title: "[SOLVED] mayday. root passwd required for hdd test"
date: 2008-10-16
forum: General Help
---

### Post by PeterVR on 2008-10-16
Ubuntu crashed.
I had no response on mouse or keyboard for several hours after which I had no alternative but press the reset button. Yeah, I know.

Upon reboot, an error was found on hda1, so the computer went in maintenance mode, requiring the root passwd in order to scan and recover the harddisk. And since I forgot the root password (always using sudo cmd) that's as far as I can get.

Pressing ctrl-alt-del gives an option to open a root shell. Unfortunately, the file system is mounted readonly and can't be umounted, so I can't erase the x after the root line in the /var/passwd file. I also can't access the file system in WinXP (this is a dual boot system).

Any suggestions anyone?

Thanks
PVR

---

### Post by aysiu on 2008-10-16
Use a live CD and run *fsck* on the drive. I forget the actual command, but I believe it involves *fsck*

---

### Post by theevilhamster on 2008-10-16
im pretty sure its ```
fsck /dev/[drive]
```.

---

### Post by jocko on 2008-10-16
Try this from a live cd (assuming the file system is ext3):```
sudo e2fsck -fpC 0 /dev/[COLOR=Red]x[/COLOR]da[COLOR=Red]Y[/COLOR]
```(change "[COLOR=Red]x[/COLOR]da[COLOR=Red]Y[/COLOR]" to whichever device node your drive has)

---

### Post by PeterVR on 2008-10-16
OK thanks folks.

What I did is use the live CD to erase the :x: in the root line in /etc/passwd. Then rebooted and didn't need to enter a password in order to advance (which is where I got stuck previously).
Well - I thought the system was going to run a disk check automatically; turns out it just gave me a root shell (with some errors btw).

So I checked on the corrupt file system - which was ext2 and not ext3 so I didn't enter the e2fsck command, but fsck. Approved of all suggested solutions and rebooted again. Happily using Linux again now.

Thanks again, just wondering if I also could have used the e2fsck command on a ext2 partition, and if so: what better would it have done? 

Cheers
PVR

---

### Post by geirha on 2008-10-16
fsck will figure out which type of filesystem it is, and run e2fsck if it is ext2 or ext3. So the result would've been the same in other words :)

---

### Post by jocko on 2008-10-17
> **PeterVR said:**
> OK thanks folks.

What I did is use the live CD to erase the :x: in the root line in /etc/passwd. Then rebooted and didn't need to enter a password in order to advance (which is where I got stuck previously).
Well - I thought the system was going to run a disk check automatically; turns out it just gave me a root shell (with some errors btw).

So I checked on the corrupt file system - which was ext2 and not ext3 so I didn't enter the e2fsck command, but fsck. Approved of all suggested solutions and rebooted again. Happily using Linux again now.

Thanks again, just wondering if I also could have used the e2fsck command on a ext2 partition, and if so: what better would it have done? 

Cheers
PVR
e2fsck is for both ext3 and ext2, fsck is just a wrapper for the file system specific fsckers, which tries to determine which file system you use and run the proper program to check it. So there would be no difference between running e2fsck directly or from fsck.

---

