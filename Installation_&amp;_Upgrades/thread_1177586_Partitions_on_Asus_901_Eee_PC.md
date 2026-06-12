---
title: "Partitions on Asus 901 Eee PC"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by moebob24 on 2009-06-03
I have UNR installed on my Asus 901 PC. If anyone is familiar with them, they come with 2 physical partitions. One is Windows XP and the other is used for file storage. 

I tried to remove the partitions and have the hard drive be one solid piece. Not gonna happen! I managed to install UNR on both the partitions. Now I have cleared out one of the partitions to use as file storage but UNR won't let me write to it. 

**Now for my question/goal: **
I want to get this second partition to the point where it is like another "drive letter" if you will (I have been a windows person all my life) where I can read write and delete at will. 

At the moment, on this disk, I have an *ext3* partition, an *extended* partition, and a *linux-swap* partition. I am pretty new to Ubuntu, and a **novice** at partitioning.

I was messing around with Gparted, and found that if I created a new partition table, the whole disk would be wiped. Is that something I would want to mess with? Keep in mind the I just want to get this drive to where I can use it as file storage. 

I received some tips telling me that if I wiped the disk and installed ext3 and a swap it would do what I wanted.

I was on another thread before, but it went dead. Here is the link to that thread for background information about what I am dealing with.
[URL="http://ubuntuforums.org/showthread.php?t=1177152"]
http://ubuntuforums.org/showthread.php?t=1177152[/URL]

To be honest, I'm freaking out here. This Asus 901 PC was a graduation gift and I just !@#$ed it up...kinda.
I find myself in these types of quandaries all the time and to be honest...I love it. I love learning about Linux! I love learning about Ubuntu!
But seriously, help me out here.:D

---

### Post by dstew on 2009-06-03
The extended partition is just a container for one or more logical partitions. If you have an extended partition, but no logical partitions in it, then you will see no file systems.

You probably just need to create a logical partition inside your extended partition. You should be able to do this with Gparted.

Alternatively, you can delete the extended partition, and create a new primary partition out of the unallocated space.

Once you have a new partition, format it as ext3. Then, you should be able to mount it to your Ubuntu desktop.

---

### Post by moebob24 on 2009-06-03
> **dstew said:**
> The extended partition is just a container for one or more logical partitions. If you have an extended partition, but no logical partitions in it, then you will see no file systems.

You probably just need to create a logical partition inside your extended partition. You should be able to do this with Gparted.

Alternatively, you can delete the extended partition, and create a new primary partition out of the unallocated space.

Once you have a new partition, format it as ext3. Then, you should be able to mount it to your Ubuntu desktop.

Well now it won't even let me format the existing ext3 partition. I'm going to attempt and re-format the whole drive partition by partition.

EDIT: Ok I deleted the swap and the extended partitions and now I have some space to work with. I'll try doing to new logical inside of a new extended. But i still cannot touch the existing ext3.
EDIT: One thing, **Am I required to have any swap in this?**

---

### Post by raymondh on 2009-06-03
Hello moebob,

Either thru UNR or a liveUSB/liveCD, can you access gparted, take a screenshot of what it outputs and post it back.  Also, access a terminal and type

```
fdisk -l
```

(small L, not 1)

and post back.  it'll help us understand what your HD set-up is right now as well as give us a visual.  Hopefully we can come up with a solution, guide or a reality check :)

Please make a back-up of your precious files.  Maybe save it someplace external at the moment.  Anytime we deal with the HD and partitioning or mounting, it is wise to assume that we can/will lose files.  Even if we don't lose files, a back-up someplace is a good practice 'eh ;)

Thanks.

---

### Post by moebob24 on 2009-06-03
> **raymondhenson said:**
> Hello moebob,

Either thru UNR or a liveUSB/liveCD, can you access gparted, take a screenshot of what it outputs and post it back.  Also, access a terminal and type

```
fdisk -l
```

(small L, not 1)

and post back.  it'll help us understand what your HD set-up is right now as well as give us a visual.  Hopefully we can come up with a solution, guide or a reality check :)

Please make a back-up of your precious files.  Maybe save it someplace external at the moment.  Anytime we deal with the HD and partitioning or mounting, it is wise to assume that we can/will lose files.  Even if we don't lose files, a back-up someplace is a good practice 'eh ;)

Thanks.

Ok, 
fdisk -l did not return anything but here are the screen shots

[IMG]http://i100.photobucket.com/albums/m15/shadowahcker/Screenshot-1.png[/IMG]

[IMG]http://i100.photobucket.com/albums/m15/shadowahcker/Screenshot.png[/IMG]

---

### Post by moebob24 on 2009-06-03
**UPDATE:**
The second drive, In the screen shot it is labeled as *sdb*, is now fully an *ext3* partition. There is nothing left on the drive. I followed *dstew's* instructions. However I am still getting the same result. It won't let me write to the drive. 

When I try to write to it I get:
```

/media/disk/\.jpg could not be saved, because you cannot change the contents of that folder.
Change the folder properties and try again, or try saving in a different location.

``` 

Same problem as last time.

---

### Post by dstew on 2009-06-03
Some thoughts. To do sudo fdisk -l you need to enter that command in a terminal window (Applications --> Accessories --> Terminal).

You cannot manipulate a mounted partition. So, if your /dev/sdb1 partition is mounted, gparted won't let you touch it.

Is /dev/sdb1 mounted? Also, what is that weird file name "\.jpg"? It could be that the file name is causing the problem. Can you get a listing of the files on the mounted /dev/sdb1 partition?```
cd /media/disk
ls -l
```

---

### Post by moebob24 on 2009-06-03
> **dstew said:**
> Some thoughts. To do sudo fdisk -l you need to enter that command in a terminal window (Applications --> Accessories --> Terminal).

