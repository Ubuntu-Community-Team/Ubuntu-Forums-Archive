---
title: "External Blu-ray Drive Not Working on Ubuntu?!"
date: 2009-01-19
forum: Hardware
---

### Post by n0tmycupoftea on 2009-01-19
Hey Everyone,

I have been searching the boards now for about 2 days now, after I purchased an external Blu-ray player, trying to solve the problem and get it to mount, but I am completely stumped.

The Blu-ray drive is a Buffalo External Mediastation Blu-ray HD DVD combo drive.

Here's what I get prior to plugging in the external drive when I run:
```
sudo lsusb
```

```
Bus 005 Device 003: ID 046d:08c6 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 413c:8114 Dell Computer Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 413c:8126 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

and here is what I get after plugging it in:

```
Bus 005 Device 006: ID 0411:0104 MelCo., Inc. 
Bus 005 Device 003: ID 046d:08c6 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 413c:8114 Dell Computer Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 413c:8126 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

```

so I suspect things are good since it is at the very least reading it. But it does not mount at all, yet it shows up under the File System.

Here is some more info:

With
```
sudo fdisk -l
```

with the external hard drive plugged in and with it not plugged in I get this:
```
Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9169    73649961   83  Linux
/dev/sda2            9170        9546     3028252+   5  Extended
/dev/sda5            9170        9546     3028221   82  Linux swap / Solaris

```

and when I type

```
sudo mount
```

I get:
```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/n0tmycupoftea/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=n0tmycupoftea)

```

and do not see it anywhere.

Here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6e351db3-552c-4652-b42a-8065139870b5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=11b7d416-5b12-4a10-b5bd-ba9dc22e194d none            swap    sw              0       0
# /dev/scd0     /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

If anyone needs any other additional info just let me know please, and thanks for the help in advance!!

---

### Post by n0tmycupoftea on 2009-01-21
bump

---

### Post by piousp on 2009-01-21
I'm not even sure if Blu-ray is supported right now. Consider this a bump, thats all i can do

---

### Post by n0tmycupoftea on 2009-01-22
Ok, thanks.

I honestly don't know what to do because of the Ubuntu guide on playing back blu-ray discs using an XBOX360 HD-DVD drive [https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD?action=fullsearch&context=180&value=blu+ray+ripping&titlesearch=Titles]("https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD?action=fullsearch&context=180&value=blu+ray+ripping&titlesearch=Titles"), but they mention of no tricks or anything with mounting the actual drive (ie: assuming it just mounted perfectly) as oppose to me in that I am having problems mounting my external device.

Again, if anyone can help me figure out this mounting issue that would be great! THANKS AGAIN!

---

### Post by novafluxx on 2009-01-22
I'm not sure its officially supported. The software for decoding and playing BLU-RAY discs isn't open source, and most likely wouldn't be included as part of Ubuntu. So...hopefully someone with more knowledge can give you a more definitive answer

---

### Post by n0tmycupoftea on 2009-01-24
you guys can close this thread, got it working flawlessly, thanks everyone!

---

### Post by HyRax on 2009-02-20
You might want to tell people what you did to get it working as I'm sure you're not the only person who will experience this issue.

---

