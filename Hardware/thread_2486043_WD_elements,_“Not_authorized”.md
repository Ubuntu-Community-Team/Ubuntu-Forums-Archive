---
title: "WD elements, “Not authorized”"
date: 2023-04-18
forum: Hardware
---

### Post by mtxlmtxl on 2023-04-18
[COLOR=#000000][FONT=Roboto]I have a WD “Elements” external disk on which I put files from “computer A” (ubuntu 16). Next, I connect it to “computer B” (ubuntu 18). However, I cannot access it or even mount it (or change permissions) from “B”.[/FONT][/COLOR]
[COLOR=#000000][FONT=Roboto]When I connect it to “computer A” I changed the permissions so that owner, group and others can read/write files on it.[/FONT][/COLOR]
[COLOR=#000000][FONT=Roboto]What do I have to do to be able to access it from “computer B”? (On "B" the option to change permissions does not appear).

[/FONT][/COLOR][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292081&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292082&stc=1[/IMG]

---

### Post by TheFu on 2023-04-18
Reads like a standard UNIX permissions issue, but I can't tell anything from GUI screen shots. Need to see the owner, group and permissions for the mounted file system from BOTH computers.  Also, need to see the output from the 'id' command for the userids on each computer.

Unix file systems only care about the uid and gid. These are numbers. The names don't matter.  If the uid/gid of the usernames on both computers match, access will "just work".

BTW, we also need for the file system to be native Linux, so ext4 would be the expected file system.  Other, non-native, file systems can be forced to work, but it is more complicated.  You'll need to **avoid using any GUI** to mount the file system.  Expect to modify the /etc/fstab to control permissions, owner, and group, for access.

---

### Post by mtxlmtxl on 2023-04-18
On "A" (ubuntu 16); uid=1000 gid=10003
On "B" (ubuntu 18): uid=1001 gid=10003
I don't know where the mounted system is on B. On A it was in /media/<username>/Elements. Both A and B are Linux. 
On B, I can only "see" the WD drive with nautilus (it's not in /media)
On A, if I do "ls -l /media/<username>/", I getdrwxrwxrwx  1 <username> mygroup  4096 feb 16 15:42 Elements/

---

### Post by The Cog on 2023-04-18
This command (on each system) should tell you where mounted. Also tell us what the filesystem is.
```
lsblk -fm | grep -v snap 
```
It's interesting that the user ID is different between the two machines. May or may not be significant though.

---

### Post by TheFu on 2023-04-18
> **mtxlmtxl said:**
> 
```
On "A" (ubuntu 16); uid=1000 gid=10003
On "B" (ubuntu 18): uid=1001 gid=10003
```


The uid's are different.  If this is a native linux file system, no bueno.

If it is a non-Linux file system, permissions are controlled at mount time. So if it is NTFS or exFAT or FAT32, good luck with that. Permissions for those are set through mount options AND are the same for all files and directories, which isn't good on a multi-user Unix system.

I've never had good luck mounting file systems using any GUI, which is what it appears your system is trying to do. This is fine for quick file copies off a temporary USB flash drive, bot not good for real storage that will be connected to the system all the time.  Storage that is always connected shouldn't be under /media/{username}/.

I'll wait for the **lsblk** command requested by The Cog above, before attempting to help further.

---

### Post by mtxlmtxl on 2023-04-19
The lsblk command gave me this: 
[FONT=courier new]NAME        FSTYPE   LABEL     UUID                                 MOUNTPOINT                       SIZE OWNER GROUP MODE[/FONT]
[FONT=courier new]sda                                                                                                931.5G root  disk  brw-rw----[/FONT]
[FONT=courier new]&#9492;&#9472;sda1      ntfs     Elements  04821C7E821C7680                                                    931.5G root  disk  brw-rw----[/FONT]

I tried (naively) to do something like "sudo ls /dev/sda/" and "sudo ls /dev/sda1/" but it tells me that /dev/sda is not a directory. 

I am sorry, the rest of your post I don't understand at all. I am not a system manager so I don't know what you mean with "native file system". I use Linux Ubuntu machines and a disk that I just connect to the either one of them to copy files to it. As far as I know this disk is not "native Linux". I don't care if I have to mount via "GUI" or via command line, as long as I can acces the files that are on the disk. 
 I just want one simple thing (and I was hoping WD Elements could do that): 
1) Connect a WD disk to a Linux ubuntu 16 machine and copy files to it (and read them back)
2) Disconnect the WD disk from the ubuntu16 machine
3) Connect the same WD disk to a (different) Linux ubuntu 18 machine and copy files to it (and read them back). Indeed, like a USB drive, but larger. 
I don't care about permissions or securities or anything like that.  USB sticks always stop working after a while and Google Drive is not large enough for my files. 
What's the point of an external disk if I cannot connect it to different machines? I mean, I am using the disk as a backup. This means that if my machine breaks down, I still can retrieve the files from the external disk and copy them to another machine. Isn't that the point of backup disks?
I know that there are problems when doing this with Mac systems, but in the past I have used WD disks between different Linux machines and even between Linux and Windows without any problem.

---

### Post by TheFu on 2023-04-19
```
NAME FSTYPE LABEL UUID MOUNTPOINT SIZE OWNER GROUP MODE
sda 931.5G root disk brw-rw----
&#9492;&#9472;sda1 _ntfs_ Elements 04821C7E821C7680 931.5G root disk brw-rw----
```
Tells me this is using NTFS.  That isn't a native Linux file system and it becomes much more complex to mount correctly.

Windows people don't really think about **file systems.**  Unix people have to, since we have many choices for different purposes.  NTFS can only be used for data files.  It cannot be used for any part of a Linux OS nor can it be used for user's HOME directories nor for programs.  It is only for data.

In Linux/Unix, storage is handled by the admin.  If there isn't one, then YOU are the admin and need to learn enough to make it work.

Linux backups require more than just a copy of the data.  The owner, group, permissions, ACLs and xattrs also need to be retained.  If you're idea of a "backup" is just the data and you only backup "data files" ... like Office documents, videos, music, then NTFS is fine.  Otherwise, NTFS shouldn't be used and a proper native Linux file system is required.  That's your business and we can help, but YOU have to decide.

We need to know 1 more thing to safely mount this NTFS file system - a unique identifier.  That can be a UUID or a LABEL. It already has a label of "Elements", which is a little generic and can cause issues if you ever connect another similar drive.

Anyway, assuming you just want to mount it as NTFS to the /media/backup directory, add this line to your /etc/fstab file using sudoedit.  It needs to be 1 line and not shared with any exiting lines already in the file. Don't touch any of those.  Also, ensure the file has 1 blank line at the bottom with nothing on it.
**$ sudoedit  /etc/fstab **
```
LABEL=Elements   /media/backup ntfs nofail,nodev,windows_names,nosuid,async,big_writes,timeout=2,uid=1001,gid=1003,fmask=0002,dmask=0002,errors=remount-ro  0 2

```Again, that's all on 1 line and the "options" cannot have any spaces between them. Don't forget the last 2 fields. Those are important too and need to be on the same line. You'll likely need to scroll to see/grab them.

After you enter this line into the file, run **sudo mount -a**.  Your userid and group will have full access.  The uid and gid numbers can be replaced with the names.  It is only at mount time that the owner, group and permissions can be set. That's a limitation of non-native file systems.

Linux file systems are all about the uid/gid to control access for unencrypted files.

---

### Post by mtxlmtxl on 2023-04-19
Hi again,
Yes, this worked. And yes, I only need "NTFS" and I only need to copy data files, I don't care about the rest. By the way, the fstab did not have an empty line at the bottom, but following your advice, now I does (after the new line with the "Elements" stuff). 
Two more questions: 
After copying the files to the disk, I will again disconnect it from the Ubuntu18 machine. Do I have to delete the "Elements" line from the fstab file again? Will the system run into problems when it tries to mount something that isn't there?
And another question: I am assuming I can still connect the disk to the Ubuntu16 machine without problems. Is that correct?

---

### Post by TheFu on 2023-04-19
> **mtxlmtxl said:**
> Hi again,
Yes, this worked. And yes, I only need "NTFS" and I only need to copy data files, I don't care about the rest. By the way, the fstab did not have an empty line at the bottom, but following your advice, now I does (after the new line with the "Elements" stuff). 
Two more questions: 
After copying the files to the disk, I will again disconnect it from the Ubuntu18 machine. Do I have to delete the "Elements" line from the fstab file again? Will the system run into problems when it tries to mount something that isn't there?
And another question: I am assuming I can still connect the disk to the Ubuntu16 machine without problems. Is that correct?

Whoa ... there .... you can't just unplug a mounted drive.  The mount we did is for performance and happens at boot.  There are other options to allow end users to **mount** and **umount** storage.  That isn't something I provided.  There is no "eject" option.

When I need a USB device to be mounted/umounted on demand, I don't use the fstab.  I use something called 'autofs', which will use the same options, but has a more complex setup with multiple files that need to be modified in very, very, specific ways.  You can read more about that here: [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)
The cool thing about autofs is that it provides access to the high performance mount options, while also mounting storage only when demanded by **any** program on the computer. It keeps the mount until a few minutes AFTER all the files on it are closed, then it automatically umount's the storage.
For example, I have a 250G NTFS partition that is used with a video recording hardware device. That device only supports NTFS. When mounted (automatically because I cd'd into the directory ... ), it shows:
```
$ df /misc/250G
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdc1       233G   19G  215G   8% /misc/250G
$ ls                   
Encode_768_1.mp4*  Encode_768_4.mp4*  Encode_768_7.mp4*  Encode_768.mp4*
Encode_768_2.mp4*  Encode_768_5.mp4*  Encode_768_8.mp4*  mkvm-script.pl*
Encode_768_3.mp4*  Encode_768_6.mp4*  Encode_768_9.mp4*  t*
```
As long as any program uses any files under  /misc/250G, it will stay mounted.  If I chdir out of the /misc/250G and wait 2 minutes, it will be umounted, automatically, if I even use **ls /misc/250G**, it will be mounted again, so I need to check if it is currently mounted before unplugging it.  Ooops, I ran:
```
$ df -Th /misc/250G
Filesystem     Type     Size  Used Avail Use% Mounted on
/dev/sdc1      fuseblk  233G   19G  215G   8% /misc/250G

```
and that mounted it, need to wait another 2 minutes and check the mount table, mtab, for it.
```
$ egrep 250G /etc/mtab
/etc/auto.misc /misc/250G autofs rw,relatime,fd=6,pgrp=3139,timeout=60,minproto=5,maxproto=5,direct,pipe_ino=53281 0 0
**/dev/sdc1 /misc/250G fuseblk** rw,nosuid,nodev,noatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 0 0
```
Still mounted ... wait another minute:
```
$ sleep 1m; egrep 250G /etc/mtab
/etc/auto.misc /misc/250G autofs rw,relatime,fd=6,pgrp=3139,timeout=60,minproto=5,maxproto=5,direct,pipe_ino=53281 0 0

```
Ok, not mounted.  There's just the autofs line, not the fuseblk line.  Running **df -Th** shows it isn't mounted too.

I have a few external storage devices setup with specific LABELs that are configured in autofs to mount on access. I tend to transfer files using network connections, but for camera flash drives and this 1 video recording HDD, that isn't a choice.

Clear as mud?

Whatever you do, never unplug a mounted file system.  That leads to corruption and with Linux using NTFS, the only real solution is to format a new NTFS file system over the corruption. That wipes all data.

---

### Post by mtxlmtxl on 2023-04-19
Okay, clearly we don't understand each other. I have only one question now: how do I unmount this external disk from my Ubuntu 18 system without damaging anything? I want to disconnect it.

---

### Post by TheFu on 2023-04-19
```
sudo umount /media/backup
```

Yes, the command is spelled 'umount'. It can take some time if some operations are still underway for the disk buffers to clear, so most admins will type 
```
sync
sync
```
and when the 2nd one finishes (the prompt returns), then it is safe.  Don't copy/paste those commands. Type them.

I suppose there are mount options to allow normal users to mount/umount storage. I've just never used them, since the power to mount is also the power to destroy. I don't think that any end-user should have that capability.

---

### Post by mtxlmtxl on 2023-04-19
Thank you.  I did  *sudo umount -l /media/backup* and then edited fstab to delete the Elements line. The machine is still running fine so I guess no harm is done.
I am the only user to the machines, and in fact use mount and umount to mount other external disks as well. It's just that in case, I don't see exactly how to do it but I'll figure it out. Thanks for the help.

---

### Post by TheFu on 2023-04-19
If you have the line in the fstab with the "noauto" option -  you need to edit that into the options:
```
# To mount:
sudo mount /media/backup

# To un-mount
sudo umount /media/backup

```
That's a bunch of hassle compared to using autofs, of course.

I'm sure there are other methods. I just don't use or know them.

---

