---
title: "Can't alter /media/disk partition"
date: 2008-11-15
forum: General Help
---

### Post by Alloie on 2008-11-15
Hello all,
I have an issue that's really rockin' my socks off..  I know eveyone's first ambition is to just tell me to chmod/chgrp/chown and all that happy bs that I've already done.  I have also tried to edit my fstab in hopes that my machine will recognize the partition, but to no avail....so I deleted all changes made and brought it back to what it was originally. It seems that my ownership on my /dev/sda6 (/media/disk) has been altered to a different owner (UUID=EF3F-0F64) and I have no write/executable permissions at all. It has become a read only partition. It seems that my fmask, and dmask has been altered, probably when I was dinking around with samba, and all the standard permission changes can't be made.  Is there a particular way that I can change my partition to make me the owner again? Perhaps you have a workaround? The data I have on this partition is very important, and I don't want to reinstall.  Thanks in advance.

---

### Post by SleepingProphet on 2008-11-15
chown doesn't work at all?
What file system is on the mystery partition?

---

### Post by Alloie on 2008-11-15
No, all the beauty of the normal way of changing permissions is not allowed. It's a vfat partition specifically for storing files away from the operating systems.

---

### Post by lswb on 2008-11-16
vfat filesystems don't use unix style permissions. The best you can do is set access policy in /etc/fstab. In the options field, you can specify various mask settings and user access settings to control access to files and directories on the vfat partition. Have a good read of the man pages for fstab and mount and if you have questions after that, post again.

---

### Post by Marcus Derekus on 2008-11-16
try opening console and entering: gksudo nautilus 

then access files through the window that appears

---

### Post by Alloie on 2008-11-16
Alright, I have modified my fstab, and it's in accordance with the man pages, so it should work. But, I took a step backwards and gave a bad mount option through the right click, mount options settings, and now it won't mount at all unless I gksudo to it, and even then I still can't write or delete from it. Guess that's what I get for pushing more buttons than necessary... It seems that the fstab config isn't overriding whatever is blocking my access to this drive. Here's a copy of my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=ed21dc46-79be-4c13-b485-7f18c13da181 /               ext3    relatime,errors=remount-ro,noatime,nodiratime 0       1
# /dev/sda7
UUID=e31a41a5-5204-4134-b93a-2cec2d4d32b6 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sda6
uid=1000	/media/disk	vfat	dmask=777,fmask=777,users,auto,mount-o,rw,noatime,nodiratime	0	0


And here's all my drives via blkid:


/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0C07" TYPE="vfat" 
/dev/sda2: UUID="88AAFB6EAAFB56E2" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="E816D56616D53672" TYPE="ntfs" 
/dev/sda5: LABEL="MEDIADIRECT" UUID="6602-5E67" TYPE="vfat" 
/dev/sda6: UUID="EF3F-0F64" TYPE="vfat" 
/dev/sda7: TYPE="swap" UUID="e31a41a5-5204-4134-b93a-2cec2d4d32b6" 
/dev/sda8: UUID="ed21dc46-79be-4c13-b485-7f18c13da181" TYPE="ext3" 

The drive I'm working with is /dev/sda6. I know it's a different UUID in the blkid, but before I wrote the new fstab line, it was no one's drive. Now it's owner is me, and I still don't have -w access to it.

---

### Post by vanadium on 2008-11-16
Do you know why you added all these options to the line for your /dev/sda6? Anyway, the first entry should be a reference to an UUID or a device name. Try

```

# /dev/sda6
UUID="EF3F-0F64" /media/disk vfat uid=1000 0 0

```
(this assumes you want to have this partition owned by user 1000, change accordingly if your uuid is different)

---

### Post by Alloie on 2008-11-16
Yeah, I know what I wanted it to do, but I tried the more basic config anyhow.  Still to no avail, it gives me the "Cannot mount volume, invalid mount option when attempting to mount the volume."  It seems it's something else, but I can't put my finger on it. I obviously tried to change my fstab to chown the dmask and fmask options, I could be wrong, but that seems to be the issue. Is there any way to change these permissions?  I can only access the partition through the gksudo nautilus command, and still can't delete anything from it.

---

### Post by lswb on 2008-11-16
That's a pretty good attempt for someone who just read the manpage for the 1st time! Let's just fix it up a little. You posted:
> 
# /dev/sda6
uid=1000 /media/disk vfat dmask=777,fmask=777,users,auto,mount-o,rw,noatime,nodiratime 0 0


