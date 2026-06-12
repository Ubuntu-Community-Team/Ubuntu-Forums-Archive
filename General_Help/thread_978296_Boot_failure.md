---
title: "Boot failure"
date: 2008-11-11
forum: General Help
---

### Post by Anandafit on 2008-11-11
Hi All,
  When I boot from the Ubuntu, it start boot normally. But unexpectedly it gives fallowing fail message with out completing process Ubuntu load process bar.

*File system check failed Log is being saved in /var/log/fsck/chekfs if that location is writable. please repair the file system manually.

*A maintenance shell will now be started 
CONTROL -> will terminate this shell and resume system boot.

bash: groups: command not found
bash: no job control in this shell
bash: less pipe: command not found
bash: command:command not found
bash: The: command not found
bash: dircolors: command not found
bash: command: command not found
bash: The: command not found
root@ananda-deshtop:~#

   When I firs time face this problem I had to reinstall system, but I can't do that type of thing this time. Is there  any one how face this problem? Help me!

Regards,
Ananda

---

### Post by Neo_The_User on 2008-11-11
What do you think might have caused this problem? Did you break anything or was it a fresh install? Oh and by the way, I recommend you stay with the command line for awhile and learn more about text commands rather than depending on a GUI. ;)

---

### Post by Herman on 2008-11-11
Have you used any hard disk partitioning software recently and made changes to any of your file systems?
If so, you may need to update /etc/fstab, (the file which tells Ubuntu how to treat each of your file systems).

Is there any chance your computer may have been improperly shut down recently?
If so, you may need to run a file system check.
To do that, boot your Ubuntu live CD, open Gnome Partition Editor, right-click on the partition to be checked, and click 'check', and then 'apply', and 'apply' again to confirm.

Neo_The_User is right too, you should be able to run a better file system check yourself from the command line, here's a link to a web page that should help, [File Systems and Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm").

Ask again in this thread if you still have trouble and someone around here will be able to help you more.
If you do still need help, please include a screencap from GParted (Gnome Partition Editor), or the output from 'sudo fdisk -lu', to help someone to be able to give you exact help.

---

### Post by walter_j on 2008-11-11
> **Anandafit said:**
> Hi All,
  When I boot from the Ubuntu, it start boot normally. But unexpectedly it gives fallowing fail message with out completing process Ubuntu load process bar.

*File system check failed Log is being saved in /var/log/fsck/chekfs if that location is writable. please repair the file system manually.

*A maintenance shell will now be started 
CONTROL -> will terminate this shell and resume system boot.

bash: groups: command not found
bash: no job control in this shell
bash: less pipe: command not found
bash: command:command not found
bash: The: command not found
bash: dircolors: command not found
bash: command: command not found
bash: The: command not found
root@ananda-deshtop:~#

   When I firs time face this problem I had to reinstall system, but I can't do that type of thing this time. Is there  any one how face this problem? Help me!

Regards,
Ananda

try running "fsck -p" at the command line. fsck checks the disk and corrects errors. I suspect your hd is failing (I had the same issue a few weeks ago). Backup your data if you get up and running again!

---

### Post by psusi on 2008-11-11
Yea, looks like the disk is fubar.  Maybe not physically but the filesystem is definitely hosed.

From the livecd you can run a diagnostic to see if the drive is physically bad:

sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
sudo smartctl -t long /dev/sda

The test will take some time to complete in the background.  You can check the results with:

sudo smartctl -l selftest /dev/sda

---

### Post by Anandafit on 2008-11-12
Thanks for all reply and I will try with your ideas. When I press ctrl+d it boot normally and comes to system login pages. Then I can work normaly with the system. But the problem is when I restart the machine it comes to same place that I had the problem and then press ctrl+d it comes to login and can work normally. 

  And also when i restart the machine it comes to that error page after another automatic restart.

---

### Post by psusi on 2008-11-12
Hrm... what does your /etc/fstab look like?  I wonder if it's trying to fsck something wrong.

---

