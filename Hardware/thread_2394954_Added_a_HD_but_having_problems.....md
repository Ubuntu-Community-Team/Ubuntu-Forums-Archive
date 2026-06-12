---
title: "Added a HD but having problems...."
date: 2018-06-24
forum: Hardware
---

### Post by exploder on 2018-06-24
I added a 1 TB hard drive to my desktop, Kubuntu can see it but I can not create folders or do anything with it. Can someone tell me what I am doing wrong?

---

### Post by TheFu on 2018-06-24
Well, what did you do exactly? Plugging it in isn't enough.  All the defaults from disk makers assume Windows, which doesn't match what a Linux user needs.

In Linux, there are many different ways to handle storage depending on your needs and how important the data might be.   What is the purpose for this drive?   Did you buy 2 of them, so you have somewhere for backups?

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) might be helpful.  There is a how-to for almost any common activity you might want.

The short answer from that link:
* partition the drive
* create new file systems - ext4 if you don't have any good reason for something else. Do not use NTFS or FAT-whatever
* create a mount point (empty directory) for each new partition
* manually mount the partition(s) to the mount point(s), and manually setup any permissions.

If everything is working, you'll probably want to automate mounting.  For internal HDDs, modify the **fstab** config file. For USB or other external devices, you probably want to use **autofs**.  There are manpages for each and how-to guides a help.ubuntu.com for both.

NEVER unplug a USB storage device without **umount**'ing it first.

A few rules of thumb about mount locations from my multiple decades as a Unix admin:
* /media/ is for disks that the OS automatically mounts. Best to avoid it for any disks you manually want to mount.
* /mnt/ is for temporary mounts and used by admins to have temporary access to partitions. Not for permanent mounts.
* Best NOT to mount a new disk under 1 individual userid's HOME.  This will likely create backup failures in the future. I prefer to either mount the the new storage for /home/ and upgrade all userids storage amount or mount it under /D/x1, x2, x3, x4 ... as more and more storage is added.  Backup storage really should not be directly connected to the machine to prevent malware and crypto-locker stuff, but if you must, /B/x1, x2, x3, x4 ... you get the idea.
* Using symbolic links from the new storage to a HOME directory is fine for convenience reasons.  I also like to use the cdpath environment variable for convenience.
* I always use LVM under the file systems to make resizing storage in different areas easier later. LVM also provides live backup techniques that cannot be added later.   But LVM's added flexibility does have 1 downside. Added complexity. I wouldn't recommend it for someone having issues mounting storage.

Of course, others will have different experiences and different opinions.

---

### Post by oldfred on 2018-06-24
Have you partitioned it with gparted or other tools.
And then formatted it? Also ifusing Windows, then you may want NTFS. But if not using Windows do not use NTFS.

And if a Linux format given yourself ownership & permissions to use it? For each partition.

