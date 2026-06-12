---
title: "Cannot copy files to removable drive"
date: 2019-01-11
forum: Hardware
---

### Post by G0at1 on 2019-01-11
Hi,  I've attached a removable drive to my PC. I can access files on it and copy/paste them to my Ubuntu drive; however, I cannot copy files from my Ubuntu drive to the removable drive. I can't create new folders/files on this drive either.  Anyone know what's going on?  Thank you

---

### Post by rbmorse on 2019-01-11
Attach the external drive, disconnect any other external storage media that may be attached, then open the file browser and navigate to:

Other locations > computer > media > <your username>.

You should see a folder in that location that represents the external drive.  If you click on it you should be able to see the contents of the external drive.  The folder will be named with the label of the external's file system, or if the external drive does not have a file system label, it will have a unique device identifier that will look something like "d858727c-59fd-49a0-9d7e".   This folder is called a mount point.  Think of it as the gateway between the folders and files on your external drive and the file system on the computer itself.  

Right click on the folder, click on "properties" then click on the "permissions" tab.  

That will show you the owner of the mount point and the permissions granted for using what it contains (in this case your external drive).  If the owner is anyone other than "me" or <your username>, chances are your user does not have permission to write to the drive, only permission to read and access it.  That explains why you can read and copy files from the external, but can't create folders or save files on it. 

There are a couple of ways to fix this, but the easiest in my mind is to open a terminal window and execute the command (very carefully, mind):

```
sudo chown <your username>:<your username> /media/<your username>/<device identifier>
```

The device identifier will either be the file system label from the external or the system determined unique device identifier.  Note the colon ( : ) between the two instances of <your username> and there are no spaces around the colon. You will be prompted to enter your user's password, then prompted to enter your user password again. Example:

```
sudo chown ron:ron /media/ron/safety
```

where the username is "ron" and the external drive has the file system label "safety". 

You should now be able to read and write to the external drive.

---

### Post by G0at1 on 2019-01-12
Thank you for responding. When I go to: Other locations > computer > media > <your username>, I see "New Volume" which is the external drive. Under permissions, I see: Owner: Me. Access: Create/delete files. Group: My name. Access: Create/delete files. Others: blank. Access: Create/delete files. Security context: unknown. 

What should I do?

---

### Post by TheFu on 2019-01-12
rbmorse is correct, if the partition mounted is using a Linux file system.  Great explanation.

Most external disks come with either NTFS or FAT32 or exFAT file systems. These do not support permission changes after mount, so chown and chmod don't work.  For these other file systems, either the mount needs to happen using the very slow gvfs FUSE mount technique - most GUI file managers will do this or if the fstab/autofs are used, then at mount time the userid and group must be used so your specific userid can have write access.  If this will be a permanently connected storage device, then using the fstab method, with the correct mount options, can be much, much, faster.

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions) explains how to update the /etc/fstab for this better performance.  To safely edit the fstab file, use the **sudoedit /etc/fstab** command.  **sudoedit** is much safer than using other options like gksudo or pkexec or any sudo incarnation you may see all over the internet.

I use *autofs* for USB storage mounts. You might not want to, since it is a little more complex. My options are:
```
250G -nodev,nosuid,noatime,async,big_writes,timeout=2,fstype=ntfs,uid=1000,gid=1000 LABEL=250G
```

The equiv fstab line would be something like:
```
LABEL=250G    /Data ntfs nodev,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000 0 0
```
Notice that I mount using the LABEL, not device or UUID.  I find this easier to handle for USB storage. The uid/gid are specific to my userid - the **id** command will show values you can use.  If you need to allow multiple users to have concurrent access, then the userids will need to be in a shared unix group.  The "big_writes" helps greatly with NTFS performance.  The /Data directory must pre-exist before mounting.  Any empty directory will work.

Once the fstab is setup, just run **sudo mount -a** to mount it immediately.  It will be mounted automatically at boot from now on.