### Post by Anandafit on 2008-11-13
Thanks for all, I fallowed Herman ideas. Now my system is worked properly.

---

### Post by physeetcosmo on 2009-02-10
> **psusi said:**
> Hrm... what does your /etc/fstab look like?  I wonder if it's trying to fsck something wrong.

All,

I am having a similar issue, but I am a noob and don't totally understand how to fix it.

To give some background:

1) I deleted a partition that wasn't used anymore and reallocated the space to a current partition. I used the RAMdisk Parted Magic thus not actually booting the OS to perform the maintenance.

2) I deleted an entry out of fstab as I was having issues formatting an SD card the was installed in my system.  It is currently NOT in the system now.

3) I had recently uninstalled VirtualBOX that I was testing out Fedora on (which doesn't work worth junk on the eeePC, great distro though  don't get me wrong!).

I am getting the same error as stated from the first person who started this thread.
Here is my fstab output, maybe I deleted a line by accident?:

```
dustin@SuperNIX:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5ef27f39-0890-46e9-8470-a087719da5aa /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=fbc17aaa-a97e-40ba-80a0-ea0aa5bc48cf /home           ext3    relatime        0       2

```

Also here is a screen shot of Gparted with the disk that is failing (/dev/sdb):
[IMG]http://2.bp.blogspot.com/_TXAD2LXLsjs/SZGZBvQI7ZI/AAAAAAAAAR0/Qo7R1RXBAe0/s1600-h/gparted.png[/IMG]
If this image doesn't come through I apologize, I'll explain what gparted shows. My partition /dev/sdb5 is mounted on /home as is concurrent with the fstab file. However there is another 'ghost' partition that covers the same amount of the physical disk that is labelled /dev/sdb1. Neither of these is my boot partition (which is /dev/sda1 as seen from fstab).

Here is the output from blkid:

dustin@SuperNIX:~$ blkid
/dev/sda1: UUID="5ef27f39-0890-46e9-8470-a087719da5aa" TYPE="ext3" 
/dev/sdb2: TYPE="swap" UUID="730d2020-87c3-41af-8c80-6f99f5a0084d" 
/dev/sdb5: UUID="fbc17aaa-a97e-40ba-80a0-ea0aa5bc48cf" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdc1: LABEL="Projects" UUID="7388c741-9a0d-4cc1-877b-33ca8e537899" TYPE="ext3" 
/dev/sdd1: LABEL="4GBDriveX" UUID="143063b5-7603-4845-9b64-9083a4431c33" TYPE="ext2" 
/dev/sde1: UUID="2E88F5C288F5891B" LABEL="DriveX" TYPE="ntfs" 
/dev/sdc: LABEL="Documents" UUID="ef13545d-e3cf-4754-988d-8140dc0d5e8d" SEC_TYPE="ext2" TYPE="ext3" 

Which I thought was the output of which disks are CURRENTLY connected to the system but not necessarily mounted anywhere. 

I am currently performing a:

```
$ sudo badblocks -v *disk*
```

on all of my system partitions, and /dev/sdb1 does not register ANY blocks available, so it IS a 'ghost' partition.

Kind of a strange thing going on here, can anyone help? :) :)

Thanks!

---

### Post by physeetcosmo on 2009-02-10
Here's a follow up, i successfully performed a complete badblocks and fsck scan on all my system partitions, here's the results:

```
dustin@SuperNIX:~$ sudo fsck -TV /dev/sda1
[/sbin/fsck.ext3 (1) -- /] fsck.ext3 /dev/sda1 
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sda1: recovering journal

Clearing orphaned inode 243011 (uid=1000, gid=1000, mode=0100600, size=28700)
/dev/sda1: clean, 153383/492880 files, 734206/1969962 blocks
[COLOR="Red"]dustin@SuperNIX:~$ sudo fsck -TV /dev/sdb1
[/sbin/fsck.ext2 (1) -- /dev/sdb1] fsck.ext2 /dev/sdb1 
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?[/COLOR]
dustin@SuperNIX:~$ sudo fsck -TV /dev/sdb5
[/sbin/fsck.ext3 (1) -- /home] fsck.ext3 /dev/sdb5 
e2fsck 1.41.3 (12-Oct-2008)
/dev/sdb5 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sdb5: recovering journal
/dev/sdb5: clean, 95233/1970416 files, 1469307/7879866 blocks
```

