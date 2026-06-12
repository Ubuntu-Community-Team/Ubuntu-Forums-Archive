---
title: "Western Digital My Book read-only"
date: 2007-09-28
forum: Hardware &amp; Laptops
---

### Post by taz5005 on 2007-09-28
When I first got my WD My Book (500 gb) i copied a whole bunch of music to it from another external hard drive.  Now, I want to delete some of the stuff on there, but for some reason it's not letting me, saying it is a "read-only file system".  I don't know a whole bunch about file systems, but I'm pretty sure it shouldn't be a read-only, especially since I wrote the stuff on there in the first place.  I must've done something to it, but I don't know what.

It's a FAT32 file system.  

I tried going into "Permissions" when mounted and change it to "access files" and it says "cannot change permissions: read-only file system" 

So I added the option "-w" to the mounting commands and now it won't mount at all because of improper options.

Help?

---

### Post by peabody on 2007-09-28
I take it that it's a partition on which you haven't installed ubuntu?  To my knowledge I think there needs to be a umask argument applied to the mount options in the /etc/fstab (or mount command).  I'll try to find something.

---

### Post by fdrake on 2007-09-28
i have the same external usb hard drive as yours. what i did is i format the disk in ext3 file system and then change my fstab config file. can you post here your mount output?

---

### Post by taz5005 on 2007-09-29
@peabody: No I haven't installed anything else on the partition in the external hard drive.

@fdrake: What do you mean post my mount output?  I can tell you what I type in to mount the drive:

```
sudo mount -t vfat /dev/sda1 /mnt/MyBook -w

```

It mounts when I do that.

I wouldn't know how to format the disk to ext3.  And what would be the pros/cons of formatting it into that type of file system?

I can get all the stuff that's on my external again even if I did reformat it though.

---

### Post by fdrake on 2007-09-29
just time "mount" and see how it is being mounted.
Did you copy those files with another previous installation? 
did you try to change the ownership?type:
sudo chown <you_username> -R /mnt/MyBook/*
sudo chmod 755 <your_username> -R /mnt/MyBook/*

---

### Post by taz5005 on 2007-09-30
Output of "mount":
```
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-386/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/My Book type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

```

I moved all the music to the hard drive under the same install.

I tried the chown and (although the chown was successful) it didn't do anything. 

I tried the chmod and it didn't work...formatting error for the code...I dunno how to fix it, I tried to read the man pages but I couldn't make sense of them.  I'm pretty sure I'm fine with just reformatting, which would be a quick(?) fix, but it wouldn't really get at the heart of the problem.

So any other suggestions would be great.

---

### Post by peabody on 2007-10-01
Have you tried mounting with the mode=0777 option?

---

### Post by taz5005 on 2007-10-01
No...I wouldn't know how...???

---

### Post by peabody on 2007-10-01
sudo mount -t vfat -o mode=0777 /dev/partition_goes_here /mount/point/goes/here

---

### Post by taz5005 on 2007-10-01
```
sudo mount -t vfat -o mode=0777 /dev/sda /mnt/MyBook/

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```


```
david@...$ dmesg | tail
[84215.546361] FAT: Filesystem panic (dev sda1)
[84215.546364]     fat_get_cluster: invalid cluster chain (i_pos 0)
[84215.547107] FAT: Filesystem panic (dev sda1)
[84215.547109]     fat_get_cluster: invalid cluster chain (i_pos 0)
[84215.547856] FAT: Filesystem panic (dev sda1)
[84215.547859]     fat_get_cluster: invalid cluster chain (i_pos 0)
[84215.548606] FAT: Filesystem panic (dev sda1)
[84215.548608]     fat_get_cluster: invalid cluster chain (i_pos 0)
[84215.549356] FAT: Filesystem panic (dev sda1)
[84215.549358]     fat_get_cluster: invalid cluster chain (i_pos 0)

```

Uh Oh...Panics aren't good, right?

---

### Post by taisao on 2007-10-15
I don't know much about this, but here is a suggestion: 

Put this line
```

/dev/sda1 /mnt/MyBook vfat defaults,locale=en_US.UTF-8 0 0
```

in yours fstab file ( /etc/fstab )

and when you want to mount use this command in the terminal:
```
sudo mount -a
```

---

### Post by wheredidrealitygo on 2007-10-15
> sudo mount -t vfat -o mode=0777 /dev/sda /mnt/MyBook/

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

you forgot something in that line, it should be 

```
sudo mount -t vfat -o mode=0777 /dev/sda[COLOR="Blue"]1[/COLOR] /mnt/MyBook/
```

---

### Post by saj0577 on 2008-05-28
Still not working :(

Saj

---

