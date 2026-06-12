---
title: "DVD not mounting help please"
date: 2008-10-13
forum: Hardware
---

### Post by christianvaldes on 2008-10-13
my Vlc Player won't play DVD's

some of them mount and most of them don't

aaron@Christian:~$ sudo mount /dev/scd0  /media/cdrom0/
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: you must specify the filesystem type

CAn someone help?

This was working perfect before I upgraded the sytem.

---

### Post by christianvaldes on 2008-10-13
vlc error

aaron@Christian:~$ vlc
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/aaron/.dvdnav/.map'
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
[00000294] dvdread demuxer error: DVDRead cannot open source: /dev/dvd
[00000297] vcd access error: no movie tracks found
[00000297] access_file access error: file /dev/dvd is empty, aborting
[00000304] main private error: cannot pre fill buffer
[00000307] cdda access error: could not read block 0 from disc
[00000307] cdda access error: cannot read sector 0

---

### Post by christianvaldes on 2008-11-03
I upgraded to Intrepid.
Everything is working fine now with my DVD Writer.
I wish that someone could have confirmed that the fix was coming out with the upgrade.

---

