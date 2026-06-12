---
title: "Trying to repair Windows harddrive with ubuntu"
date: 2008-12-26
forum: Hardware
---

### Post by sdlyr8 on 2008-12-26
Okay. Dad's (Windows XP) computer crashed and I'm working on trying to fix it with my ubuntu Live CD. I've narrowed it down to the harddrive's boot sector and a few other blocks have been corrupted. 

The harddrive is not showing under Computer and when I try to mount it, I get...
> ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sda /media/windows/ -o umask=0000
Error reading bootsector: Input/output error
Failed to mount '/dev/sda': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.


When I try to do 'sudo fdisk -lu /dev/sda' I get nothing. 

I've tried badblocks and got a list of 22 numbers, I'm guessing they are the blocks that are corrupted? 

Not to sure what to do from here. Anyone have any suggestions? Thanks in advance!

---

### Post by vanadium on 2008-12-26
The error message is very clear on what to do. It is an ntfs system and you really need an MS Windows system to reliably repair it.

---

### Post by caljohnsmith on 2008-12-26
Do you have your Windows Install CD? I would begin by booting that, going to the "recovery console" and running:
```
fixboot
chkdsk /r
```
And run the chkdsk command as many times as it takes until it reports no errors. Then try to mount the partition again in Ubuntu and let me know if it works, or what errors you get.

---

### Post by khelben1979 on 2008-12-26
IF you ever get the system up and running again I would suggest that you get [the SpinRite program]("http://www.grc.com/spinrite.htm") (if you can afford it).

It seems like a very reliable program for fixing bad harddrives.

---

### Post by cariboo on 2008-12-26
You could also go the hard drive manufacturers web site and download the diagnostic tools and check to see if the hard drive is repairable. You may have a bad hard drive and the diagnostic tools will tell you whether it is good or bad.

Jim

---

