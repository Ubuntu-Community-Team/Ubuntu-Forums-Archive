---
title: "DVDs not recognized"
date: 2006-02-16
forum: Hardware &amp; Laptops
---

### Post by rumli on 2006-02-16
My DVD drive does not recognize DVDs under Ubuntu (although it does recognize both data and audio CDs).  When I try to manually mount the drive via "sudo mount /dev/dvd -o unhide" or "sudo mount /dev/hdd/ -o unhide", I get a "mount: No medium found" error.

This is not a physical problem because, when I boot to WinXP, the drive recognizes and plays DVDs fine.  Also, the DVDs themselves are legal and have worked on various other DVD players and computers.

I have installed libdvdcss2 and have enabled DMA for /dev/dvd, /dev/cdrom, /dev/cdrom1, and /dev/hdd.  (In the other threads I've seen on this forum, doing so often fixed the problem, but not in this case.)

Can anyone help?

- Rumli

PS.  Here is my system info:

Dell Optiplex GX270
Intel Pentium 4, 2.6Ghz
512MB RAM
Lite-On LTN486S 48x Max <-- CD-ROM
_NEC DVD+RW ND-1100A  <-- CD-RW/DVD-RW  (this one doesn't recognize DVDs under Ubuntu)


And here is my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               reiserfs notail          0       1
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222  0  0
/dev/hda2       /media/hda2     ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by bluevoodoo1 on 2006-02-16
There's a program called powertweak that has some more advanced configuration possibilities. One of the options you can set is one that says "check media" for your CD drive. Might be worth a shot. It's available in Synaptic. Once it's installed run it with...
```

gpowertweak

```

you could also check your removable drives and media preferences. system > preferences > removable drives + media and make sure the proper boxes are checked off (all of mine are checked on the first dialog screen).

---

### Post by rumli on 2006-02-16
Thanks very much.  The powertweak tip works, although the drive now fails to recognize audio CDs.  (When I uncheck the "check media" option in gpowertewak, CDs start working again, and DVDs stop.)  But this is a huge step toward fixing the problem.

**Update**: After rebooting, it seems to be working fine, reading both CDs and DVDs.  Thanks again!

[QUOTE=bluevoodoo1]There's a program called powertweak that has some more advanced configuration possibilities. One of the options you can set is one that says "check media" for your CD drive. Might be worth a shot. It's available in Synaptic. Once it's installed run it with...
```

gpowertweak

```

you could also check your removable drives and media preferences. system > preferences > removable drives + media and make sure the proper boxes are checked off (all of mine are checked on the first dialog screen).[/QUOTE]

---