In the first field, you have uid=1000. a uid refers to your user id. What you want here is a _UUID_, (Universally Unique IDentifier) and you wouldn't be the first person to get them confused. So the first field needs to be changed to "UUID=EF3F-0F64" BTW this field can use a device name like "/dev/sda6" or a disk label like " label="LABELNAME" " but there are some good reasons to use the UUID so let's stick with that for now.

Now the 4th or options field: This is where it gets interesting. Delete "mount -o" The mount command is for manually mounting a filesystem on the cli. In the /etc/fstab file, we just list the options in the 4th field of the fstab line. "noatime" and "nodiratime" don't really apply to a vfat partition so they can be removed as well.

There is a "defaults" option that includes "auto" and a few others you likely want, so lets use that.

The mask settings work just the opposite of how they do with chmod. They are used to _restrict_ permissions rather than allow them. Honestly, I don't have a vfat partition on my present system to compare, and I can't think through all the ramifications right now, so to get going quickly, lets just use umask=000. It would be a good idea to read up on the dmask, fmask, uid, and gid options for vfat to get them set them up just the way you want. And for character set compatiblilty for DOS filenames the option "utf8" is usually recommended.

With these changes the line now reads:

```
 
UUID=EF3F-0F64 /media/disk vfat defaults,umask=000,utf8  0 0

```

Try that (substitute correct UUID and mount point names if necessary) in your fstab. Then from command line, type

sudo umount /media/disk
sudo mount -a

and see what happens.

---

### Post by Alloie on 2008-11-17
Alright, I gave that string a shot, and now instead of it not existing, from the attempt to mount from the places/partition menu, it tells me I do not have permission. From the terminal, it tells me the partition doesn't exist.... so, what's the next step?

---

### Post by lswb on 2008-11-17
Make sure the mount point you are using isn't already in use for another filesystem. In a terminal,

mountpoint /media/disk
should return "not a mount point"
If it says it is a mount point, select or mkdir an empty root- owned directory somewhere and use the full path to it where I use /media/disk below (I would recommend you make a different mountpoint anyway since this partition is installed in your internal hd, not removable media)

Verify that the vfat partition is /dev/sda6 by using "sudo blkid" or "sudo fdisk -l" If it is different substitute where I have used sda6 below. 

First, in case it is mounted in some oddball way,
sudo umount /dev/sda6
then
sudo mount -t vfat -o defaults /dev/sda6 /media/disk

The try
sudo ls /media/disk
and see if you can access the partition. If so recheck the uuid and make sure it is entered correctly in fstab and that there are no other errors in the line for the vfat partition. (No spaces between the option items separated by commas, make sure you don't have an 'o' where it should be zero, etc.)  When you think it is corrrect,

sudo umount /media/disk
sudo mount -a

If you have no success copy the output of "sudo fdisk -l" and paste it into your next post.

---

### Post by Alloie on 2008-11-18
I opened up my Gkrellm today for the first time in a while, and noticed something peculiar... I shows that I have three users. As far as I know, I am the sole user of my machine, and have no idea how that happened. Probably something to do with samba, right? Could this possibly be the reason I am locked out of my partition?

---

### Post by louieb on 2008-11-18
Not likely the other users have anything to do with you not being able to access the partition.  More likely  you have couple of terminal windows open.  To find out who is logged on use the **finger **command.

---

### Post by vanadium on 2008-11-19
If instead of telling us what the prompt does, copy/paste the commands and their output here. This will allow some real diagnosis of the problem. Before proceeding, it might be a good idea to check the integrity of the file system. Under linux, broken file systems are mounted read-only or not at all.

---

### Post by Alloie on 2008-11-19
Right.... after much debate with my soul as to whether or not to reinstall, I finally, after much more frustration, reinstalled.  BUT, after all the new packages were installed, and it became a fresh system, I still have no privileges on my fu!@#$g partition!!!!!  WTF!!!! I thought vfat wasn't supposed to retain privileges!!!!  And to top it all off, it's now a read-only system.... Please, someone....I really need help.

---

### Post by lswb on 2008-11-19
Please run "sudo fdisk -l" in a terminal, and paste the output into your next post, along with a copy of your /etc/fstab file.

---

### Post by Alloie on 2008-11-19
Here's a copy of the output sudo fdisk -l, 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2              10        1315    10485760    7  HPFS/NTFS
/dev/sda3   *        1315        6414    40960000    7  HPFS/NTFS
/dev/sda4            6415       19458   104768538+   f  W95 Ext'd (LBA)
/dev/sda5           19131       19458     2620416   dd  Unknown
/dev/sda6            6415       15387    72075591    b  W95 FAT32
/dev/sda7           15388       15509      979933+  82  Linux swap / Solaris
/dev/sda8           15510       19130    29085651   83  Linux

Partition table entries are not in disk order


and here's a cp of my /etc/fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=5000807a-2e79-4c40-8a3c-e2c15e6da4a9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=e4b657a6-4e85-4c48-837b-999394147e9a none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


It seems that there is no entry for my 73.8 gig partition... just like before the reinstall..... which, by the way, I am totally regretting...

---

### Post by vanadium on 2008-11-20
Since Hardy 8.04, volumes by default are only mounted 'on demand', not automatically during startup. If you want the latter, you need to include the drive in /etc/fstab yourself.

I already told you it is necessary to check the integrity of the filesystem before attempting anything else. Did you do that?

To diagnose an eventual problem with mounting, mount the disk manually in the terminal. this way, you can see any error messages in the console and have a hint of what is wrong.

Therefore
1) First check and, if needed, repair the file system (you can use "chkdsk <driveletter> /f" for now in MS Windows. The linux tool is dosfsck, see "man dosfsck").
2) Try whether now, you can normally acces the partition with full permissions.
3) If not, mount the drive manually. Issue following command, copy/paste the entire session here. Supply your user password when a "sudo" command requests it

