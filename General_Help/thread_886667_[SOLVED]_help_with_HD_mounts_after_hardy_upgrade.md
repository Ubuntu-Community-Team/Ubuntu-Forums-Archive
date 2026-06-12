---
title: "[SOLVED] help with HD mounts after hardy upgrade"
date: 2008-08-11
forum: General Help
---

### Post by speed32219 on 2008-08-11
Up-graded to 8.04 server (Should have used LTE, server had to have desktop and stuff added to it)  and lost my hard drives auto mounting during boot. I have to manually mount them  by the folowing: 

**Cmd line manual mounts**
sudo mount /dev/sdd1 /media/Movies 
sudo mount /dev/sdb1 /media/Movies_2 
sudo mount /dev/sdc1 /media/Movies3 
sudo mount /dev/sde1 /media/Movies4

And all is fine in the Ubuntu world. But I am having problems setting them up to work at boot up, I have addded them to fstab below and created mount points in media also below.

**Output of cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5216fb37-d883-4675-9992-a0f0f69882c0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=3d4481f9-4c94-40e0-91fa-d9489b1a5393 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1	/media/disk-1	ext3	default		0	0
/dev/sdc1 	/media/disk-2	ext3	default		0	0
/dev/sdd1	/media/disk	ext3	default		0	0
/dev/sde1 	/media/disk-3	ext3	default		0	0

**ls /media (Mount points = disk, disk-1, disk-2, disk-3)**
cdrom  cdrom0  disk  disk-1  disk-2  disk-3  floppy  floppy0  

I am using Xbmc to as a front end to an HDTV with Ubuntu being the file server.  I would like to shorten the paths that I have to add to the Xbmc setup. (I.e. /media/disk/Movies to /media/Movies, Movies_2, Movies3, Movies4)

So when I tried to edit Fstab and add Movies4 instead of the disk-3 and create a mount point in /media/Movies4 and do the following error.

sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sde1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

So if someone could help me just get the darn drives to auto mount it would be greatly appreciated. I'm sure it is a problem with me from using dos/windows for so long.

---

### Post by logos34 on 2008-08-11
> **speed32219 said:**
> 
/dev/sdb1    /media/disk-1    ext3    default        0    0
/dev/sdc1     /media/disk-2    ext3    default        0    0
/dev/sdd1    /media/disk    ext3    default        0    0
/dev/sde1     /media/disk-3    ext3    default        0    0


option is wrong--you want 'default[COLOR=Red]**s**[/COLOR]'.  try that

---

### Post by speed32219 on 2008-08-11
Duh, Brain Fart, what can I say.

Thank you logos34, that did it.  Only took me 3 hours to install and 9 hours add'l to get it to work. Duh!

Now on to getting the Netgear MA101 wireless to work.  Took me awhile with edgy so I am looking forward to another day to be totally done with this for now until I get an HD graphics card, BD optical drive and HD tuner to compliment the Xbmc setup. Gotta find the time!

---

### Post by logos34 on 2008-08-11
good to hear it's fixed.

It's the simplest mistakes that can have you banging your head against the wall wondering what the problem is.  That was always my problem in calculus--I grasped the larger concepts and could derive and transform just fine...But on a test I would always screw up an equation and get the wrong answer at the very end, making a simple addition error!! :(

---

