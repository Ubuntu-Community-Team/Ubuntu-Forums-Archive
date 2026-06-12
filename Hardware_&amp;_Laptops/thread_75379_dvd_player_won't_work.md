---
title: "dvd player won't work"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by gsaathoff on 2005-10-13
Hey all,

I can't get my DVD/RW drive to play or record to DVD's. The drive is also a CD/RW and CD-ROM/RW functions work fine. Ubuntu seems to recognize that the drive is DVD capable.

I have tried mounting DVD's as iso9660 and cannot read them. When I do, dmesg gives me this output:

[61539.417120] end_request: I/O error, dev hdd, sector 64
[61539.417214] isofs_fill_super: bread failed, dev=hdd, iso_blknum=16, block=16
[61539.422136] hdd: packet command error: status=0x51 { DriveReady SeekComplete Error }
[61539.422143] hdd: packet command error: error=0x40 { LastFailedSense=0x04 }
[61539.422148] ide: failed opcode was: unknown
[61539.422840] ATAPI device hdd:
[61539.422843] Error: Hardware error -- (Sense key=0x04)
[61539.422847] Focus servo failure -- (asc=0x09, ascq=0x02)
[61539.422852] The failed "Read Cd/Dvd Capacity" packet command was:
[61539.422855] "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "

when trying to play a dvd in mplayer I get this output:

MPlayer 1.0pre7try2-3.4.5 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices (Family: 8, Stepping: 0)
Detected cache-line size is 64 bytes
CPUflags: MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2


CommandLine: '-v' 'dvd://'
get_path('font/font.desc') -> '/home/graham/.mplayer/font/font.desc'
font: can't open file: /home/graham/.mplayer/font/font.desc
font: can't open file: /usr/local/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Using nanosleep() timing
get_path('input.conf') -> '/home/graham/.mplayer/input.conf'
Can't open input config file /home/graham/.mplayer/input.conf: No such file or directory
Can't open input config file /usr/local/etc/mplayer/input.conf: No such file or directory
Falling back on default (hardcoded) input config
get_path('.conf') -> '/home/graham/.mplayer/.conf'
Playing dvd://.
get_path('DVDKeys') -> '/home/graham/.mplayer/DVDKeys'
Reading disc structure, please wait...

vo: x11 uninit called but X11 not inited..

Exiting... (End of file)

~~

IDE-SCSI and DMA are enbled, and I am using the latest version of "breezy". Synaptic shows that all packages are up to date.

Maybe it will help to note that I had weird problems burning CD's at first, and in order to get it to work I have to specify --dev=/dev/hdd at the command line. cdrecord --scanbus does not see my drive unless I specify this.

Anyone have ideas about this?

Thanks,
Graham

---

### Post by ronmarley1 on 2005-10-15
Graham,I had a similar problem, although it looks you're more advanced than me, I posted and got a solution.
See this link: [http://www.ubuntuforums.org/showthread.php?t=74326](http://www.ubuntuforums.org/showthread.php?t=74326)

---

### Post by gsaathoff on 2005-10-15
Hey,

Thanks for the link.  I was able to get libdvdcss installed, so I'm further along than I  was before.  But I'm still having the same problem.

~~
[  175.735135] end_request: I/O error, dev hdd, sector 64
[  175.735268] isofs_fill_super: bread failed, dev=hdd, iso_blknum=16, block=16
[  175.753074] hdd: packet command error: status=0x51 { DriveReady SeekComplete Error }
[  175.753082] hdd: packet command error: error=0x40 { LastFailedSense=0x04 }
[  175.753087] ide: failed opcode was: unknown
[  175.753779] ATAPI device hdd:
[  175.753782]   Error: Hardware error -- (Sense key=0x04)
[  175.753787]   (vendor-specific error) -- (asc=0x92, ascq=0x05)
[  175.753791]   The failed "Read Cd/Dvd Capacity" packet command was:
[  175.753794]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00

~~
I'm getting the sense that the problem might be with the drive.  Someone did suggest that I specify it as a SCSI device, and I'm not quite sure how to do it.

IDE-SCSI is already loaded and called by my grub.conf file, but the drive still shows up as ATAPI...

Any other ideas?  

Also, if it helps, I'm using an AOPEN DUW1608 cd/dvd-rw drive on am AMD64 system running Breezy.  CD writing works fine.

Thanks,

-g

---

### Post by ronmarley1 on 2005-10-15
Also, I had to change from totem-gstreamer to totm-xine player and everything worked fine.  I had problems with Mplayer.
rg

---

### Post by kudu on 2005-10-15
I use Totem. You have to install libdvdcss2 and xine instead of gstreamer. Works great!

kudu

---

### Post by SickTwist on 2005-10-16
hdparm can display information about how your dvd drive is configured. Could run the following command and post the results:

sudo hdparm /dev/hdd

It might give us an indication of why you're getting errors from the drive.

---

### Post by gsaathoff on 2005-10-16
Here's what I get from hdparm:

/dev/hdd:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

thanks in advance for any ideas.

-graham

---

### Post by SickTwist on 2005-10-17
[QUOTE=gsaathoff]Here's what I get from hdparm:

/dev/hdd:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

thanks in advance for any ideas.

-graham[/QUOTE]

According to hdparm, DMA is turned off for that drive (/dev/hdd). That could explain why you were having trouble burning CDs and it might also contribute to the DVD issue. You can enable DMA by editing /etc/hdparm.conf (there are examples in the config file as well as many posts in the forum if you need help with that).

I was studying the output that you posted from mplayer and I'm trying to figure out what could be causing this part:

```

Reading disc structure, please wait...

vo: x11 uninit called but X11 not inited..

Exiting... (End of file)

```

I'll post if I can find out more. By the way, have you tried playing the DVD with xine yet? (You can change totem's backend by installing totem-xine.)

---

