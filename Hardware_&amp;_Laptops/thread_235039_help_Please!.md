---
title: "help Please!"
date: 2006-08-12
forum: Hardware &amp; Laptops
---

### Post by rck_hitokiri on 2006-08-12
i accidentally change my cd/r drive to read only.... how do i reverse this? i cant burn anything even with gnome baker... heres the stats:

mount: block device /dev/hdc is write-protected, mounting read-only

mount: wrong fs type, bad option, bad superblock on /dev/hdc,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so


Please help out i need to put an important document to a cd and needs to be submitted in 2 hours.... please help me out,.... please....

---

### Post by rck_hitokiri on 2006-08-12
these are some results to guide you.



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hda1       /windows2       ntfs    nls=utf8,umask=0222 0   0
/dev/hdd1       /windows        ntfs    nls=utf8,umask=0222 0   0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0




This happens when i mount a cd... and i cant burn or write anything od cd-r's:::

Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.
Show details:
            mount: block device /dev/hdc is write-protected, mounting read-only

mount: wrong fs type, bad option, bad superblock on /dev/hdc,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so



This is the problem... please guys help out....

---

### Post by rck_hitokiri on 2006-08-12
please help me ill give any info you need just to fix this cd-rw.... thanks....

---

### Post by Turin Turambar on 2006-08-12
I'm not an expert, but, how did you make your cdrw drive to be just cdr? What commands did you use for that? What program are you using for burning?
Seems like you messed the hdparm settings, but I could be wrong.

And oh, if you want more answers, please change your subject, because "help Please!" doesn't say anything particular about your specific problem.

---

### Post by rck_hitokiri on 2006-08-13
heres the catch. My cd-rw drive (/dev/hdc) can read other cd's like normal cd-roms... the problem is when i put on a blank cd-r disk, i cant write to it or make any data files and audio files written to it. i dont know whats wrong but it sends out an error message like this:


mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

heres my fstab stats:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222 0   0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   iso9660 defaults,user,rw,noauto 0       0
/dev/hdd1       /windows2       ntfs    nls=utf8,umask=0222 0   0


Hope this can help. thanks and sorry if the post is confusing im really confused figuring this out. :(

---

### Post by Turin Turambar on 2006-08-13
I don't know if this will help, but here's a fstab for my cdrw:

/dev/hdc        /media/cdrom0	udf,iso9660 user,noauto     0  0

Try to copy/paste that line instead of yours and see if that works.


Also check System/Administration/Discs, check your cdrw and see supported features.

Good luck!

> **rck_hitokiri said:**
> heres the catch. My cd-rw drive (/dev/hdc) can read other cd's like normal cd-roms... the problem is when i put on a blank cd-r disk, i cant write to it or make any data files and audio files written to it. i dont know whats wrong but it sends out an error message like this:


mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

heres my fstab stats:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222 0   0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   iso9660 defaults,user,rw,noauto 0       0
/dev/hdd1       /windows2       ntfs    nls=utf8,umask=0222 0   0


Hope this can help. thanks and sorry if the post is confusing im really confused figuring this out. :(

---

### Post by rck_hitokiri on 2006-08-13
i appreciate your troubles but it didnt work... thanks bro.. :(

---

### Post by simonn on 2006-08-13
```

mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc, missing codepage or other error
in some cases useful info is found in syslog - try dmesg | tail or so

```

This is normal and to be expected.
CDs are read only, so it tries to mount the CD read only, and the "wrong fs type" error is caused because a blank CD has no file system - it is blank! 

Assuming you are using Ubuntu and not Kubuntu or Xubuntu, see the section "Using GNOME Nautilus desktop "file manager" to burn a data CD:" in [http://yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html](http://yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html).

---

