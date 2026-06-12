---
title: "In Over My Head a Little on Ownership &amp; Permissions"
date: 2011-11-28
forum: Hardware
---

### Post by Curbuntu on 2011-11-28
I have created a file/folders ownership/permission problem that I’m pretty certain can be solved with one recursive chmod command from the terminal.  But I’m not comfortable enough with chmod and some of its concepts, so I thought I’d check in here with the experts.
 
Situation: I have needed to upgrade my laptop’s two 320 Gb hard drives to two 750 Gb drives.  The laptop is running Ubuntu 10.04 64-bit.  However, I forgot that I installed the second hard drive (sdb under Linux) back when it was a Vista machine, and that I had failed to change the file-format to Ext4 when the machine switched over fully; thus sdb has always been an NTFS-formatted drive.
 
 Here’s what I did for the upgrade:
 
 
[LIST=1]
[*]Temporarily swapped out the     current sda 320 Gb (three partitions – /, home, swap) for the 750 Gb which would ultimately become the new sdb.
[*]Booted from a Live Gparted disk, partitioning and formatting (Ext4) the new drive into two approximately equal partitions.  (I created two because I figured,  correctly, that Clonezilla would overwrite the target partition as     NTFS.)
[*]Booted from a Clonezilla CD and copied the NTFS partition (all of sdb) to the temporary sda1 partition, cloning the NTFS partition on to the new drive.  (FWIW,  Clonezilla cloned 298.7 Gb in about 106 minutes.)
[*]Booted from a live 10.04 disk and cp’d everything from sda1 (NTFS) to sda2 (Ext4).  I had to do this cp in terminal as sudo su, because I didn’ t have permission to copy the files as the default user in the GUI.
[*]Used Gparted to wipe out the NTFS partition (sda1), then “grew” sda2 to take up the entire drive capacity.
[*]Pulled out the original 320 Gb sdb, swapped in the the new 750 Gb sdb (which had been the temporary sda during the cloning process), then swapped in the original sda (/, home, swap) to its rightful position.
[/LIST]
 Everything works okay, except now I have permissions for none of the files on the new sdb.  All the folders (based on x'ed-over folder icons I can see) and files are there (based on how much of the new drive remains available).
 
 Am I correct in assuming that one recursive chmod command can fix this for me, and if so, how should the command be structured?
 
 BTW, if I have to repeat the cloning process because I botched things too badly, I haven’t altered anything on the original 320 Gb sdb HDD.

Thanks in advance.

---

### Post by oldfred on 2011-11-28
The minute you copied to NTFS you lost all ownership & permissions. But most of the system has to be root and /home has to be you. Not sure about permission of most root files. But some of the system has other settings to run things. 

When I first installed Ubuntu I did start a recursive change from root to fred & managed to stop it before too much damage. I did change back and it kinda worked, but ended up reinstalling as things never were totally correct.

Ubuntu /home is permissive:
[https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access](https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access)

this should work for /home but you may have to run after changing / as I do not know enough of / & details other than one massive change of everything.

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name or use $USER
sudo chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username:username /home/username     
chmod 755 /home/username

.dmrc errors- drs305
[http://ubuntuforums.org/showthread.php?p=6161267](http://ubuntuforums.org/showthread.php?p=6161267)
.ICEauthority errors
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)
sudo chown $USER:$USER /home/username/.ICEauthority
sudo chmod 644 /home/username/.ICEauthority
sudo chmod 644 $HOME/.ICEauthority
look at the permissions on ~/.Xauthority, too. It often gets changed when ~/.ICEauthority gets changed. The same fix applies.

Note the different permission from root, a few are my files (thats where they went:) ) which you can ignore and many are 
drwxr-xr-x 
```
fred@fred-MavericDT:/$ ls -l
total 136
drwxr-xr-x   2 root root  4096 2011-10-19 10:02 bin
drwxr-xr-x   3 root root  4096 2011-11-21 10:53 boot
drwxr-xr-x   2 root root  4096 2010-10-11 14:43 cdrom
drwxr-xr-x  17 root root  4740 2011-11-28 17:49 dev
drwxr-xr-x 172 root root 12288 2011-11-28 14:19 etc
drwxr-xr-x   2 root root  4096 2010-10-26 15:36 grub12
drwxr-xr-x   3 root root  4096 2010-10-11 14:44 home
lrwxrwxrwx   1 root root    33 2011-11-21 10:53 initrd.img -> boot/initrd.img-2.6.35-31-generic
lrwxrwxrwx   1 root root    33 2011-06-28 10:18 initrd.img.old -> boot/initrd.img-2.6.35-30-generic
drwxr-xr-x  17 root root 16384 2011-10-25 10:58 lib
drwxr-xr-x   4 root root 16384 2011-04-27 08:35 lib32
lrwxrwxrwx   1 root root     4 2010-10-11 14:42 lib64 -> /lib
drwx------   2 root root 16384 2010-10-11 14:41 lost+found
-rw-r--r--   1 root root   446 2011-08-26 12:08 mbrsda.bin
-rw-r--r--   1 root root   446 2011-08-26 12:08 mbrsdc.bin
drwxr-xr-x   6 root root  4096 2011-11-22 13:37 media
drwxr-xr-x  10 root root  4096 2011-08-09 22:53 mnt
drwxr-xr-x   2 root root  4096 2010-10-07 10:56 opt
dr-xr-xr-x 197 root root     0 2011-11-28 08:18 proc
drwx------  17 root root  4096 2011-11-20 14:27 root
drwxr-xr-x   2 root root 12288 2011-10-25 10:58 sbin
drwxr-xr-x   2 root root  4096 2010-05-10 00:45 selinux
drwxr-xr-x   3 root root  4096 2010-12-16 15:59 srv
drwxr-xr-x  13 root root     0 2011-11-28 08:18 sys
drwxrwxrwt  11 root root  4096 2011-11-28 22:39 tmp
drwxr-xr-x  11 root root  4096 2010-10-11 15:00 usr
drwxr-xr-x  16 root root  4096 2011-08-24 14:09 var
lrwxrwxrwx   1 root root    30 2011-11-21 10:53 vmlinuz -> boot/vmlinuz-2.6.35-31-generic
lrwxrwxrwx   1 root root    30 2011-06-28 10:18 vmlinuz.old -> boot/vmlinuz-2.6.35-30-generic



```

