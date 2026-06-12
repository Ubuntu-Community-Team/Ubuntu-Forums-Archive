---
title: "Non believer so far"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by beanoil on 2009-04-08
Hello to all. First post, but many years of experience with PC's and thousands of windows loads, Redhat, Linspire, Solaris, MS-DOS, IBM PC-DOS and every version of Windows from 3.1 on up.  Wish I could say I was typing this while using Firefox.. I can't. Short story, brother in law allows someone to use his computer. Said person manages to take a smooth running win2k pro install to it's knees in about a half hour by surfing where he shouldn't. I figure W2K is getting long in the tooth, so after hearing about Ubuntu, I figure I'll give it a go. ASUS P3B-F, 512 ram, P3 700, Western 20 gig. Nothing special. I download 8.04, and use Nero to make an image disk on my WXP pro box.
  Ubuntu 8.04 runs fine from the live cd but it will not install. The partitioner never populates the window, as if it does not see the hard drive. Running 8.04 from the cd, the partitioner does not populate either. I read a few entries about a bug in the partitioner that is fixed. I try Linspire... loads right up, I'm running in about 40 minutes. Same with W2K, same with a corp version of XP just to try. So the hardware is good, at least for those software combos.
  So I grabbed 8.10... It will not run from the cd and acts very differently from 8.04. There is never a text line indicating loading a linux shell when using the cd. If an attempt to install is made, it appears to install, including the patitioner seeing the drive and displaying the current partitions. It grinds for about 45 minutes or so, appearing to load. However, upon reboot, it displays the splash for about 40-50 seconds, and drops out to ALERT! /dev/disk/by-uuid XXXXXXXXX does not exist. Dropping to a shell!
Busybox gives me (initramfs) with a flashing cursor. 
So to say I'm not real impressed so far would be close. I'd like to give UBUNTU a whirl, but I cannot in good conscience install this for a novice user if I cant get it to run myself. I will say however, that of all the linux versions I have seen and touched, this is by far the nicest GUI and slickest looking. Now if I can just get it to run.... Any suggestions as to what to edit the command line to read to get 8.10 to boot ?

---

### Post by upchucky on 2009-04-08
boot from the 8.10 live cd, then download this,

[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055) 

then open a terminal click applications > Accessories > Terminal

then do this,

```
sudo bash ~/Desktop/boot_info_script*.sh
```

post the file this creates here and there are some that can tell you exactly what to do to make it boot.

also supergrub will get it up and running. 

Grub = Grand Unified Bootloader it will boot just about any os out there but needs the proper information to set up right.


Supergrub

Get Supergrub to set up/repair Grub here:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

after you have downloaded and created the supergrub disk boot from it then use it to fix grub.

you must read the instructions carefully and understand them, google what you do not understand. You will not hurt anything with this but can get very confused if you do not understand what it does.

be forewarned that depending on the machine specs the graphical display may need to be set up manually, we can tackle that after we get the machine booting if it becomes an issue.

the reason that things seem to not function as anyone would like is because of the many different machine specs out there, Linux must be configured specifically for each different machine spec. to design Linux to be able to automatically set up on each and every machine out there would create the super bloat os that windows is, thus negating the ability of linux to be a lean mean powerful os. and also stop it from running on the simplest of hardware.

---

### Post by beanoil on 2009-04-08
Thank you for the direction. I'll get on that little project tomorrow... Gotta go to work now. Very pleasant work, and grateful to have job though. Good day.

---

### Post by beanoil on 2009-04-08
Here we go  Looks like I'm not seeing the hard drive  
============================= Boot Info Summary: ==============================


=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

---

### Post by ronparent on 2009-04-08
In a terminal type:

sudo sfdisk -l

This should find a hardrive and tell us it's status.

---

### Post by beanoil on 2009-04-10
4 days.. I'm giving up on Ubuntu. I have loaded this at least a dozen times in various ways and configurations. I swapped to a different hard drive. I have tried a second HP platform. All the results are the same. 8.10 appears to load but it will never boot into Ubuntu from the hard drive. I downloaded a grub editor and have worn the tips of my fingers off with mouse clicks and command lines. I'm done. Frankly, I have never loaded a piece of software including too many Solaris loads to count, that was as bad or as immature as this. One of the basic tools of software is that it knows where it loads, and notifies the directory or registry. This doesn't. Really too bad.. it's a slick GUI. Congrats to all who are using it.

---

