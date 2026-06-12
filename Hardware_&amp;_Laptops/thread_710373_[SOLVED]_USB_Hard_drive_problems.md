---
title: "[SOLVED] USB Hard drive problems"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by nowhere@cox.net on 2008-02-28
I am having troubles with a FreeAgentPro external hard drive.  The machine it's connected to is a dual boot XP/Gutsy machine and the file system on the USB drive is NTFS.  I am intermittently losing connection to only certain (and seemingly random) directories on the file system. So far I have noted a directory full of videos, one full of music and my Azureus downloads folder.  

The system had been up and running a couple days with no problems as far as I can tell. I don't know if all directories are available. I remotely mounted the music folder to PVR via sshfs and worked fine for several hours before going to bed. This morning the wife calls and cannot listen to music because the PVR cannot read the files. I ssh into the host systems where the USB drive is physically connected and can read the drive fine, open files, write to it etc EXCEPT I cannot see the music folder.

On the PVR I umounted the sshfs mount. Still can't see the music folder on the host system. Also I cannot umount the USB drive since it says it is in use. I am not certain this time but I think even rebooting doesnt fix the problem. I have to reboot, pause at the grub menu, power cycle the drive then continue boot to clear the problem. I can power cycle it with the system up (and have) but it causes corruptions of the filesystem which so far fsck has been able to fix without data loss.

Anyone have any suggestions? NTFS support flakey?

Thanks,
Eric

---

### Post by chochem on 2008-02-29
It's not much but just to say that I've used an external 500Gb HD formatted to NTFS with my ubuntu install for three or four months with no issues at all. I suppose 'they' wouldn't have included NTFS read/write in Gutsy if it wasn't fairly stable. At least I hope so.

---

### Post by Yellow Pasque on 2008-02-29
I would boot into Windows and run scandisk/defrag

---

### Post by nowhere@cox.net on 2008-03-10
I will try to scan/defrag.  One other interesting note is that this version of HDD is the one with e-SATA included. I quit using e-SATA because it had this kind of issue CONSTANTLY in windows and Linux. I assumed my MB's e-sata was not stable. I am now suspecting there is something wrong with the drive but I am afraid that Seagate won't support it. Their docs claim that if their diagnostic software reports no errors that they will not RMA it. 

I may try anyway after scanning it. 

Thanks for the info so far.

Eric

---

### Post by nowhere@cox.net on 2008-03-12
Ok scanning in Vista found nothing. I did not defrag but if someone thinks this will make a difference I will.

The symptom is that random folders become inaccessible while the rest of the drive is accessible. It happened again yesterday but I was able to vnc to the server, umount and remount and it was accessible again. Sometimes the drive will be permanently flagged as busy so I cannot even umount it. 

Do you think the drive is defective? e-SATA was almost unusable since it wouldn't stay connected at all and would corrupt the filesystem every time it failed. 

Eric

---

### Post by nowhere@cox.net on 2008-05-20
Solved. See [http://ubuntuforums.org/showthread.php?t=757284](http://ubuntuforums.org/showthread.php?t=757284)

---

