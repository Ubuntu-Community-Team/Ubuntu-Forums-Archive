---
title: "External USB HDD suddenly get unmounted"
date: 2013-12-14
forum: Hardware
---

### Post by asafs.sarid on 2013-12-14
I have an WD MyPassport 1TB drive connected.
From time to time it suddenly gets unmounted \ disconnected, I checked the power saving preferences and I did a search for a similar problem over here but nothing helped.
I am running a 13.10 ubuntu.
I guess it's not a general problem because it didn't happen in my windows 7 OS.

I am quite new to ubuntu so let me know if there is some logs that I need to run and post that will help.
Thanks.

---

### Post by frankmorris2 on 2013-12-14
Hello,

I am using the same USB drive on my machine. I have  noticed the same disconnection problem.

However, the problem only occurs  on a USB 3.0 port. When I use an older 2.0 port, the drive says  connected for the whole duration. I have not yet asked google.com about  this issue, but for the moment, this is my workaround.

I am sure Ubuntu gurus on this forum will be able to help us more.

Have a nice day.

---

### Post by tgalati4 on 2013-12-14
Open a terminal:

```
dmesg | tail -50
```

Cut and paste any messages related to the disconnection.  It could be a cable issue--perhaps the cable is not rated for the speed of the port.  It could be an overcurrent issue--not enough power to spin up the drive before the kernel thinks it has died and dismounts it.  Could be a kernel/USB3 module bug.

---

### Post by asafs.sarid on 2013-12-16
Here is what I guess is related to the disconnection, I runned the command right after it got disconnected.
```
[66635.837091] usb 4-2: USB disconnect, device number 2
[66635.882176] usb 4-2: Set SEL for device-initiated U1 failed.
[66635.882182] usb 4-2: Set SEL for device-initiated U2 failed.
[66636.870207] Buffer I/O error on device sdc1, logical block 96385212
[66636.870215] Buffer I/O error on device sdc1, logical block 96385213
[66636.870220] Buffer I/O error on device sdc1, logical block 96385214
[66636.870223] Buffer I/O error on device sdc1, logical block 96385215
[66636.870227] Buffer I/O error on device sdc1, logical block 96385216
[66636.870230] Buffer I/O error on device sdc1, logical block 96385217
[66636.870233] Buffer I/O error on device sdc1, logical block 96385218
[66636.870235] Buffer I/O error on device sdc1, logical block 96385219
[66636.870238] Buffer I/O error on device sdc1, logical block 96385220
[66636.870241] Buffer I/O error on device sdc1, logical block 96385221

```

have no idea what these error means, thanks for the help.

---

### Post by asafs.sarid on 2013-12-20
Anyone that can help in this situation? 
I have noticed that it's mostly happening when the HDD is in high usage such as playing movie from it or downloading files to it.

---

### Post by tfrue on 2013-12-20
asafs.sarid,

I can tell you that it's not good that you are having 'logical error' errors, I would back up your drives just incase something goes wrong. Do you have your computers dual booted with Window's and Linux on the same partition? Also, I would like to see the output from the command ```
sudo fdisk -l
``` Please and thanks!

---

### Post by asafs.sarid on 2013-12-20
Hi Chris, thanks for the reply.
Yes, I am using both windows and linux, but not on the same partition.


Here is the 'sudo fdisk -l' output:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd4bdc600


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       81920    32935935    16427008    7  HPFS/NTFS/exFAT
/dev/sda3        32935936   800303312   383683688+   7  HPFS/NTFS/exFAT
/dev/sda4       800305150   976771071    88232961    5  Extended
/dev/sda5       968587264   976771071     4091904   82  Linux swap / Solaris
/dev/sda6       800305152   968587263    84141056   83  Linux


Partition table entries are not in disk order


Disk /dev/sdc: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00023f15


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953458175   976728064    7  HPFS/NTFS/exFAT

```

and this is a 'lsblk' output that might help:
```

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1   8:1    0  39.2M  0 part 
&#9500;&#9472;sda2   8:2    0  15.7G  0 part 
&#9500;&#9472;sda3   8:3    0 365.9G  0 part /media/asafsari/OS
&#9500;&#9472;sda4   8:4    0     1K  0 part 
&#9500;&#9472;sda5   8:5    0   3.9G  0 part [SWAP]
&#9492;&#9472;sda6   8:6    0  80.2G  0 part /
sdc      8:32   0 931.5G  0 disk 
&#9492;&#9472;sdc1   8:33   0 931.5G  0 part /media/asafsari/My Passport
sr0     11:0    1  1024M  0 rom  


```


Thanks!

---

### Post by tfrue on 2013-12-20
I'm sorry, I meant drive lol. I was getting sleepy!:P  I would back up your drive or at least get the files that you want from the 1TB drive, run a Disk Checking tool on it, and possibly format it. You are getting I/O errors on your WD drive, which is bad, so you need to run software like Gparted or use Window's chkdsk, and let the software scan and repair bad sectors on the drive.

I would try that first and see if that helps, if it doesn't we will continue troubleshooting.

---

### Post by asafs.sarid on 2013-12-20
Ok so the problem is solved..
It actually had nothing to do with ubuntu, it was a bug in the WD MyPassport with usb3.0 ports.
The problem got solved by updating the WD firmware. And by the way, WD software and firmware updates are not supported threw linux, so I had to update it from the windows.

Thanks for helping out!

---

### Post by tfrue on 2013-12-20
No problem! Have a good one!

---

### Post by oldrocker99 on 2013-12-21
I occasionally see 8 (the number of external drives I have) file manager windows open spontaneously on my system, which would indicate that they were unmounted, then mounted. Don't know why, but it does happen once in a while.

---

