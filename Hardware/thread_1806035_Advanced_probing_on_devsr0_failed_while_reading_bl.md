---
title: "Advanced probing on /dev/sr0 failed while reading block size"
date: 2011-07-17
forum: Hardware
---

### Post by piolin on 2011-07-17
Hi all,

I used to be able to play DVDs, but after an upgrade or two, nothing will play back.  Here's what happens with a DVD in the drive and running Kaffeine:


rolandj@sibilla:~$ kaffeine
Advanced probing on /dev/sr0 failed while reading block size
rolandj@sibilla:~$ params.c:OpenConfFile() - Unable to open configuration file "/home/rolandj/.smb/smb.conf":
        No such file or directory
params.c:OpenConfFile() - Unable to open configuration file "/home/rolandj/.smb/smb.conf.append":
        No such file or directory
libdvdnav: Using dvdnav version 1.1.19 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Attempting to use device /dev/sda6 mounted on / for CSS authentication
libdvdread: Could not open /dev/sda6 with libdvdcss.
libdvdread: Can't open /dev/sda6 for reading
libdvdread: Device /dev/sda6 inaccessible, CSS authentication not available.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/rolandj/.dvdnav/.map'
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
libdvdnav: Using dvdnav version 1.1.19 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdnav: vm: faild to open/read the DVD


I can't find anything about the subject error, relating to DVDs or Kaffeine. Any clues?

TIA,
piolin

---

