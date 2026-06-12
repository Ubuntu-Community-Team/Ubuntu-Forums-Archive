---
title: "Target Filesystem doesn't have /sbin/init"
date: 2006-07-26
forum: Hardware &amp; Laptops
---

### Post by CrimsonTider12 on 2006-07-26
Ok, it seems I am the eleventy-billionth person to have some variety of this problem.  When booting Ubuntu from hard disk, it gets hung up on "Mounting filesystem" and I eventually get the message:

Target Filesystem doesn't have /sbin/init

I sucessfully installed the Dapper Drake kernel (after much struggle), and everything seemed to be going fine until now.  Does anyone know what to do about this?  If not, I may be tempted to remove Ubuntu, because I simply do not have the time to deal with this.  I really do like Ubuntu, and I would love it if I could get it to work consistently.  Please, if I have left out something, let me know...I'm sure I have...

---

### Post by zxee on 2006-07-27
From the looks of it this seems like it could be a udev problem.
Take a look at this [http://www.linuxquestions.org/questions/showthread.php?t=446745](http://www.linuxquestions.org/questions/showthread.php?t=446745)
and specifically post #8 which suggests running a live cd and doing
> su -
mount -t ext3 -o rw /dev/hda1 /mnt
chroot /mnt
apt-get update; apt-get upgrade; apt-get install udev
Good luck and let the forum know how that works.

Note: If your ubuntu install is on a different partition than that shown above plug in your actual values. 
Oh and the linuxquestions thread is about debian so instead of su you need to do sudo for each command.

Therefore:

> 
sudo mount -t ext3 -o rw /dev/hda1 /mnt
sudo chroot /mnt
sudo apt-get update; apt-get upgrade; apt-get install udev

---

### Post by CrimsonTider12 on 2006-07-27
ubuntu@ubuntu:~$ sudo mount -t ext3 -o rw/dev/hdd1 /mnt
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

ubuntu@ubuntu:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': No such file or directory

ubuntu@ubuntu:~$ sudo apt-get update; apt-get upgrade; apt-get install udev
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release [34.8kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [40.4kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages [619kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [4275B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [9872B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [974B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages [4571B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources [255kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources [1478B]
Fetched 1002kB in 5s (189kB/s)
Reading package lists... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?



Well, by the looks of it, this hasn't worked.  However, I will reboot and see...

Nope, nothing has changed :sad:

---

### Post by zxee on 2006-07-28
omit the -t ext3 -o rw part of the command and try that.
e.g. just use the mount command with the device/partiton that the install is on. Report what happens back.

---

### Post by maxol on 2006-07-31
I had exactly the same problem so tried:> sudo mount -t ext3 -o rw /dev/hda1 /mnt
sudo chroot /mnt
sudo apt-get update; apt-get upgrade; apt-get install udevusing an old live CD as suggested.

It upgraded Firefox, Thunderbird and libfreetype6 but reported that udev was already the latest version.

Funny thing is when I rebooted everything worked again!

I'm using Xubuntu on a Dell C610 laptop.

---

### Post by Nelson-Ray on 2006-08-19
Im having the same problem...after doing the sudo apt-get upgrade...rebooted my server and it won't...when it gets to loading root filesystem I get an error messaging saying "target filesystem doesn't have /sbin/init" along with  messages. I am trying to use the dapper live installer to mount the drive but when I do 

sudo mount -t ext3 -o rw /dev/hda1 /mnt

I get this message wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I get the same message with sudo mount /dev/hda1 /mnt 

...help

---

### Post by gnowak on 2007-03-18
> **Nelson-Ray said:**
> 
I get the same message with sudo mount /dev/hda1 /mnt 

...help

Are you sure your system is on hda1?

Did you boot up on a live CD.. knoppix etc.?

---

### Post by Thibaud74 on 2007-07-08
Hi, 
I've got the same problem. I run the command chroot after mount, but I get :
chroot: cannot run command `/bin/bash`: Not a directory

Thanks for help,
Thibaud.

---

### Post by havanahjoe on 2008-03-19
I'm having this issue on my Gutsy install.

I don't know how it happened but after a reboot X wouldn't load.  I ran e2fsck and fsck and they found a lot of lost files, which were put under lost+found.

After that, I have been unable to boot Ubuntu from my HD again.  I've tried this solution but I can't get chroot to change my root to my root partition.

I get the "chroot: cannot run command `/bin/bash`: Not a directory" error.

I guess this is because my root partition is so messed up that I can't even chroot to it.  I don't know what are the minimum things needed for chroot to work.

Does anyone have any suggestions on how to get the system back?  How can I rebuild my root partition?  My /home is on a different partition so I should be able to just rebuild root and keep my settings right?

---

### Post by gnowak on 2008-03-19
Yes, be more specific about what you did. Which live cd /dvd did you use.. which steps did you use etc....

I can replicate your steps (kubuntu though) and tell you if I can chroot the way you did.. I can then explain how I chroot...

---