```

sudo umount /dev/sda6
cd ; mkdir test
sudo mount /dev/sda6 test
echo "this is the content of a new file" > test/NewFile
ls -l test
cat test/NewFile
rm test/NewFile
sudo umount /dev/sda6

```

This will reveal whether you can manually mount the drive and whether you can read/write to it.

---

### Post by Alloie on 2008-11-22
I ran dosfsck, and it seemed to work really well till it hit one particular folder, then it hangs saying:

dosfsck 2.11 (12 Mar 2005)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Checking we can access the last sector of the filesystem
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00
  Not automatically fixing this.
Boot sector contents:
System ID "MSWIN4.1"
Media byte 0xf8 (hard disk)
       512 bytes per logical sector
     65536 bytes per cluster
        32 reserved sectors
First FAT starts at byte 16384 (sector 32)
         2 FATs, 32 bit entries
   4504576 bytes per FAT (= 8798 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 9025536 (sector 17628)
   1126043 data clusters (73796354048 bytes)
63 sectors/track, 255 heads
 103040973 hidden sectors
 144151182 sectors total
/ISOs
  Contains a free cluster (945694). Assuming EOF.
/14 - mp3
  Contains a free cluster (520114). Assuming EOF.
/14 - mp3
  File size is 6918698 bytes, cluster chain length is 0 bytes.
  Truncating file to 0 bytes.
/Political Punk Bands.odt
  Contains a free cluster (489378). Assuming EOF.
/docPPb.odt
  File size is 8830 bytes, cluster chain length is 0 bytes.
  Truncating file to 0 bytes.
/2752518529_1c2c1c512b_o.jpg
  Contains a free cluster (855712). Assuming EOF.
/2752518529_1c2c1c512b_o.jpg
  File size is 112042 bytes, cluster chain length is 0 bytes.
  Truncating file to 0 bytes.
/Desktop/..
  Start (1060275) does not point to .. (0)
/Folder1/..
  Start (1060275) does not point to .. (0)
/Folder2/..
  Start (1060275) does not point to .. (0)
/Folder3/..
  Start (1060275) does not point to .. (0)
/Folder4/..
  Start (1060275) does not point to .. (0)
/Folder5/..
  Start (1060275) does not point to .. (0)
/Folder6/..
  Start (1060275) does not point to .. (0)
/Folder7/..
  Start (1060275) does not point to .. (0)
/Tubes/File  and
/School Work/PanduitNetworkInfrastuctureEssentials/Labs/ModuleTwo
  share clusters.
  Truncating second to 131072 bytes.
/BackedUpBookmarks/..
  Start (1060275) does not point to .. (0)
Reclaiming unconnected clusters.


Then it just sits there.. I let it sit overnight to see if anything would happen, but that's about as far as it went.  Should I have added the -r argument? I only ran the -av arguments...

---

