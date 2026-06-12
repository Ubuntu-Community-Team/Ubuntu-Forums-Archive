---
title: "Copying Files From XP To Ubuntu"
date: 2008-08-30
forum: General Help
---

### Post by 3DGE on 2008-08-30
I wanted to know how can I copy my files that are on XP Like my Music, Pictures, Videos etc.. Onto Ubuntu when I used the Live CD I could go on my main C drive and look at everything that was on XP. Now that I have installed Ubuntu on my hard drive I cannot. 

Could someone please help.

---

### Post by tamoneya on 2008-08-30
well hopefully you didnt install ubuntu over your windows install (this would include your media files).  Lets take a look by running this command:```
sudo fdisk -l
```

This command should be run in terminal (applications -> accessories -> terminal)

---

### Post by 3DGE on 2008-08-30
After I did that I get this and no I didn't format My hardrive I just installed Ubuntu on it with XP. When I boot up the computer I can choose between XP Or Ubuntu.

Disk /dev/sda: 60.4 GB, 60496236544 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbad1bad1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2490    20000893+   7  HPFS/NTFS



What now?

---

### Post by Pro-reason on 2008-08-30
Fdisk is indicating that you have only one partition on your machine.  Generally this means that you have only one operating system, but I suppose you must have installed Ubuntu on to a filesystem contained within a file on your XP installation.

You can boot into each system without problems, right?

---

### Post by 3DGE on 2008-08-30
Yepp both XP And Ubuntu work fine and once I go onto XP all my Documents and Programs are still there and work, I just want to get them over to Ubuntu because I get bored without anything on Ubuntu.

---

### Post by tamoneya on 2008-08-30
yeah i dont exactly see where you have installed ubuntu.  But anyways this is how you could get to your files.  The process is called mounting.
```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/sda1 /media/windows
```

This more or less sets C:/ to /media/windows/

If that doesnt work can we see this output:```
mount
```

---

### Post by 3DGE on 2008-08-30
When I put in the first code I got   mkdir: cannot create directory `/media/windows': File exists

The Second One I Got 
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


And Then The Last One 

 /host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/jason/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jason

This is harder then I thought.

---

### Post by tamoneya on 2008-08-30
for the first command we can ignore it.  I was just being explicit.  If the directory already exists you can now ignore that command.  For the second command it almost looks as if there was a typo or something.  Some sort of syntax error.  Can you copy the section where it shows what you typed in as well?

Looking at the last command it doesnt tell us anything to do with windows but it satisfies my curiosity.   I was rather suprised not to see the ubuntu partition in sudo fdisk -l.  Looking at the device path I can now see that you are using wubi and it all makes sense now.

---

### Post by 3DGE on 2008-08-30
Here is the second one again this time I got a lot more stuff.

jason@jason-desktop:~$ sudo mount -t ntfs /dev/sdal/media/windows
[sudo] password for jason: 
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
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
jason@jason-desktop:~$ 


And about using Wubi I don't think I am because I installed Ubuntu onto my computer on the same hardrive and it is not an application in windows but I dont know maybe I am wrong.

---

### Post by tamoneya on 2008-08-30
okay i see the problem.  You need to make sure you have a space between /dev/sda1 and /media/windows

---

### Post by 3DGE on 2008-08-30
Ok heres what I get now.

jason@jason-desktop:~$ sudo mount -t ntfs /dev/sdal /media/windows
[sudo] password for jason: 
ntfs-3g: Failed to access volume '/dev/sdal': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.
jason@jason-desktop:~$ 


I don't know if that would help.

---

### Post by Pro-reason on 2008-08-31
> **3DGE said:**
> Ok heres what I get now.

jason@jason-desktop:~$ sudo mount -t ntfs /dev/sdal /media/windows
[sudo] password for jason: 
ntfs-3g: Failed to access volume '/dev/sdal': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.
jason@jason-desktop:~$ 


I don't know if that would help.

<Takes a deep, calming breath>

You have put an L instead of a 1.

It would be much better to copy-and-paste the command, rather than reading it and typing in something that looks similar to it.

---

