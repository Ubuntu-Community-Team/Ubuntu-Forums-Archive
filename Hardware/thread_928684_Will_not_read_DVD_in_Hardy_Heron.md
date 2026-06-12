---
title: "Will not read DVD in Hardy Heron"
date: 2008-09-24
forum: Hardware
---

### Post by ajaychebbi on 2008-09-24
My drive is working - it reads CDs fine. But will not read movie DVDs or Data DVDs . The drive churns for couple of times and then stops - but the drive LED (light) stays on!
Hardware: HP omnibook 4150B laptop.
 
I installed VLC, libdvdcss2, and a everything else I could find on the forums :(
This is what I get on dmesg | tail

[ 1753.154387] sr: Add. Sense: Unable to recover table-of-contents
[ 1755.153484] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 1755.153521] sr: Sense Key : Medium Error [current] 
[ 1755.153533] sr: Add. Sense: Unable to recover table-of-contents
[ 1757.152630] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 1757.152666] sr: Sense Key : Medium Error [current] 
[ 1757.152679] sr: Add. Sense: Unable to recover table-of-contents
[ 1759.151912] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 1759.151950] sr: Sense Key : Medium Error [current] 
[ 1759.151962] sr: Add. Sense: Unable to recover table-of-contents

Please help!!

---

### Post by Patsoe on 2008-09-24
"Medium error" and "could not recover toc" seem hardware errors to me? I think that machine is pretty old (had that model at some point too, but without dvd transport) - so maybe it cannot read the type of dvd you're trying to feed it?

---

### Post by ajaychebbi on 2008-09-24
Thanks for the thought. The DVD drive works fine when I boot on Win XP. may be I need to install a driver for that DVD drive?

This is what I see on the VLC console window

libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/scd0 with libdvdcss.
libdvdread: Can't open /dev/scd0 for reading
libdvdnav: vm: faild to open/read the DVD
[00000294] dvdread demuxer error: DVDRead cannot open source: /dev/scd0
[00000297] vcd access error: could not read TOCHDR
[00000297] vcd access error: no movie tracks found
[00000297] access_file access error: file /dev/scd0 is empty, aborting
[00000297] cdda access error: could not read TOCHDR
[00000297] cdda access error: no audio tracks found
[00000292] main input error: no suitable access module for `dvd:///dev/scd0'

---

