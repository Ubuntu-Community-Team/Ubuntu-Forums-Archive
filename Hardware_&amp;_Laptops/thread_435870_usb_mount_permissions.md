---
title: "usb mount permissions"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by WilliamKB on 2007-05-07
I have an external 100gig drive that I have been using for about 6 months. It came preformatted 'fat32' and everything worked fine, except the file size limit 'fat32' has.

So I reformatted it to 10gig 'fat32' and the rest 'ext3'.

:( Here's the problem the 'ext32' side always auto mounts with root permission only while the 'fat32' side  has user permissions. I have included some info below:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=93d307b5-9064-464a-892b-af8e55b5db92 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0ad0b564-310e-4598-b623-498347ef9212 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6996    56195338+  83  Linux
/dev/sda2            6997        7296     2409750    5  Extended
/dev/sda5            6997        7296     2409718+  82  Linux swap / Solaris

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10830    86991943+  83  Linux
/dev/sdb2           10831       12161    10691257+   b  W95 FAT32

I mount and unmount this drive all the time so I need it to mount with user permissions on both partitions. I appreciate any help.

---

### Post by WilliamKB on 2007-05-07
bump

---

### Post by Claus7 on 2007-05-08
What we want to do :
We want to partition an external USB Hard Disk Drive (HDD) and be able to read and write data to it. In case this is not a new one (you already have written data to it) have in mind that the process that follows will destroy them.

If we buy such a disk we can have three cases:
1)the disk to be totally unformatted
2)to be formatted with FAT32 
3)to be formatted with NTFS

The second case, even though is very "comfortable" to Linux users, because they can read and write without any worries about permissions and compatibility issues, yet it has some drawbacks:
i) it is not safe format 
ii)you cannot write data more than 2 or 4 GB (for example video files).

The third case enables the Linux users to read data, yet they cannot write data to the disk, so this case is useful only if you have a Windows machine, you copy your files to the external HDD
and you want to read them from your Linux machine. Of course there exists ntfs-3g,which enables Linux users to read and write to such disks, yet I do not know how well that works. 
As far as the first case is concerned you obviously have to format the disk in order to use it.
 
Of course any disk of the above cases can be formatted accordingly so as to cover every user's needs.
One should pay attention to the buffer that a disk has (the more the better) and of course to the size
of the disk. The buffer, simply put, is a memory which helps the transfer of data. 
Pay attention to the size cause :
i) if 1 KB is 1000KB or 1024KB (1024=2**10)
2) no matter how you calculate the size, a part of it won't be usable.

In order to format the disk you have to plug it to the computer first and become root.
Close any windows that might appear and use the command:
```
 df -h
```
With this command you will see the mounted devices in your computer.

In order to partition the disk you have to unmount it. 
```
umount /dev/sda
```

In order to unmount the correct volume have in mind that the usb devices look like this: sda(number), if you type df -h.
Take extreme care on this, because if you type for example hda1 instead of sda1 then you will format your internal hard disk! 

[For the sda1 : serial disk, first usb port, partition 1,
if you have three partitions in that disk then the third partition will look like sda3.
Probably if the disk is new you won't find any partition and you will see the disk as sda. Unmount all the partitions in order to repartition your disk.]

First of all for the partition to take effect you have to create the partitions and then to format the disk.
For example my disk is 300GB and I wanted 200GB for ext3(Linux read only), 80 for FAT32(read by every system)
and 10 for NTFS. With 
```
fdisk /dev/sda
```
manualy you create the number of partitions you want and the size they will have (have in mind that the numbers
you will insert will be in the diad system, for example if you want 1GB, type +1024M). Try to have 2 or at least up to four partitions. If you want more, then some of them will be extended ones.
While you have typed the fdisk command if you type h you will find helpful information about the creation of partitions.

Now you can create the partitions. For my case:
1) ```
mkfs.ext3 -j dev/sda1 -L name of your partition up to 11 characters
```

2) ```
mkfs.vfat -F 32 -n name of your partition up to 11 characters dev/sda2
```

For the ntfs partition you have to use a windows machine.

Up to now we have partitioned the disk. YET you are still not able to write to the first partition (or if you prefer the extended one), unless you are root. In other words you cannot drug and drop items. This is because Linux systems are used also for security reasons.
In that case there are a couple of solutions. The first one is the following:

i) become root
ii) cd /media/name of ext3 partition
iii) mkdir (name of folders you want to create)
iv) chown your user name your user name* (for example if your user name is myname then type chown myname myname*)
v) chgrp your user name your user name* (as above)

