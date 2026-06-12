---
title: "What is that device I never noticed before?"
date: 2008-11-10
forum: General Help
---

### Post by svaens on 2008-11-10
Hi all, 

Not been using linux very long. But i'm getting by. 
got Hardy fresh install on my laptop, and been using it no problems. 

For some reason never noticed this before, but when I click on the 'places' drop down menu, I have this 1,3 GB Media entry. 
When I click on that menu item, ubuntu mounts this device 'sda1 according to what I see in the system monitor' as /media/disk

When I use the 'mount' command, i see the following entries:
```

sean@svUbuntuX:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw,errors=remount-ro)
/dev/sda2 on /mnt/virtualizations type ext3 (rw,errors=remount-ro)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/sean/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sean)
/dev/sda1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
```


And there it is, sda1 on /media/disk, type ext3 etc etc. 

Thing is, it is not in my fstab file, so how did it get there, why is it there apparently taking up 1,3 GB of space?



My fstab file:
```
sean@svUbuntuX:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=8e58c507-b42f-432f-8d75-aff0602b74c3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=02f58d1f-4509-4207-a2db-0ee14a5aff6b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda3 /home ext3 defaults,errors=remount-ro 0 1
/dev/sda2 /mnt/virtualizations ext3 defaults,errors=remount-ro 0 1

```

Anyone know why it is there?

Thanks in advance!

---

### Post by phidia on 2008-11-10
Since it looks like it's part of your primary drive which is sda I'd say it's a partition of that drive. I don't know why it's showing in that mountpoint.

From a terminal what does "sudo fdisk -l" output?

---

### Post by fragos on 2008-11-10
The purpose of fstab is to mount the partitions you use with a particular distribution. Partitions beyond those in fstab aren't mounted by default. You may add them to fstab if you wish but that'ws not really necessary since nautilus shows they exist and will mount them for you.

---

### Post by night_fox on 2008-11-10
Use "Partition Editor" in administration to see if you have any random bits of unused disk space.

---

### Post by hansdown on 2008-11-10
Hi svaens.

Do you have a thumb drive, or other usb device connected?

Double click on it and see what pops up.

---

### Post by svaens on 2008-11-11
Hi all, and thanks for the help!

By the way, it seems to be that I don't have permission to write to this one (probably I would as root, but since i don't know what it is for, i haven't tried). 

@phidia -  here is the output from fdisk -l

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         158     1269103+  83  Linux
/dev/sda2           14350       19457    41030010   83  Linux
/dev/sda3            8173       14349    49616752+  83  Linux
/dev/sda4             159        8172    64372455    5  Extended
/dev/sda5             159        7839    61697601   83  Linux
/dev/sda6            7840        8172     2674791   82  Linux swap / Solaris

Partition table entries are not in disk order


@hansdown - hi.... no, I have no usb drive connected... And I can't really remember that I have one (had one) this size that somehow the device is remembered even when it is no longer plugged in.... 

But if you look at the table above, it definitely looks like part of the main disk. An extra partition. Which is what I expected. 
But it is not the swap. Because we can see the swap is that /dev/sda6.

I also think it is no coincidence it is in the first blocks. 

Is this where Grub is installed maybe? It's own partition in the first blocks? 

If so, ok. But why does ubuntu show it in places as an extra location I should be able to open and use? And if this is the answer, how do I remove it from 'places' ?

---

### Post by fragos on 2008-11-11
A default Ubuntu install only has two partitions. One for swap and the other with everything else. Linux allows installation accross a number of partitions. Dell computers with Ubuntu preinstalled add two additional partitions, one with system test functions and another with all the debs used in a new install.

---

### Post by svaens on 2008-11-11
well... I of course created the partitions for a couple of specific things, like my virtual machines, and the home directory. But There's no way i intended on creating a useless sized 1.2 Gig partition.... for what? No.. i'm quite sure I didn't create that. ... 

In any case..... if no one thinks it could be used by the system somehow...... 
Then I could try and delete it and merge the sapce it into sda2. My only worry is that it is 'required' somehow.. hmmmm..... But you say 'not' eh fragos?

---

### Post by Rinzwind on 2008-11-11
Could it be a partition your hardware supplier used to store a backup for Windows?  Dell does this too with their utility's CD. 

But both of those partitions generally also have a 'label' telling you that it is such a partition.

I say delete it >:) Damn the consequences :D

---

### Post by svaens on 2008-11-11
but geez!!! ... it can't be windoz left overs or left overs from the original OS on this toshiba at all.... it is after all an ext3 partition. 
Have a look at the pic! (see attachment) It is even flagged 'boot'.... 

Isn't there someone who's going to tell me I shouldn't delete this partition?

---

### Post by fragos on 2008-11-11
> **svaens said:**
> but geez!!! ... it can't be windoz left overs or left overs from the original OS on this toshiba at all.... it is after all an ext3 partition. 
Have a look at the pic! (see attachment) It is even flagged 'boot'.... 

Isn't there someone who's going to tell me I shouldn't delete this partition?

That partition is marked as the one to boot from. I wouldn't recommend deleteing it. It probably a throwback to a previous install. Normaly that would be your swap partition which is used for the initial boot to the /boot/grub/menu.lst of your last distribution install where you probably elected not to reuse your old swap partition. At some point you should do a clean install to the entire drive. It will do no harm as it is.

---