Notice that the scan of the /dev/sdb1 partition indicates that it IS a 'ghost' partition, is this normal? Here are the results from badblocks scan:
```
dustin@SuperNIX:~$ sudo badblocks -v /dev/sda1
Checking blocks 0 to 7879850
Checking for bad blocks (read-only test): done                                
Pass completed, 0 bad blocks found.

dustin@SuperNIX:~$ sudo badblocks -v /dev/sdb1
[sudo] password for dustin: 
Checking blocks 0 to 0
Checking for bad blocks (read-only test): done                                
Pass completed, 0 bad blocks found.

dustin@SuperNIX:~$ sudo badblocks -v /dev/sdb5
Checking blocks 0 to 31519466
Checking for bad blocks (read-only test): done                                
Pass completed, 0 bad blocks found.
```

Thanks for all your help! :)

---

### Post by Herman on 2009-02-11
:-k  Hmmm, sorry for the late reply.
It's too late now, but I have to remind you that you should never run a file system check on a file system while it's mounted, however, you did read the warnings and obviously have decided to proceed anyway.

It might not be too late yet though, probably you can still run a file system check from your  Parted Magic USB disk, to do that, boot your Partition Magic USB disk, open GParted, right-click on the partition to be checked, and click 'check', and then 'apply', and 'apply' again to confirm.
Parted Magic doesn't mount your partitions, (unless you command it to), so it is safe to run a file system check with Parted Magic.

It looks to me as if your /etc/fstab is okay, except if the swap area is really missing from it, you might want to add the lines for one.

If you need more details, please don't be afraid to ask, and I'll try to reply as soon as I get time, unless someone else can help you sooner.

---

### Post by physeetcosmo on 2009-02-11
> **Herman said:**
> :-k  Hmmm, sorry for the late reply.
It's too late now, but I have to remind you that you should never run a file system check on a file system while it's mounted, however, you did read the warnings and obviously have decided to proceed anyway.

It might not be too late yet though, probably you can still run a file system check from your  Parted Magic USB disk, to do that, boot your Partition Magic USB disk, open GParted, right-click on the partition to be checked, and click 'check', and then 'apply', and 'apply' again to confirm.
Parted Magic doesn't mount your partitions, (unless you command it to), so it is safe to run a file system check with Parted Magic.

It looks to me as if your /etc/fstab is okay, except if the swap area is really missing from it, you might want to add the lines for one.

If you need more details, please don't be afraid to ask, and I'll try to reply as soon as I get time, unless someone else can help you sooner.

Herman,

No worries about reply time :) I have found if I'm going to run Nix i sometimes have to take chances and have to be independent! :)

I found that my blkid cache was screwed, which I guess is where the fsck on bootup looks to define which devices to check. So, although I had only two partitions listed in fstab, there was that whole list of devices still in the blkid cache.

I used the following to cleanup the cache:
```
$ sudo blkid -g
```
The -g is a 'garbage collector' which removes all entries of disks that no longer exist. During bootup there was no more problems during file system check.

Thanks for the parted magic advice, I didn't know how to check the partitions from inside the RAMdisk application. :)

---

### Post by Herman on 2009-02-11
:) Okay, I'm happy for you and glad you have things working properly again.

The /etc/fstab file controls which file systems will be checked automatically during each boot-up as far as I know, unless developers have recently changed things and this is the first time I've heard of it.  
Thanks for sharing your information, if I read of something like this again I'll start to re-think my assumptions. It's always possible that something new has happened and I don't know about it yet, it wouldn't be the first time that has happened to me. I might easily be wrong. 

Regards, Herman :)

---

