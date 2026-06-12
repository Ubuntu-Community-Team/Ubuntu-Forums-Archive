---
title: "Unable to mount volume: Very odd error"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by seismicmike on 2008-02-05
I'm trying to mount my Samsung mp3 player in Linux. Previously I've been able to mount it with "supposed" rw access, but when I try to write a file it does nothing... literally... it acts like it's transferring the file, but the progress bar never moves and no file is ever transfered.

So I screwed around with fstab for a bit with no luck, and now I fear I've made things worse b/c now when I plug it in I get this:

```
mount point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)
```

This pops up in a window btw.....

Can I just say, W T F?????????????????????????????????????????????????????????


I mean, seriously. I have removed all possible reference to this device from fstab and mtab.... (which is the way it was before). Where the flip is this mount point error thing so I can fix it.....

Help, please??? I just want to download my podcasts straight to my thumb drive from my laptop without having to go through a stupid windows box.

---

### Post by jan quark on 2008-02-05
plug in the player and run these commands and post the result please


```
mount
```
```

sudo fdisk -l
```

```
cat /etc/fstab
```

---

### Post by seismicmike on 2008-02-06
```
lappy486:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/scd0 on /media/cdrom0 type udf (ro,noexec,nosuid,nodev,user=seismicmike)
```

```
lappy486:~$ sudo fdisk -l
[sudo] password for seismicmike:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4688    37656328+  83  Linux
/dev/sda2            4689        4864     1413720    5  Extended
/dev/sda5            4689        4864     1413688+  82  Linux swap / Solaris

Disk /dev/sdb: 1987 MB, 1987575808 bytes
62 heads, 62 sectors/track, 1009 cylinders
Units = cylinders of 3844 * 512 = 1968128 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
```

```
lappy486:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
# /dev/sdc1
UUID=116b1b38-098f-4513-a126-8ce9d6160ca7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=15e20115-5a33-4cf0-97ca-3f4ceab925e5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Thanks in advance.

---

### Post by seismicmike on 2008-02-06
PS Under my current fstab configuration my usb thumb drive works fine plug and play. Like I said in my original post, my thumb drive works fine plug and play under these settings.

Also, it's quit working in Windows too, so maybe there's a problem with the player itself :shrug:

---

### Post by seismicmike on 2008-02-07
bump

---

### Post by seismicmike on 2008-02-12
it's not the device. I have it working on my Windows desktop right now. I just cannot get it to mount in Ubuntu. Please help.

---

### Post by seismicmike on 2008-02-19
bump

---

### Post by raymurph on 2008-03-09
Hi, I had a similar problem that I was able to cure with this answer from another thread. Hope it helps others!



"I had this same problem, only it was for my external hard drive. In the mount point, I entered /media/usbdisk because it was mounting as /media/disk.

I got the same error message, mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

I found the setting by going Places | Computer. From there, was able to see my drive but it gave me that error when trying to mount. Right click | Properties | Volume Tab | Removed the mount point setting.

I found that if you want to change the mount point, you only have to put what it should be named. For instance, to have my disk mounted as /media/usbdisk, I put usbdisk into the box (an not the entire path)."

---

### Post by seismicmike on 2008-03-10
Hey, thanks!

---

### Post by leroygbiv on 2008-03-20
Big thanks to Raymurph for a great solution & Seismicmike for asking the question.
It's helped me out a lot.:)

---

### Post by lcjones on 2008-04-10
I did the same thing and I did what you just said, but my properties doesn't have a volume tab!  Here are the tabs:  Basic Emblems Permissions Open With Notes

and none of those have the mount point option.  Anyone know anything else?

---

### Post by zweiundzwei on 2008-04-21
> **lcjones said:**
> I did the same thing and I did what you just said, but my properties doesn't have a volume tab!  Here are the tabs:  Basic Emblems Permissions Open With Notes

and none of those have the mount point option.  Anyone know anything else?

I have the same problem. Any ideas?

---

### Post by enmar213 on 2008-04-26
I just had this problem this morning. I love google!

I was able to fix it by using gconf-editor. The link below has the solution.

[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668)

---

### Post by r0cks0ul on 2008-07-14
> **raymurph said:**
> Hi, I had a similar problem that I was able to cure with this answer from another thread. Hope it helps others!



"I had this same problem, only it was for my external hard drive. In the mount point, I entered /media/usbdisk because it was mounting as /media/disk.

I got the same error message, mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

I found the setting by going Places | Computer. From there, was able to see my drive but it gave me that error when trying to mount. Right click | Properties | Volume Tab | Removed the mount point setting.

I found that if you want to change the mount point, you only have to put what it should be named. For instance, to have my disk mounted as /media/usbdisk, I put usbdisk into the box (an not the entire path)."

for some reason the solution is not working when you are on 8.04 i know what i did that caused the problem i tried changing some settings on the mount point when you right click on it then properties. Before I got on to his thread I already tried the instructions here but then it did not work. I already check fstab but there is nothing wrong in it. I will look for some other solutions.

---