With iv and v you say that I want the user(owner and group) to have permissions to all the files(that's the * for)  that you created as root.

Doing this you will be able to drug and drop to the folders you have created anything. Of course you will be able to
create new folders as well. The drawback with this solution is that you cannot use the ext3 in another computer with
different id number and gr number. The default for both is 1000. Type
```
id
```
in order to see your own.

The other one is to type:
```
sudo chown (user name) /media/(name of partition)
```
and you can do anything! I do not know though if you have problems with different computers' id. I suppose not cause that way is like changing the permissions in a file and use it in every computer. 

I have taken this from [http://ubuntuforums.org/showthread.php?t=387644&highlight=external+usb+hdd+write](http://ubuntuforums.org/showthread.php?t=387644&highlight=external+usb+hdd+write)

I hope this helps,
Regards!

---

### Post by WilliamKB on 2007-05-09
Thank you Claus.:cool: 

I haven't been able to return to this problem until now. I will try your ideas this evening and let you know what happens.[-o<

---

### Post by Claus7 on 2007-09-27
Hello,

ok you did what you did. I had left aside the part of formatting the ntfs part from windows. So today I wanted to finish this step as well, and I (after a long time I must admit) booted my dual boot machine from windows. Yet, I was surprised because when I plugged my usb external hdd to my pc I found out that I had a FAT drive and a new local disk. The linux partitions weren't recognised (or mounted if you prefer) at all. I could not see them from windows.

It was very annoying because I already had a local disk which had my linux partition on it and of course wasn't recognised by windows (yet, I could see it). So which drive belonged to which disk?
Or if you prefer :

i)The one disk was my linux partition on my internal hard disk drive.
ii)The other was the unformatted ntfs partition on my externat hdd.

The properties tab isn't very helpful because it recognises those two as raw disks and is doesn't dislpay any valuable information. So which is the way to tell the difference between the two?

Someone must remember the size of the partitions. And from windows we do right click. Then format ... (yes don't worry the procedure won't start immediatly). Then, a new window will open which will inform you with the size of the partition you want to format. Be sure that you have chosen the right one and proceed. Don't format the internal one in my case! 

I have to say that searching the net I came accross a driver that enables windows to read ext2 and ext3. I do not know how these might be helpful and how someone can install them in one's system. This just FYI.
Of course if someone finds out something more practical than this I will be glad to hear.

I hope that this was helpful.
Regards!

---

### Post by farazhussain on 2007-10-01
> **WilliamKB said:**
> bump

Hi,

I did as you wrote with my Seagate Free Agent Go 120 GB.

Here is part of the  output from the 'df' command:

/dev/sdb2             29288240     11600  29276640   1% /media/FHEHDDVFAT
/dev/sdb1             86519648   4767792  77356876   6% /media/FHEHDDEXT3


Here is part of the information displayed by fdisk using "fdisk /dev/sdb" then printing the partition table:

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10943    87899616   83  Linux
/dev/sdb2           10944       14591    29302560   83  Linux


The problem I'm having is this:

I am able to view both the partition of my external hard drive in Linux. I was also able to write to both partitions from Linux. Great!

However, in Windows, the disk is simply not visible !!!! It says that a new device has been installed  etc., but its nowhere to be seen! In the tray it shows an icon and I click it and it gives me the usual, "you can now safely remove" message, but I just can't get it to  show either partition on the external hard drive or the external hard drive itself!

Thanks in advance.

---

### Post by Claus7 on 2007-10-02
Hello,

at first I do not understand your quote. Anyway.
As far as your problem is concerned, and judging from the output of the commands you provide, it is normal that your windows partition cannot see the ubuntu partitions of your external hard drive. Those two file systems are incompatible (as it is implied above). Yet, this might help you :

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Regards!

---

### Post by farazhussain on 2007-10-02
> **Claus7 said:**
> Hello,

at first I do not understand your quote. Anyway.
As far as your problem is concerned, and judging from the output of the commands you provide, it is normal that your windows partition cannot see the ubuntu partitions of your external hard drive. Those two file systems are incompatible (as it is implied above). Yet, this might help you :

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Regards!

Well, I finally figured out what I was doing wrong. 

I did notice that fdisk was showing "Linux" for the 'system' on both my partitions.  That did concern me, but I definitely had used mkfs.ext3 and mkfs.vfat to make the two partitions and I was sure of that. And I confirmed this by using the gparted utility --  indeed it showed the two partitions were ext3 and vfat.

So at least the vfat partition (which was FAT 32), should have been recognized by Windows....

What solved it for me was that when I repeated the process, after creating the vfat partition on my external drive, I also used the fdisk 't'  command which can be used to "change a partition's system id". 

I selected 'b', which stands for "W95 FAT32", and everything worked just fine. 

I now have the entire external hard drive with just the one partition of type VFAT (Windows 95 FAT32) and I'm able to read and write from both Linux and Windows.

Thanks.

Faraz.

PS: Sorry I'm still to learn how to quote others' messages.

---

### Post by Claus7 on 2007-10-03
Hello,

excellent! I didn't expect it to be something like this. It's nice that you were able to solve it. And not only that but also to post what it was wrong. Keep up the good work!

Regards!

---

### Post by Dreamlocked on 2008-03-20
Nice guide.

> **Claus7 said:**
> 
Now you can create the partitions. For my case:
1) ```
mkfs.ext3 -j dev/sda1 -L name of your partition up to 11 characters
```


If you do the previous command without root privileges, you do not have to do the following steps to make it "writable" to the user.
At least, that's what I experienced.

> 
Up to now we have partitioned the disk. YET you are still not able to write to the first partition (or if you prefer the extended one), unless you are root. In other words you cannot drug and drop items. This is because Linux systems are used also for security reasons.
In that case there are a couple of solutions. 

---

