---
title: "External Hard Drive refuses to Mount"
date: 2010-07-14
forum: Hardware
---

### Post by bezukhova on 2010-07-14
Hello! i know there are many threads already about external hard drive mounting problems, and I've gone through many of them and followed the advice but none of it seems to be helping.

I was using Karmic and both my externals were mounting fine automatically, however, yesterday, i backed up all my files and installed Lucid from scratch off a CD (please don't ask why i didn't just upgrade... there were reasons but it's complicated and not really relevant i don't think). anyway, one of my externals (Western Digital MyPassport) is mounting FINE but the other one (Western Digital Elements) is not. as i said, i've been through the forums looking for a solution, tried rebooting and trying the same commands again, no joy. was wondering if anyone could help? thanks in advance!

here is what comes up in my terminal when i try mount the drive.

```
starla@Anna:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/elements
[sudo] password for starla: 
Error reading $MFT: Input/output error
Failed to load $MFT: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
starla@Anna:~$
```

---

### Post by YesWeCan on 2010-07-14
A longish shot, but not without good reason. Uninstall dmraid and then try mounting it.

---

### Post by bezukhova on 2010-07-14
turns out dmraid isn't actually installed to start with

---

### Post by YesWeCan on 2010-07-14
What's the output of sudo fdisk -l?

---

### Post by bezukhova on 2010-07-14
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002357f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18663   149903360   83  Linux
/dev/sda2           18663       19458     6384641    5  Extended
/dev/sda5           18663       19458     6384640   82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aa0f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976761560    7  HPFS/NTFS
```

---

### Post by YesWeCan on 2010-07-14
It is device sdc now. Before it was sdb?

---

### Post by bezukhova on 2010-07-14
yes, that appears to be the case. i did notice that - not sure why. i did have the other external hard drive connected in between but i don't see why that would affect it.

---

### Post by YesWeCan on 2010-07-14
Obviously it is vital to mount the correct drive.:) Can you connect both externals and do fdisk -l and then try the mount command again for the 1TB device and check it still fails?

Otherwise I don't know. I suggest finding out if the drive can be mounted by any other computer or OS at all. It strikes me as very odd that the WD Passport mounts ok but the WD Elements doesn't. What are the differences between them?

---

### Post by bezukhova on 2010-07-14
this link
[URL="http://www.wdc.com/en/products/index.asp?cat=9"]
http://www.wdc.com/en/products/index.asp?cat=9[/URL]

shows a few differences, beyond what's on there i'm not sure without digging out the paperwork that came with them - and i've had the My Passport a while so i'm not sure where that is. i have the My Passport Essential 250gb and the Elements 1tb.

both plugged in at once:

```
starla@Anna:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002357f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18663   149903360   83  Linux
/dev/sda2           18663       19458     6384641    5  Extended
/dev/sda5           18663       19458     6384640   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aa0f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976761560    7  HPFS/NTFS

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    c  W95 FAT32 (LBA)
```

---

### Post by YesWeCan on 2010-07-14
This sounds similar: [http://gparted-forum.surf4.info/viewtopic.php?id=14099](http://gparted-forum.surf4.info/viewtopic.php?id=14099)
Aside from trying the HD on another system to isolate the fault I have no more ideas. Good luck.

---

### Post by IcarusR on 2010-07-14
If you have access to a windows pc you could try running 'chkdsk /f /r' on it.
Or if you have a windows cd you could boot from that & use recovery console to run chkdsk.

If neither above are available then you could use manufacturers tools to check the disk. There are a lot of these on Hirens Boot CD.

[http://www.hirensbootcd.net/download.html?ver=10.6]("http://www.hirensbootcd.net/download.html?ver=10.6")

---

### Post by bezukhova on 2010-07-14
thanks for the help guys. a friend of mine is going to let me try it on his windows desktop and/or macbook tomorrow... i've also been trying to get my laptop to boot into Karmic (from a CD) to see if it still works in that (ie to check if it's just a glitch in my Lucid install), but that's not working for some reason.going to get some sleep and try those things in the morning, i'll update if anything works so hopefully if anyone else has the same problem they can avoid some of the hassle.

---

### Post by bezukhova on 2010-07-15
chkdsk doesn't actually seem to do anything. like, it doesn't even check the disk. the program just closes itself. going to try figure out how to use command lines in Windows, but as i don't use Windows AT ALL i'm a bit clueless.

---

### Post by bezukhova on 2010-07-15
ok - so i tried EVERYTHING on the thread, EVERYTHING on similar threads i could find, some of it multiple times, eventually chkdsk /f /r worked. would have tried it sooner but i didn't have access to a windows machine right away.

it took hours to run the program, but all my data (as far as i can tell, haven't checked every file) is still there. it's currently copying to another hard drive, once i know it's safe i can figure out whether the drive will mount on my ubuntu machine and if not, i can safely reformat. if anyone has a similar problem, i'd recommend getting access to a windows machine and running chkdsk. life saver.

---

### Post by YesWeCan on 2010-07-15
Hurray! :)

---

