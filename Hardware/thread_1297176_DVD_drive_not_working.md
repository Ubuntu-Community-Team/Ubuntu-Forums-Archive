---
title: "DVD drive not working"
date: 2009-10-21
forum: Hardware
---

### Post by ubuntave on 2009-10-21
Hi gang. Noob with questoins here. I have been doing extensive searching on these forums to solve my issue. I can do certain things with my DVD drive currently, but not mount. I have found postings that have solved this issue for some and not others. 
 
So far I am in the "others" category.
 
Before I start posting my Fstabs and such (I am still getting used to commands) I want to list a little of what is going on.
 
1.) I can use the Eject command and eject the drive through the terminal
2.) I can get a no Mount point error
3.) I have run a command or two to audit my system, and my drive does show up in the command.
 
I guess my initial queston is this:
 
Does it matter if the drive is set to cable select, slave or master? I am only using one drive, and one hard drive. 
 
Does the Master/Slave/CS matter at all? I believe I am set to Cable select.
 
I KNOW this drive is not broken. It is new and I installed Ubuntu with it. When in Ubuntu, however, can't read an instered disk. Yes I have tried a few different disks.
 
Thanks! I am sure this is my first of many posts.

---

### Post by ajgreeny on 2009-10-21
It would certainly be worth posting your /etc/fstab file with ```
cat /etc/fstab
```, and also the output of ```
ls /media
```to see if there is an entry for the cd/dvd drive, and also to see if there is a folder for it to mount to in /media.

---

### Post by ubuntave on 2009-10-21
I can do that, although I was hoping you could clarify:

What does the fstab file do?

What is the "cat" command?


Here are my results - thank you!
#####################

super@super-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=294aa519-e2ba-43a7-aaf5-19ac72ef6e5b /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=bf3b610c-ece8-4456-9554-3b8250b968e8 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
super@super-desktop:~$ ls /media
cdrom  cdrom0  disk  floppy  floppy0  HP v125w
super@super-desktop:~$ 

#####
THis is a DVD drive, is it supposed to be referenced as a cdrom?

---

### Post by 00ber n00b on 2009-10-21
Are you using Karmic?

---

### Post by ubuntave on 2009-10-21
Tried adjusting the Drive to CS, Slave, or Master. None work. 

If I navigate to Places > Computer and try to access the DVD drive icon, I receive the "Unable to mount Location - there is no media in the drive" error.

There is media in the drive. Have tried different disks.

The disks I tried were widows based and the install cd for ubuntu. I can boot up from the disk, but can't access the drive if I try to access through the OS.

A little frustrating, but this will be killer when I get it working.

---

### Post by ubuntave on 2009-10-21
I do not know what KArmic is, but I am using the latest version of Ubuntu, 9.04

---

### Post by ajgreeny on 2009-10-22
Not sure what is going on but the output from those two commands is more or less exactly as it should be, so I'm baffled.

For your information, the cat command just displays the contents of a file.  If it's plain text it shows that, if it's a binary it just shows gobbledegook, but it will do no harm.  To see what a command does use ```
man command
``` in a terminal and the manual will appear.

Look here for more quick info.
[http://ss64.com/bash/](http://ss64.com/bash/)

---

### Post by ubuntave on 2009-10-22
Thank you for the command list. That will be useful. This seems to be a fairly large  hurdle to ovecome.. at least I get to practice some commands.

---

### Post by ubuntave on 2009-10-23
Would it make sense for me to reinstall the OS? I haven't done too much with the system yet so I wouldn't be rolling back that far. 
 
It did take me a few tries to install the system to start.... perhaps there was some corruption or incorrect initialization?
 
Make sense?

---

### Post by danfromakron on 2009-10-23
It's not just you. I am having the identical problem. I installed ubuntu 9.04 on my desktop from a DVD. I know that the drive is physically all right because it ran from the BIOS, the system booted from the DVD drive and the drive worked perfectly until after installation was complete.

The DVD drive initially showed on my desktop until I tried to access it.  Then I got the "spinning wheel" or whatever it is for a while and then that stopped and the icon for the drive was gone - all without ever accessing the drive. 

Thereafter, I could find the drive in my "places" but when I tried to access it I received an error message that it couldn't mount the drive.

This is all rather frustrating because ubuntu works perfectly on my Asus 901 netbook and functions properly with all USB peripherals including stand beside DVD drives and hard drives.

---

### Post by ubuntave on 2009-10-23
I'm still a noob, of course, but it's like having a crazy puzzle that will have a huge payoff when it's complete. I am totally into this... I just can't work with WINE unless I get the drive running.
 
It automatically mounts my Flash drive when I plug it in... I just can't mount that dvd drive. Bummer. But still cool. I will install the OS again.. it is a relatively fast install

---

### Post by danfromakron on 2009-10-25
Problem solved!  I just installed 9.10 beta and it runs perfectly, including it recognizes and runs the dvd drive.

---

### Post by ubuntave on 2009-10-26
I pulled the drive, made some adjustments.... then plugged a differnet drive in and it worked?
 
Strange. Very strange. 
 
But I will take it! Thanks for the advice gang.

---

### Post by kleewyck on 2009-12-17
Hello,

I am a rank beginner at Ubuntu.  I have an old Dell Precision 380 desktop.  It came with just a CD rom drive.  I have added a Samsung DVD RW drive, but on startup my system does not acknowledge it.  I ran the same command as the original poster on this thread and these are the results:

laureen@laureen-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=8cbe1581-ad64-4294-a198-bb3c0be6b93d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f08653b3-6a47-4689-a835-575a6c7783a4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
laureen@laureen-desktop:~$ ls /media
cdrom  cdrom0  floppy  floppy0
laureen@laureen-desktop:~$ 


so the system sees my cdrom and floppy drives.  How do I get it to recognize the new dvd drive?

Thanks for any advice.

---

### Post by chuina on 2009-12-17
> **kleewyck said:**
> Hello,

I am a rank beginner at Ubuntu.  I have an old Dell Precision 380 desktop.  It came with just a CD rom drive.  I have added a Samsung DVD RW drive, but on startup my system does not acknowledge it.  I ran the same command as the original poster on this thread and these are the results:

laureen@laureen-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=8cbe1581-ad64-4294-a198-bb3c0be6b93d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f08653b3-6a47-4689-a835-575a6c7783a4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
laureen@laureen-desktop:~$ ls /media
cdrom  cdrom0  floppy  floppy0
laureen@laureen-desktop:~$ 


so the system sees my cdrom and floppy drives.  How do I get it to recognize the new dvd drive?

Thanks for any advice.

Insert a disk into the drive then use this command:

```
sudo mount
```

it will show all of mounted partitions,CD/DVD,USB etc. data devices...

---

### Post by unknown23 on 2009-12-28
i am a noob

i installed karmic and now my dvd drive does not work

how can i fix this?


shadowcast@shadowcast:~$ sudo mount
[sudo] password for shadowcast: 
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/shadowcast/.Private on /home/shadowcast type ecryptfs (ecryptfs_sig=085787dc01f81ea9,ecryptfs_fnek_sig=fe882ef77d9b2865,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/shadowcast/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=shadowcast)
shadowcast@shadowcast:~$ 

:(

---

