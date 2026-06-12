---
title: "I Cant Play DVD's !"
date: 2005-05-15
forum: Hardware &amp; Laptops
---

### Post by AthlonXPInside! on 2005-05-15
Hi there! Just installed ubuntu and this is my first try in Linux, so I guess the problem I'm having is simple but for me it's impossible to solve since I don't understand (yet!) how linux works when mounting devices. I have 1 dvd rom, 1 dvd rw and 1 cd rw in my box. I also have a program named totem which I think can playback DVD's. Well everytime I put a DVD on the DVD RW or DVD ROM totem just says that there was a error mounting my device. If I put a DVD with data (like ubuntu dvd) the icon just pops in my desktop and I can browse  the DVD...  ](*,) 

What's wrong with my setup? Any help would be appreciated.

I just read some posts and I think this should help, my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               reiserfs notail          0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdb        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom2   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Zelut on 2005-05-15
[QUOTE=AthlonXPInside!]Hi there! Just installed ubuntu and this is my first try in Linux, so I guess the problem I'm having is simple but for me it's impossible to solve since I don't understand (yet!) how linux works when mounting devices. I have 1 dvd rom, 1 dvd rw and 1 cd rw in my box. I also have a program named totem which I think can playback DVD's. Well everytime I put a DVD on the DVD RW or DVD ROM totem just says that there was a error mounting my device. If I put a DVD with data (like ubuntu dvd) the icon just pops in my desktop and I can browse  the DVD...  ](*,) 

What's wrong with my setup? Any help would be appreciated.

I just read some posts and I think this should help, my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               reiserfs notail          0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdb        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom2   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0[/QUOTE]
 I had the same error with Totem (not my personal favorite, by the way).  I did notice that I needed to go into the Totem settings & tell it which drive was my DVD.  That was simple enough using a drop-down selection.  Give that a try if you haven't already.

I'm also having problems with playing DVDs but its just that the audio/video doesn't match up completely.  If anyone has suggestions with that I'd appreciate it.

---

### Post by bruizer on 2005-05-20
This has been the subject of many posts. Check out @jens post about DMA. This may help you as I was seeing the same type of errors prior to reading:
[http://www.ubuntuforums.org/showthread.php?t=35188](http://www.ubuntuforums.org/showthread.php?t=35188)

Hope this helps!

---