---

### Post by Curbuntu on 2011-11-29
Dear Fred,

Thanks for your quick reply.  But I'm left a bit bewlidered and wondered if you'd be so kind as to help me tie in what you said with my situation.

> **oldfred said:**
> The minute you copied to NTFS you lost all ownership & permissions. But most of the system has to be root and /home has to be you. Not sure about permission of most root files. But some of the system has other settings to run things. 

I'm not certain we're on the same page, but I acknowledge that could be due to my profound ignorance of the subject.  However, I want to point out:

1) I didn't copy TO NTFS.  sdb was NTFS from the get-go, as far as Ubuntu was concerned.  The files were quite readable/writeable in the original setup. In fact, after the clone job, all the files in the *new* NTFS partition were still quite accessible.  It was only after cp'ing the files to an EXT4 partition that they became "locked" to me.  That's why I thought the issue could be fixed with an as-yet-to-be-implemented recursive chmod command of some sort.

2) I haven't yet touched the original sda with its Linux root, home, and swap partitions; so root permissions on that drive aren't an issue.  (At least, at the moment!  The cloning of that drive will be attempted once I sort out this problem with ownership and permissions on sdb.)  I blew away everything related to MS Vista by letting Ubuntu take the whole drive 18 months ago.

I hope that makes it clear why your response befuddled me a bit.

Thanks!

---

### Post by oldfred on 2011-11-29
Are these just data files that were in NTFS and are now in ext4? But do not run -R parameter on any system folder.

I do this to mount my data partition, although after testing it is then in fstab.

sudo mkdir /mnt/data
sudo chmod 777 /mnt/data
sudo chown $USER:$USER /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
#if not known to list partitions
sudo fdisk -l

#If you cannot read and write then change the permissions. Not for NTFS
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
# 777 is read, write & execute by everyone
I just learned something - see post #8 & 10 by morbius1. Seems like a better way as you have more control over what is executable.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)
sudo chmod -R a+rwX /mnt/data 
#is better than this:
sudo chmod 777 /mnt/data

---

### Post by Curbuntu on 2011-11-29
> **oldfred said:**
> Are these just data files that were in NTFS and are now in ext4?

Yes.

---

### Post by oldfred on 2011-11-29
How are you mounting the partition?

If it is like my example above you then can run the chmod & chown commands with -R for that mount/path of a data partition only.

---

### Post by Curbuntu on 2011-11-29
OldFred,

This turned out to be far less difficult and less intimidating than I thought:

1) I dropped to the terminal and entered sudo so mode.
2) I did a chown -R name:name for each directory on the new drive.  (I realize I probably could have done this to /media/drivename, but then -R would have changed the root:root on the lost+found folder.)
3) cd'd to /media, then chown'd drivename (without the -R).
4) Changed the drive name in Disk Utility
5) Opened fstab and made the necessary changes so that the new drive is automounted (commenting out the lines pertaining to the old drive).

Everything seems to work fine!

Thank you!

---