And if internal drive, you probably want to mount each partition using fstab, so you can give it a mount point that makes sense. I use /mnt/data, but some have very large music files  may directly mount into /home/music or video or whatever data you have.

       gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[URL="https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions"]https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions
      [/URL]
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.dedoimedo.com/images/computers/2009/gparted-create-extended.png](http://www.dedoimedo.com/images/computers/2009/gparted-create-extended.png) 
Ownership & permissions:
 Seems like a better way as you have more control over what is executable. Isee post #8 & 10 by morbius1.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)
sudo chmod -R a+rwX,o-w /mnt/data
sudo chown -R $USER:$USER /mnt/data
#where $USER should be your login name
#or to see user
echo $USER

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

---

### Post by exploder on 2018-06-24
Thank you both very much! This did the trick,

sudo chmod -R a+rwX /media

Permissions were the problem. Thanks again!

---

### Post by TheFu on 2018-06-24
Do you understand what **sudo chmod -R a+rwX /media ** did?

That just gave anyone on the system the ability to write and delete to all files from /media down.  That probably isn't really advisable.  Basically it is chmod -R 777 which should almost never be used ... ever, unless you are setting up a system to be hacked.

---

### Post by exploder on 2018-06-24
I unplugged the drive because I am not understanding all this. Why is is such a task to add a hard drive for backups and storage? I need a more step by step explanation to understand how to fix this.

---

### Post by TheFu on 2018-06-24
It is only confusing if you don't understand Unix file/directory permissions.  If you do, then it makes perfect sense.

Linux is like Unix and multi-user from the ground up.  This is different from that other popular OS. On Unix systems, file and directory permissions matter. They are the core for all system security.  There isn't any way to avoid learning about these things, sorry.

It isn't hard, if you apply yourself and just learn it.  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
Actually, Unix file permissions are quite elegant.   By default, new file systems are owned by root:root.  There are reasons for that.  Depending on the desired use for the storage, you might want to leave it that way and create subdirs to be used for different purposes and to have different owners and perhaps different groups in the permissions.  We don't have enough information to know.

If you just want it to work and don't care about security, use 777 permissions.

If you want to "do it right", think multi-user and layout the purposes for the storage with the specific userids and groups which need to own and which need write access to the different areas.  For backups, if the backups are at the system level, then root:root should be fine. Backups generally are performed with sudo/root, but it depends on how you are performing backups and which backup tools are being used.

With great power and great flexibility, comes some added complexity. That's the way of the world.

---

### Post by exploder on 2018-06-24
I am using a 240 GB SanDisk SSD as the drive for the OS. I want to use a 1 TB Toshiba SATA hard drive for music, backing up data, music and videos. I need to be able to create folders, copy files, play music and videos, etc.

---

### Post by oldfred on 2018-06-24
It is my understanding that this is the same as /home defaults.

fred@bionic-z97:~$ sudo chmod  a+rwX,o-w temp.txt
fred@bionic-z97:~$ ll t*
-rw-rw-r-- 1 fred fred 0 Jun 24 22:39 temp.txt

a means all or owner, group & other and then + means all get 
rw or read & write but big X excludes execute unless already executable
and o-w excludes write on other

[URL="https://help.ubuntu.com/community/FilePermissions"]https://help.ubuntu.com/community/FilePermissions
      [/URL] Seems like a better way as you have more control over what is executable. See post #8 & 10 by morbius1 on correcting oldfred's use of 777.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369) 

    [URL="https://help.ubuntu.com/community/FilePermissions"]
[/URL]

---

### Post by exploder on 2018-06-25
Thanks oldfred! I will try and put this all together as to how I can apply your instructions to my situation tonight after work. I get the basics of it but getting the drive mounted without breaking the system is still confusing me. In previous attempts I ended up with a system that would not boot up. You are right about having my permissions just like home, that is exactly what I want to do.:) I am probably making things way harder than they need to be trying to get my head around doing this from the command line.

---

### Post by TheFu on 2018-06-25
> **exploder said:**
> I am using a 240 GB SanDisk SSD as the drive for the OS. I want to use a 1 TB Toshiba SATA hard drive for music, backing up data, music and videos. I need to be able to create folders, copy files, play music and videos, etc.

Uses:
* Backup data
* Music/videos

I see these as 2 different purposes.

Music/videos should either be owned by your userid or by the media server on the system.  If you use plex, then "plex" is the userid that needs permissions to the level you desire.  That could be just read or it could be read & write & delete.  Just depends on how you manage the files.  I use kodi and plex together, but only Kodi can delete files in my setup. Plex cannot.  In my setup, I have 4775 permissions with thefu:kodi as the owner:group, but the group has the "setgid bit" set to ensure any new files retain the osmc group and permissions. My userid is a member of the "osmc" group.  If this is done on the initial top directory, then all new files and directories created/copied into the area will get those permissions and groups.

OSMC is just a special version of kodi designed to run on raspberry pi SBC devices. The default kodi userid is "osmc" for those installations. Whenever I say "kodi", it is really the OSMC userid, osmc.  

As for backups, root needs to be the owner.  Backups need to be run as root to handle all the different userids and permissions involved.  Normal users probably shouldn't have access - no access - to the storage used for backups, especially in a mixed house with novice users.  Backups usually contain sensitive data that we'd rather not allow the world to see. The top level directory would be 700 with root:root as the owner:group.

My personal files would have 770 permissions. thefu:thefu as the owner:group.

