---
title: "Ubuntu is unable to mount external hard drive though it could in Live session"
date: 2010-02-09
forum: Hardware
---

### Post by suleydaman on 2010-02-09
Hello, I am a new user in ubuntu and linux, in fact, I only installed ubuntu today:p. My windows crashed so I used an openSUSE gnome live CD(I was trying to decide between ubuntu and openSUSE) and copied all of my files from my hard drive to an external one. I had never used the hard drive before, the first time I used it was in the openSUSE live session. I was able to copy all my files successfully and was able to navigate it easily in both ubuntu and openSUSE. When I installed ubuntu today, I can see the hard drive, but I can only navigate it for a while, when an error message comes up telling me that it is "unable to mount the external hard drive" and I can no longer see the hard drive.

This is what I get for sudo fdisk -l

> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae24ae24

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38398   308431903+  83  Linux
/dev/sda2           38399       38913     4136737+   5  Extended
/dev/sda5           38399       38913     4136706   82  Linux swap / Solaris

Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeefa5d9b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1      121602   976759808    7  HPFS/NTFS


And this is what I get for sudo lsusb:

> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 009: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 003 Device 004: ID 04f3:0212 Elan Microelectronics Corp. Laser Mouse
Bus 003 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I think that Jmicron Technology thing may be the hard drive.

Please help, I have been reading so many forums but all the people who post have slightly different circumstance from me and I don't know what to change in the commands. I am a real noob, and this hard drive problem is killing me. Thank you very much.

---

### Post by no2498 on 2010-02-09
did you use the whole disk to install
was the drive plugged in ?
im only asking as i can not help you
but you can try unmounting it first then unplugging it an restarting the computer
plug it in did it mount ?
hope that helps some

---

### Post by hxcobd on 2010-02-09
Any problems I've had with external drives in recent linux distros have had really strange, mind-numbingly easy solutions.

For example, on this install, I tried for hours to figure out why my USB external wouldn't mount or show up... All I had to do was unmount when logged in as root, reboot, log in my regular user account, and it mounted just fine.

Try some simple stuff. Reboots, unplug/plug in, unmount as root, etc.

---

### Post by suleydaman on 2010-02-09
I think the problem may have occurred because i didn't unmount the hard drive. I looked around the panels for the Linux equivalent of "safely remove USB" and couldn't find it so I just unplugged it thinking l didn't have to worry about that with Linux. Is that bad?

I can tell it is mounted becuase it appears when I type sudo fdisk -l , but when I try this 

> suleyman@Home-desktop:~$ sudo -i
root@Home-desktop:~# umount /mnt/usb/
umount: /mnt/usb/: not found

So it can't unmount, but I can see it when I do the sudo fdisk command.
Also, the hard drive says it is in /dev/sdg1 but that doesn't exists and aren't they usually /dev/sda , or at least that was the case for most of the forum threads I have checked out.

---

### Post by ivanvajar on 2010-02-09
Allways unmount drive by right-clicking on the drive's desktop icon and then 'unmount volume'.


Restart your machine with drive plugged-in. If that doesn't work, we'll fix it another way.

---

### Post by suleydaman on 2010-02-10
I have tried that just now, it still doesn't work. What seems to be happening is that the external hard drive is in the directory like /dev/sdg1 or /dev/sdf1, but as soon after a moment of going into the folder, it gives me the error and the files (sdg1 or sdf1) dissappear. The external hard drive will only come back if I unplug it from USB port, plug it in again and restart. But it will do the same thing again, ie. I am allowed to access it for a while before it crashes.

I also forgot to mention that it wasn't plugged in when I installed therefore Ubuntu is not installed on it

---

