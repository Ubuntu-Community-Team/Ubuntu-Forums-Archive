---
title: "Cannot enable DMA on my new dvd writer"
date: 2005-08-30
forum: Hardware &amp; Laptops
---

### Post by icheyne on 2005-08-30
I installed my DVD writer after my new Ubuntu install - poor move. Now I cannot get DMA enabled on the drive. I have followed the instructions in the wiki, but to no avail.

[https://wiki.ubuntu.com/DMA]("https://wiki.ubuntu.com/DMA")

I believe I am pointing hdparm.conf at the wrong file, as the DVD drive can burn and play DVDs with no problems.

Here are the last two lines of my /etc/hdparm.conf:
```
/dev/dvd {
dma = on
}

```

Interestingly, on boot, there is a message saying there is no such device as /dev/dvd. Which device do I use?

Here is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               reiserfs notail          0       1
/dev/hdb5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#Added by winmac_fstab utility
/dev/hda1 /media/12\040GB\040Disk\040(hda1) ntfs ro,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
#Added by winmac_fstab utility
/dev/hda4 /media/100\040GB\040Disk\040(hda4) vfat rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
/dev/hdd        /media/dvd   udf,iso9660 ro,user,noauto  0       0
```

---

### Post by ayates on 2005-08-30
In hdparm try /dev/hdd instead of /dev/dvd.

---

### Post by icheyne on 2005-08-31
Thanks mate. I tried it but no joy. So frustrating!

---

### Post by Copter on 2005-09-01
[QUOTE=icheyne]Thanks mate. I tried it but no joy. So frustrating![/QUOTE]hi!

i had the same problem. i tried _everything_... and it worked (finaly). check my post [here](http://ubuntuforums.org/showthread.php?t=56835&page=5&pp=10) or read the whole thread. im sure it will help you.

good luck!

copter :]

---

### Post by icheyne on 2005-09-02
Thanks I'll have to look at that, but it looks pretty complicated...

---

### Post by Copter on 2005-09-02
kernel compilation is quite tricky, but i think you should try adding your motherboard chipset drivers to /etc/modules. [this](http://www.ubuntuforums.org/showpost.php?p=93238&postcount=5) post is essential and its not that hard to handle.

believe me, it is possible :). in my case it took a week or so. i think i tried every method / trick mentioned on this forum.

---

### Post by vayu on 2005-09-02
[QUOTE=icheyne]I installed my DVD writer after my new Ubuntu install - poor move. Now I cannot get DMA enabled on the drive. I have followed the instructions in the wiki, but to no avail.

[https://wiki.ubuntu.com/DMA]("https://wiki.ubuntu.com/DMA")

I believe I am pointing hdparm.conf at the wrong file, as the DVD drive can burn and play DVDs with no problems.

Here are the last two lines of my /etc/hdparm.conf:
```
/dev/dvd {
dma = on
}

```

Interestingly, on boot, there is a message saying there is no such device as /dev/dvd. Which device do I use?

Here is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               reiserfs notail          0       1
/dev/hdb5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#Added by winmac_fstab utility
/dev/hda1 /media/12\040GB\040Disk\040(hda1) ntfs ro,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
#Added by winmac_fstab utility
/dev/hda4 /media/100\040GB\040Disk\040(hda4) vfat rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
/dev/hdd        /media/dvd   udf,iso9660 ro,user,noauto  0       0
```[/QUOTE]
 According to your fstab you should be using /dev/hdd

try this:
$ sudo hdparm /dev/hdd

does it show dma = 1

if not then do:
$ sudo hdparm -d1 /dev/hdd

If you get a message that it can't do it then you need to modify /etc/modules

I had the same problem and read an article on it that solved it, but I cannot find it.  The entry changed based on your cpu.  For intel you put:
piix
ide-core

above the ide-cd entry.

My /etc/modules now looks like this:
piix
ide-core
ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse

also in the hdparm.conf file put:

/dev/hdd {
dma = on
}

Then reboot.

---

