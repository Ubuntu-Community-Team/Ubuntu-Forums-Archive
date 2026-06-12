---
title: "My Harddrive Partition Will Not Mount - HELP!"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by Gamzarme on 2007-12-30
Hello. I need help.

I have Ubuntu 7.10.
I cannot mount my Ubuntu partition after I changed both it and it's SWAP partition with gParted on a Linux Boot Tools CD. I gives me an error when attempting to mount in the Ubuntu Live CD:
> wrong fs type, bad option, bad superblock on /dev/sda2,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so
I do not know what to do. It seems as if it's corrupted, but can it be fixed through a recovery Linux CD? On gParted it closed out of the program whilst checking the partition.
The GRUB bootloader is now throwing an error and refusing to load. I have Windows dual booted, but that's inaccessable without restoring either GRUB or the Windows boot loader via the Windows XP CD. I didn't want to try any restoration of bootloaders until I was sure it wouldn't mess up my partitions.

Is there no hope for my situation? All I need to do is mount the partition and copy off my files under "/home/thomasp".

Right now I'm running under the Ubuntu 7.10 Live CD. I'll be happy to provide any more information about the situation on my end. I've included a screenshot.
Anything...anything at all...

-Patrick

---

### Post by taurus on 2007-12-30
When you changed partitions table around with gparted, you also change the UUID of those partitions so I bet that is the problem.  Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
That is a lower case letter L.

---