Clear as mud?

---

### Post by G0at1 on 2019-01-12
I will only connect and turn on this external drive once a week or so (maybe less) to backup files as needed. I'm sure it's NTFS. As far as the rest of your response, I've read it a few times and I don't understand anything you said. :( I'm sorry, what do I have to do again?

And I don't understand why Linux makes it so hard for people to use it easily. Why can't I just be able to plug in my external hard drive and use it like I do with a USB stick?

---

### Post by TheFu on 2019-01-12
> **G0at1 said:**
> I will only connect and turn on this external drive once a week or so (maybe less) to backup files as needed. I'm sure it's NTFS. As far as the rest of your response, I've read it a few times and I don't understand anything you said. :( I'm sorry, what do I have to do again?

If this drive is a backup for Linux, then you should refomat it to use a Linux native file system like ext4.  Many backup tools don't work correctly when using NTFS with Unix files. In Unix, the owner, group and permissions for files are at least 50% of the backup data needed.

If it is only connected once a week, then I wouldn't modify the fstab.  I'd use the autofs method, though I suspect this is beyond you current skill.

Exactly how are you backing up the data?  Aptik? Duplicity, Duplicati, something else?  I use a tool called rdiff-backup. It is extremely efficient and having 60+ days of backups only takes about 10-20% more storage than the original files.  I do automatic, daily, backups. These take 1-4 minutes for most systems.

From last night:
```
=== Time for Backups to spam2 === 
StartTime 1547277065.00 (Sat Jan 12 02:11:05 2019)
EndTime 1547277075.29 (Sat Jan 12 02:11:15 2019)
ElapsedTime 10.29 (10.29 seconds)
TotalDestinationSizeChange 1081 (1.06 KB)


=== Time for Backups to lubuntu === 
StartTime 1547273707.00 (Sat Jan 12 01:15:07 2019)
EndTime 1547274150.82 (Sat Jan 12 01:22:30 2019)
ElapsedTime 443.82 (7 minutes 23.82 seconds)
TotalDestinationSizeChange 28712008 (27.4 MB)


=== Time for Backups to hadar === 
StartTime 1547274905.00 (Sat Jan 12 01:35:05 2019)
EndTime 1547274930.69 (Sat Jan 12 01:35:30 2019)
ElapsedTime 25.69 (25.69 seconds)
TotalDestinationSizeChange -90288 (-88.2 KB)


=== Time for Backups to nextcloud === 
StartTime 1547279409.00 (Sat Jan 12 02:50:09 2019)
EndTime 1547279539.40 (Sat Jan 12 02:52:19 2019)
ElapsedTime 130.40 (2 minutes 10.40 seconds)
TotalDestinationSizeChange 7314615 (6.98 MB)


=== Time for Backups to cb35 === 
StartTime 1547269387.00 (Sat Jan 12 00:03:07 2019)
EndTime 1547270145.97 (Sat Jan 12 00:15:45 2019)
ElapsedTime 758.97 (12 minutes 38.97 seconds)
TotalDestinationSizeChange 98967478 (94.4 MB)

```

You get the idea.

---

### Post by G0at1 on 2019-01-12
By "back up" I literally mean copy/pasting files from my main hard drive to the external one. I don't use any utilities yet. I just got on Ubuntu and don't know my way around. I think you're right though. It looks like I have to copy all my files from the NTFS drive to Ubuntu > format it to ext4 > put the files back > save my sanity. :D  Assuming, I copy everything to Ubuntu, how do I format the drive if it's not letting me even write to it? I right-clicked on it and don't see a "format" option. I just see Open, Open in new tab, Open in new window, Unmount.

---

### Post by rbmorse on 2019-01-12
Was the external drive connected to a Windows host that was "hibernating" when it was disconnected?  

If that happens, a Linux host would mount the external as a "read only" device.

---

### Post by G0at1 on 2019-01-12
No, it was not and I normally always "eject" my drives in Windows before unplugging even though it's not really required.

---

### Post by TheFu on 2019-01-12
It cannot be mounted for this work.

To format as ext4, there are many ways.  I'd use **sudo -H gparted** (this is the 1-time running a GUI with sudo is fine).  Then I'd delete everything, create a new GPT partition table and then create an EXT4 partition, setting the LABEL to what you want to use at mount time in the fstab or via autofs.  The -H is absolutely critical. ABSOLUTELY.

If you want to go old, old, old, school, you can use fdisk to wipe the disk, create the GPT partition table, and partition.  Then exit that and run **sudo mkfs -t ext4 /dev/disk/......** whatever the device is. Don't make up a device. If you get the wrong one, you will be wiping all the existing data. Not what anyone wants.  Unix does what we tell it, not what we actually mean.

Knowing how to do it via a GUI is only useful on desktops.  On servers, there isn't a GUI, so no gparted program.

I would stay away from any other tools. Some cause problems that are easily avoided by not using them.

I keep mentioning autofs.  Why?  The autofs manpage explains:
```
DESCRIPTION
       autofs  controls the operation of the automount(8) daemon(s) running on
       the Linux system. Usually autofs is invoked at system  boot  time  with
       the  start parameter and at shutdown time with the stop parameter. Ser&#8208;
       vice control actions can also be manually invoked by the system  admin&#8208;
       istrator to shut down, restart, reload or obtain service status.
```

In short, it can be configured to mount storage on-demand, as needed. If storage isn't used for a period of time, it is removed from the mount table (umounted) automatically. This frees up resources.  Also, autofs provides access to kernel-level mounts which are much, much, faster than FUSE mounts.

NEVER just pull storage out from a Unix system. Always umount them or use the eject button in the GUI.  It is common for Unix to buffer data for long periods before writing to physical media.

---

### Post by G0at1 on 2019-01-12
Holy cow the partitioning worked and then I used the sudo chown command so I can write to it. Now I see a "lost+found" folder which I don't know what it is and can't delete but I don't care at this point.

The only thing I don't understand is what I need to do with fstab. I'm totally lost. In Terminal, I typed **sudoedit /etc/fstab. **I just don't understand what I'm supposed do at this point. I labeled my device: 300GBDrive

---

### Post by TheFu on 2019-01-12
If the device isn't always connected, I wouldn't use the fstab method. Reasons given above.

The lost+found/ directory is part of most file systems. That is where corrupted files that lose their parents (like the directory they are in) are put.  The **fsck** command does this.

Since you've converted to ext4, I think the performance issues caused by using a GUI tool don't happen, so you can use the file manager you like to mount and umount (<-- that is the correct command) the storage.  Probably sufficient for your needs today.  Yes?

---

### Post by G0at1 on 2019-01-12
No, it's not always connected; just when I want to back up some documents and music. YES! I'm totally set. Thank you both very much for helping me out! :)

---

### Post by G0at1 on 2019-01-13
Can I ask one more question? I formatted another external drive and did everything as the above. This one doesn't automatically show up on my desktop when I plug it in. I have to go to Other Locations to open it. Once I do that, it shows up on the desktop. Also, the previous external drive has a USB logo on it on the desktop. This drive has no logo. Also, the previous drive says "safely remove drive" and this second one says "unmount" before I want to unplug.

---

### Post by G0at1 on 2019-01-14
> **TheFu said:**
> If the device isn't always connected, I wouldn't use the fstab method. Reasons given above.

The lost+found/ directory is part of most file systems. That is where corrupted files that lose their parents (like the directory they are in) are put.  The **fsck** command does this.

Since you've converted to ext4, I think the performance issues caused by using a GUI tool don't happen, so you can use the file manager you like to mount and umount (<-- that is the correct command) the storage.  Probably sufficient for your needs today.  Yes?

I tried to send you a PM about my question above but left it in the Conversation section. Sorry about that! Everything resolved.

---

