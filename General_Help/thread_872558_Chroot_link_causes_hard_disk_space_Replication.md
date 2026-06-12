---
title: "Chroot link causes hard disk space Replication"
date: 2008-07-28
forum: General Help
---

### Post by wefojoij on 2008-07-28
I am using Ubuntu 8.04 AMD64 with a 32-bit chroot Gutsy environment for legacy software testing and running 32-bit binaries.

My PC is reporting just under 1 GB of hard disk space available out of over 80 GB in the hard drive. I used disk space usage analyzer to figure out the problem. 

When the analysis was complete, I noticed the following issue: my home directory is linked to the chroot's home directory, so it is appearing as though the same memory is used twice for the same files! I have ~37.12 GB of /home/ and the same 37.12 GB is /var/chroot/gusty/home/. 

I need to resolve this issue as it have prevented me from storing any new information on the PC.

---

### Post by geirha on 2008-07-28
Are you sure you're not just using mount binding? what's the output of these commands:
```
mount
df -h /home /var/chroot/gutsy/home

```

---

### Post by wefojoij on 2008-07-28
me@my-laptop:~$ mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
proc-chroot on /var/chroot/gutsy/proc type proc (rw)
/dev/sda2 on /media/sda2 type vfat (rw,utf8,umask=007,gid=46)
/proc on /var/chroot/gutsy/proc type none (rw,bind)
/dev on /var/chroot/gutsy/dev type none (rw,bind)
/sys on /var/chroot/gutsy/sys type none (rw,bind)
/tmp on /var/chroot/gutsy/tmp type none (rw,bind)
/home on /var/chroot/gutsy/home type none (rw,bind)
/media on /var/chroot/gutsy/media type none (rw,bind)
/home on /var/chroot/gutsy/home type none (rw,bind)
/tmp on /var/chroot/gutsy/tmp type none (rw,bind)
/dev on /var/chroot/gutsy/dev type none (rw,bind)
devpts-chroot on /var/chroot/gutsy/dev/pts type devpts (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=me)
me@my-laptop:~$ df -h /home /var/chroot/gutsy/home
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             79G   78G  1003M 99%  /
/home                 79G   78G  1003M 99%  /var/chroot/gutsy/home

---

### Post by geirha on 2008-07-29
```
/home on /var/chroot/gutsy/home type none (rw,bind)
```
Yep, it's the same filesystem. So /home and /var/chroot/gutsy/home is only taking up 37GiB in total, not the double.

---

### Post by wefojoij on 2008-07-29
Thanks for your reply. The GUI in nautilus is confused about this. It reports < 1 GB free.

Also, the disk space usage analyzer is also confused and reports them as seperate entities.

Can I correct this display? Is this a bug? Also, what will happen if I override half of my disk capacity in the /home/ directory?

Thanks again for your help.

---

### Post by wefojoij on 2008-07-29
Even gparted is reporting only 5 GB on this partition. This is more than 1 GB, but still very small compared to the amount I should have.

Also, do you know if there is any way to break the link that is causing these issues? 

Thanks.

---

### Post by geirha on 2008-07-30
Try the following: ```
sudo du -x --max-depth=1 / | sort -g
```

It should tell you what is using the most space in /. If /var is the directory taking up the most space, run the same command, but with /var instead of / and so forth.

I don't understand what you mean by "breaking the link".

---

### Post by wefojoij on 2008-07-31
Hi. Thanks for your replies. By "breaking the link", I mean removing the connection between the directory in /var/chroot/gutsy/home and /home. I don't really use it and it may be causing problems.

Also, I got two instances of a Kernel Panic where the caps lock blinked on my Thinkpad PC. Could this be related?

More infromation is available:
[http://ubuntuforums.org/archive/index.php/t-421542.html](http://ubuntuforums.org/archive/index.php/t-421542.html)

and also
[http://ph.ubuntuforums.com/showthread.php?t=859471](http://ph.ubuntuforums.com/showthread.php?t=859471)

Thanks.

---

### Post by geirha on 2008-08-01
I can't see how it is related, but I don't know everything about linux, so it could be. But did you try the du (disk usage) command above? It must show where the other 40GiB that is not in /home is at. 

I don't think the link has anything to do with it either.

---

### Post by wefojoij on 2008-08-06
Hi,
I'm running that command now. But could this be a reporting bug?

---

### Post by wefojoij on 2008-08-06
Running the command above leads me to /var/chroot/gutsy/home/ as the directory that takes up the most space--~37 GB, the same amount as the /home/.

This seems to be the same information as I get by using Applications>Accessories>Disk Usage Analyzer, which is what originally caused me to think that the space was being replicated.

Does this help resolve the issue?

Please let me know if other commands will be useful.

Thanks for the great support.

---

### Post by geirha on 2008-08-08
If you unmount /var/chroot/gutsy/home with the command:
```
sudo umount /var/chroot/gutsy/home
```
How much space does du report for that dir then?

---

### Post by wefojoij on 2008-08-11
Before I unmount, I would like to be sure I am aware of how to mount and revert to the current condition. Is it

sudo mount /var/chroot/gutsy/home

or something more complex?

---

### Post by wefojoij on 2008-08-21
Hi

I would like to solve this issue. Does anyone know the answer to my previous post?

Thanks in advance for the great support I get on these forums.

---

### Post by wefojoij on 2008-08-24
Hi

Still the same issue after running 
sudo umount /var/chroot/gutsy/home

That is, the disk usage is still 99%

---

