---
title: "Disk ID changes for every reboot (sda becomes sde)"
date: 2010-06-13
forum: Hardware
---

### Post by thelxinoe on 2010-06-13
So I have a small server that runs Ubuntu 10.04 from a IDE disk connected to a Asus A8N motherboard, with 4 disks connected to the SATA ports for storage. 
At first there wasn't a problem, installed ubuntu on the IDE disk, added the other disks (sata disk 1 to 4, sdb to sde) as /media/DiskX/

Then I had to move the server, turned it on again, now suddenly things have changed, because sata disk 1 went from sdb to sda, while the IDE disk went from sda to sde. So I changed things around, thinking it was probably because ubuntu numbers the SATA as the first ones. 

But now I had to do another reboot, and the IDE disk suddenly is sdc, turning more havoc on my poor fstab. 

Is there a reason for this happening, I thought the /dev/sdX numbering scheme was supposed to stay that was unless I moved disks around?

This is becoming more and more annoying, because programs that looks for files on /media/Disk02/stuff can't find it because the disk that was mounted as Disk02 had changed.

---

### Post by arrange on 2010-06-13
The */dev/sdxx* labelling is unreliable, use UUID instead.
For examples see
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by quadproc on 2010-06-13
> **thelxinoe said:**
> ...
Is there a reason for this happening, I thought the /dev/sdX numbering scheme was supposed to stay that was unless I moved disks around?

As arrange has stated, the sdX designators cannot be depended upon because they are assigned by the operating system at startup time.  That problem is exactly why UUIDs were implemented.

These days, with systems often having removable storage devices such as flash drives or external disks, it is very common for sdX identifiers to change at any time.  Fortunately, fstab allows the use of UUIDs.  Here is a line from mine:
> UUID=e61d892a-0341-4f99-a87b-c9345d9f9eb1 /home        ext3    relatime,errors=remount-ro    0    2
quadproc

---

### Post by Morbius1 on 2010-06-13
Or LABEL's.

You can get a list of all those identifiers by issuing the following command:
```
sudo blkid -c /dev/null
```You'll get an output that looks something like this:
>  
/dev/sda1: LABEL="WinXP" UUID="DA9056C19056A3B3" TYPE="ntfs" 
/dev/sda6: LABEL="COMMON" UUID="C4DB-C1B0" TYPE="vfat" 
/dev/sdb6: LABEL="Data" UUID="f7927995-b098-42be-ada0-987857f5177a" TYPE="ext3" So for that "Data" partition you can specify any of the following in fstab:
> /dev/sdb6 /DATA           ext3     defaults        0       2
UUID=f7927995-b098-42be-ada0-987857f5177a /DATA           ext3    defaults 0       2
LABEL=Data /DATA           ext3    defaults        0       2

---