So, hopefully, this shows and explains some of the non-trivial methods for managing permissions.

Also, hopefully the reason that **sudo chmod -R a+rwX /media ** - effectively 777 - is wrong is clear.  When Oldfred added the ,o-w, that changed lots of important things.  

And I don't use 775 permissions on data files.  That is just an over simplification, which really means 775 for directories and 664 for files.  Files that cannot be run having execute permissions would drive me nuts, and might be a security risk, since someone could place a malicious file into those directories and trick someone with sudo access to run them.  For partitions purely with data, mounting with the noexec option can be smart.

And hopefully, I didn't make this so complex as to scare anyone off.

---

### Post by exploder on 2018-06-26
I figured out the auto mount for the 1 TB hard drive but I can not figure out how to set the permissions with the command line. Here is what I have.

```
/dev/sda1: UUID="2743507a-a645-4b4f-afc5-9c09e5662299" TYPE="ext4" PARTUUID="f099dbb1-01"
/dev/sdb1: UUID="4fdbe801-2579-42c8-a9c1-1881ab2c656c" TYPE="ext4" PARTUUID="a267e6de-01"

```

and

```
don@MSI-7641:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=2743507a-a645-4b4f-afc5-9c09e5662299 /               ext4     noatime,errors=remount-ro 0       1
UUID=4fdbe801-2579-42c8-a9c1-1881ab2c656c /mnt ext4 defaults 0 2
/swapfile                                 none            swap    sw              0       0

```

With my user name "don" what would the command be to set the permissions the same as my home folder? This is driving me insane...

---

### Post by oldfred on 2018-06-26
See post #3 except it looks like you used /mnt, not the /mnt/data I use.

TheFu suggests not to use /mnt at all and mount elsewhere. To his point, I have, in testing something used a /mnt default and that deleted (temporarily) my /mnt/data.

---

### Post by exploder on 2018-06-26
I still have absolutely no clue what to type in the terminal to be able to use my own hard drive. It would take 5 seconds to fix if KDE developers had not taken away root access to dolphin. I just want to use my hard drive.

---

### Post by oldfred on 2018-06-26
Did you look at post #3?
sudo chmod -R a+rwX,o-w /mnt/data
sudo chown -R $USER:$USER /mnt/data

Except yours is /mnt

UUID=4fdbe801-2579-42c8-a9c1-1881ab2c656c [COLOR=#ff0000]/mnt[/COLOR] ext4 defaults 0 2

sudo chmod -R a+rwX,o-w /mnt

sudo chown -R $USER:$USER /mnt

Note that -R is recursion, or every lower level file & folder is also changed. If just your data that is ok, but never run on system partition.
and make sure spacing is correct.  Some accidentally put a space between / & mnt and then destroy system as it runs on /.

---

### Post by exploder on 2018-06-26
Thank you! I can finally use my hard drive! Do you think the way I have it mount is alright?

---

### Post by oldfred on 2018-06-26
Everyone has their preferences. Yours is ok, but probably not what most of us use.

I also like to have multiple partitions on larger hard drives. Easier to backup, run fsck or other repairs, but does then require managing available space. I do not fill drives, so not an issue for me, normally.

---

### Post by TheFu on 2018-06-27
> **exploder said:**
> I still have absolutely no clue what to type in the terminal to be able to use my own hard drive. It would take 5 seconds to fix if KDE developers had not taken away root access to dolphin. I just want to use my hard drive.

Using root with a GUI is a security risk. There are other reasons not to allow it too.

But if you learn how to do admin things from a shell, they way things work almost never changes. For example, the file permissions using chmod have been the same for 40 yrs.  And over ssh, we can admin systems 5, 50, 500, 5000 miles away pretty much exactly the same.

GUIs seem to change every 3-5 yrs.  The shell is effectively the same today as it was in 1992, though a few things do necessarily change as problems are solved.

</soapbox>

As stated already, I'd make 2 subdirs - one for my stuff and the other for backups.  And I'd limit any partitions to 4TB in size.  4TB is large enough, but still a good size disk that can be cheaply purchased when one fails if the 8TB disks are too expensive that week.

---

