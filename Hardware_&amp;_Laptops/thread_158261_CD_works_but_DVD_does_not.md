---
title: "CD works but DVD does not"
date: 2006-04-10
forum: Hardware &amp; Laptops
---

### Post by atomicbaum on 2006-04-10
I have been searching around the Internet for days for a solution to this problem.  I have an old Compaq DVD player that has worked for a few years now.  I have installed SuSE (DVD format) with this DVD player before, and I have also installed Debian (also DVD format) with this drive before (and yes I fell in love with Ubuntu). The DVD drive does work with CDs and is mounted. However, whenever I try to use the DVD to watch movies it wont work. Every time I try to mount it it just tells me "no medium found".

Some additional information:

yoshi@paradox:/media$ hdparm -v -i /dev/dvd

/dev/dvd:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

 Model=COMPAQ DVD-ROM SD-612B, FwRev=BL16, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 *mdma2
 AdvancedPM=no

 * signifies the current active mode

------------------------------------------------------------------------------------------------
And my fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hda5       /media/windowsxp  ntfs    nls=utf8,umask=0222 0       0

It would be great If I could finally get some help with this.

---

### Post by dbw on 2006-04-10
This really sounds like a software problem.  Have you installed the dvd codecs yet?

---

### Post by rutterhj on 2006-04-10
Hello I am having the same issues. Where are the codecs found?

---

### Post by GatorV on 2006-04-11
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) in the PlayDVD section

---

### Post by atomicbaum on 2006-04-11
Hmmm, I will have to try (I'm at school right now), but would codecs even hinder the mounting of a DVD? I guess I should try My SuSE dvd to see if it mounts.

---

### Post by atomicbaum on 2006-04-11
Well, DVD's with information (Like an old SuSE 9.0 DVD) work, but movie DVD's do not work. I do have libdvdcss2, libdvdnav4, libdvdread3,and libdvdplay0. I can play movies if they are .mpg, .mpeg, or .avi with xine and totem. I just cant get the video DVD to mount. It just says "no medium found".

---

### Post by atomicbaum on 2006-04-12
Ok, mabe it is a software problem. I downloaded a few DVD players and when i try to use them they give me this messege:

yoshi@paradox:~$ ogle
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
ERROR[ogle_nav]: faild to open/read the DVD
DVDSetDVDRoot:: Root not set

Any suggestions?

---

### Post by atomicbaum on 2006-04-12
Here is something

yoshi@paradox:~$ mplayer dvd://49 -dvd-device /media/cdrom0/
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu6 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Athlon Thunderbird (Family: 6, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 0 SSE2: 0
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Opening joystick device /dev/input/js0
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing dvd://49.
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Couldn't find device name.
Reading disc structure, please wait...
libdvdread: Can't open file VIDEO_TS.IFO.
Can't open VMG info!
File not found: '49'
Failed to open dvd://49


Exiting... (End of file)

---

### Post by atomicbaum on 2006-04-13
Well, I got fed up with my DVD drive, so I took it apart (Im to cheep to buy a new one) and turns out it was full of dust. So I cleened it and come to find out, It started to mount DVD'S! Why it mounted cd and data dvds I and not video DVD's I dont know. I still had problems with some DVD's (using ubuntu) but they mounded on Windows XP (I feel dirty for using that). So today I will take it apart once more and do a complete cleening.

Thanks for the help from everybody!

---