You cannot manipulate a mounted partition. So, if your /dev/sdb1 partition is mounted, gparted won't let you touch it.

Is /dev/sdb1 mounted? Also, what is that weird file name "\.jpg"? It could be that the file name is causing the problem. Can you get a listing of the files on the mounted /dev/sdb1 partition?```
cd /media/disk
ls -l
```

Ok that did get an output. Lol forgot sudo

```

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x58d1ca06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         462     3710983+  83  Linux
/dev/sda2             463         490      224910    5  Extended
/dev/sda5             463         490      224878+  82  Linux swap / Solaris

Disk /dev/sdb: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d00c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         981     7879851   83  Linux

Disk /dev/sdc: 1039 MB, 1039663104 bytes
32 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 1984 * 512 = 1015808 bytes
Disk identifier: 0x8ef631df

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?     1064787     2052059   979374166   66  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(734, 123, 14) logical=(1064786, 10, 21)
Partition 1 has different physical/logical endings:
     phys=(120, 143, 6) logical=(2052058, 21, 22)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?     1738586     3726659  1972168331    7  HPFS/NTFS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(187, 180, 14) logical=(1738585, 4, 52)
Partition 2 has different physical/logical endings:
     phys=(784, 0, 13) logical=(1561856, 0, 1)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?     1653132     2637739   976730017   7d  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(252, 59, 46) logical=(1653131, 28, 39)
Partition 3 has different physical/logical endings:
     phys=(139, 118, 4) logical=(472936, 22, 28)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?     2106534     2110729     4161550   6f  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(370, 101, 50) logical=(2106533, 5, 11)
Partition 4 has different physical/logical endings:
     phys=(10, 114, 13) logical=(2110728, 8, 44)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

I'm in the USB live-run right now. I'll boot back into the hard disk and look at the file in the disk folder.

---

### Post by moebob24 on 2009-06-03
total 16
drwx------ 2 root root 16384 2009-06-03 13:13 lost+found


That is what ls -l in /media/disk gave me.

---

### Post by dstew on 2009-06-03
So, that looks like a mounted, empty disk. Try to copy a regularly named file to it.

One thought: Are you working as root?

---

### Post by moebob24 on 2009-06-03
> **dstew said:**
> So, that looks like a mounted, empty disk. Try to copy a regularly named file to it.

One thought: Are you working as root?

No I am not working as root.

Ok, Trying to copy a text file from a USB drive:

```

Error while copying "LAN_info.txt"
There was an error copying the file into /media/disk.
>Show more details:
    Error opening file '/media/disk/LAN_info.txt': Permission denied

```

I really don't know what is up. Everything says it should work.

---

### Post by moebob24 on 2009-06-03
I can't even make a folder in it. 

```

user@ubuntu:/media/disk$ mkdir test
mkdir: cannot create directory 'test': Permission denied

```

---

### Post by moebob24 on 2009-06-03
Inside the folder properties:
[IMG]http://i100.photobucket.com/albums/m15/shadowahcker/Screenshot-2.png[/IMG]

---

### Post by dstew on 2009-06-03
Apparently the disk was mounted by user "root", and is owned by "root". Root is a special user that trumps everything else. You may have accidentally activated the root account at some point, and the disk is automatically being mounted by root. Try the same command but use sudo to get root privileges, without actually logging in as root: **sudo** cp, or **sudo** mkdir.

---

### Post by moebob24 on 2009-06-03
Thats was I was thinking. I must bow down to the all mighty root!!!

---

### Post by moebob24 on 2009-06-03
Ya 
```
sudo mkdir test

```
Worked like a charm. 

So......now how do I change these permissions????

---

### Post by dstew on 2009-06-03
See [this document]("https://help.ubuntu.com/community/RootSudo"). You can use **chown** to change the owner. However, in this case, it might be that the disk is being automounted with the owner and user root. You might need to edit the file /etc/fstab to change how the disk is being mounted.

I need to go, good luck and talk to you later.

---

### Post by LewRockwell on 2009-06-03
```
whoami
```

---

### Post by moebob24 on 2009-06-03
> **dstew said:**
> See [this document]("https://help.ubuntu.com/community/RootSudo"). You can use **chown** to change the owner. However, in this case, it might be that the disk is being automounted with the owner and user root. You might need to edit the file /etc/fstab to change how the disk is being mounted.

I need to go, good luck and talk to you later.

Well thank you very much for all your help today. You have been more than helpful here!!!:D I'll figure it out.

---

### Post by moebob24 on 2009-06-03
> **LewRockwell said:**
> ```
whoami
```

running whoami shows that I am the user: 'bill'

---

### Post by moebob24 on 2009-06-03
Just for reference:

```

 # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=f1b5d578-0638-431c-8a6c-8bb734675034 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=24354a8a-c7b8-411d-8b90-2ca9bdba2cd0 none            swap    sw              0       0

```

---

### Post by pablolie on 2009-06-21
i just installed regular 9.04 desktop on my asus eeepc 901 yesterday. and found it remarkably straight forward.

i assigned the entire 4gb soldered on ssd as primary sda to mount on / (that is, most of the stuff will install there) and the 8gb as primary sdb to mount on "/home", meaning all user accounts and data will go there. mark both partitions to format, too.

no swap, ignore the warning. both ext4.

works like a charm. doesn't get along with aes+tkip security encryption on wpa2, though, go for aes, at least that worked for me on a linksys wrt610.

ps: i do not use ubuntu 9.04 netbook remix, but rather regular desktop. i truly do not like the unr user interface - and fail to see the point. the lack of screen real estate only bothers me when i am working on the browser, and firefox looks exactly the same anyhow...

---