### Post by Gamzarme on 2007-12-30
Thank you *so* much for replying! =)
Here is the output you asked for:
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001f311

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14589   117186111    7  HPFS/NTFS
/dev/sda2   *       14590       60672   370161697+  83  Linux
/dev/sda3           60673       60801     1036192+   5  Extended
/dev/sda5           60673       60801     1036161   82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1           4      128394    0  Empty
/dev/sdd2               5        2432    78011640    b  W95 FAT32
If you would like, I can also trying booting again to give you the error number that GRUB is reporting, if it would help you understand what is happening, although you seen to have a great understanding of what is going on. In detail, what also I did was have a dual booted computer (Ubuntu & Windows) and install Ubuntu 7.04, then create a new partition using gParted and temporarily put all of my /home/thomasp/* files on that partition (copy/paste from within 7.04) and then use gParted to delete the old partition and the SWAP and extended and leave the temporary partition. Then I reinstalled Ubuntu 7.10 on the old unallocated space left from the 7.04 installation and remounted the temporary partition in 7.10 and copy/pasted my files back into /home/thomasp/. I then went back into gParted and deleted the temporary partition and expanded Ubuntu's partition to fill the rest of the hard drive, that which was not being used for Windows. I then used gParted to shrink the new 7.10 SWAP space to 1 GB, instead of ~5.8 GB, this seems to perhaps have caused a problem.
I don't know why it is reporting 80 GB total, it should be the full 500 GB for my hard drive.

I do hope it helps you! Thank you again for your reply!

-Patrick

---

### Post by taurus on 2007-12-30
Run these commands on a terminal from the LiveCD.

```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda2 /media/ubuntu
```
Now, post the output of these commands.

```
sudo cat /media/ubuntu/boot/grub/menu.lst
cat /media/ubuntu/etc/fstab
```

---

### Post by Gamzarme on 2007-12-30
Here is the output from attempting to mount my Ubuntu partition into /media/ubuntu:
> mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
Apparently there is a bad superblock? Can this be repaired or gotten around by reinstalling GRUB, perhaps?

I do not think I'll be able to run the second set of commands until I can mount sda2...

Should I be more clear as to the process I took for partitioning?
Thanks for your replies.

-Patrick

---

### Post by taurus on 2007-12-30
Can you fire up gparted in System -> Administration and have it display the partitions of the first harddrive, /dev/sda.  Post the screenshot of that then.

---

### Post by Gamzarme on 2007-12-30
Here is the screenshot. I notice it isn't showing the total/used space of sda2. That isn't good...is it..?

I've also included the error message that came along with the Details of sda2.

---

### Post by taurus on 2007-12-30
I guess you must have done something to /dev/sda2 when you used gparted to move your partitions around.

---

### Post by Gamzarme on 2007-12-30
Are the errors that it is reporting significant? I know I let it operate for two and a half hours whilst it moved my data "to the right". There should not have been a power interruption because it was in the same state when I found it in the morning, the app was shut down but the Live OS was up. Is there anything I can do to recover my data, or perhaps a CD that will allow me to mount or restore a partition? Or simulate ex3?
Thank you for your help.

-Patrick

---

### Post by murmel on 2007-12-30
Have you installed nfs-common? (sudo apt-get install nfs-common)
Edit: Maybe has nothing to do with it. But when I'm mounting stuff from another linux-computer I need this or else I get the same error you got. Worth a try!

---

### Post by taurus on 2007-12-30
Try

```
sudo mount /dev/sda2 /media/ubuntu
```

---

### Post by Gamzarme on 2007-12-30
Murmel, I have installed nfs-common on my Ubuntu partition (sda2) before I made the partition changes. However, I haven't attempted to install it on the temporary Live CD that I am running now, I assume that it is already installed.

I have also uploaded the gParted error report generated from me attempting to check sda2 for errors. It says something like the ex3 filing system is gone and the ex2 is in it's place.

I've just installed "nfs-common", It still does not mount. Thanks for the replies.

-Patrick

---

### Post by Gamzarme on 2007-12-30
> **taurus said:**
> Try

```
sudo mount /dev/sda2 /media/ubuntu
```

I tried that in the terminal and got this:
```
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
So it failed to mount sda2 because of a bad superblock. Do you know if a superblock can be repaired?

I've uploaded a screenshot. Thank you for the help.

-Patrick

---

### Post by murmel on 2007-12-30
How it looks in my fstab:
```
# mount /home on mserver
mserver:/home   /mnt/mserver    nfs     rsize=8192,wsize=8192,timeo=14,intr 0 0
```

Maybe doesn't help at all? 
mserver is the hostname of my server and I mount it's /home onto my /mnt/mserver

---

### Post by Gamzarme on 2007-12-30
> **murmel said:**
> How it looks in my fstab:
```
# mount /home on mserver
mserver:/home   /mnt/mserver    nfs     rsize=8192,wsize=8192,timeo=14,intr 0 0
```

Maybe doesn't help at all? 
mserver is the hostname of my server and I mount it's /home onto my /mnt/mserver

I have a similar setup, except it mounts a server. But this is another problem as I know I didn't change any of the references to mounting sda2 in the fstab file, I am sure I left know completely alone.
Thanks for the help.

-Patrick

---

### Post by Gamzarme on 2007-12-30
I have [discovered something]("http://www.cgsecurity.org/wiki/TestDisk") that may prove quite useful for recovering superblocks, so it says. If it does, wow. It looks rather promising, too. What do you think?

-Patrick

---

### Post by murmel on 2007-12-30
Have you tried adding this to /etc/fstab (sudo nano /etc/fstab) 
```
UUID=xxxx-xxxx-xxxx-xxxx /path/to/mount               ext3    defaults,errors=remount-ro 0       0
```
Your UUID can be found [here](http://ubuntuforums.org/attachment.php?attachmentid=54712&d=1199042776).
Then:
```
sudo mount -a
```

---

### Post by Gamzarme on 2007-12-30
I cannot get to my fstab file because it is located in my sda2 partition, the one that I cannot access. The picture that I uploaded of gParted shows that sda2 is not reporting space total/used, like my Windows partition is (NFTS?).
Thanks.

-Patrick

---

### Post by murmel on 2007-12-30
Ah, damn. Then I have no idea what to do... :S Try the software you posted! =)

---

