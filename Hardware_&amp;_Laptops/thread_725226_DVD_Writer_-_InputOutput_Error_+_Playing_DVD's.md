---
title: "DVD Writer - Input/Output Error + Playing DVD's"
date: 2008-03-15
forum: Hardware &amp; Laptops
---

### Post by SuprNoodles on 2008-03-15
I'm having trouble getting my new DVD/CD Writer working. It's a Pioneer
DVR-115D (/dev/hdc). I'm running Gutsy.

Now, in addition to this new drive, I have a standard DVD-ROM (/dev/hdd) drive as well, and
DVD's play perfectly in that--meaning I have all the required codecs, etc etc
installed.

/dev/hdc is running on 2nd IDE Master
/dev/hdd is running on 2nd IDE Slave

I've updated the firmware of the Pioneer drive to the latest found in the Pioneer web site.

Everything with this new drive works fine on Windows. I used VLC Player and Nero
8 to test the various features.


When it comes to Gutsy, the following is what happens:

- Play Audio CD? Yep. That works fine.
[COLOR="DarkRed"]- Write CD? Nope, I get an error when using Brasero. I'll get that pasted in
  here asap.[/COLOR]
- Erase CD-RW? That works fine.
[COLOR="DarkRed"]- Play DVD? Nope. Doesn't work (error's below)[/COLOR]
[COLOR="DarkRed"]- Read DVD? I can browse directories and get listings, but files appear
  corrupted.[/COLOR] However, those same files on the same disk work fine on Windows +
  Mac OS X. So it appears to just be a read error on Gutsy's part of the disk.

I have set the DVD drive to Region 2 using regionset.

Ok, so playing DVD's, here are the various outputs from VLC, Mplayer and Xine:

VLC:

```
>: vlc
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: Casino Royale
libdvdnav: DVD Serial Number: 36368886
libdvdnav: DVD Title (Alternative): Casino Royale
libdvdnav: Unable to find map file '/home/davidwinter/.dvdnav/Casino Royale.map'
libdvdnav: DVD disk reports itself with Region mask 0x00ed0000. Regions: 2 5

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000190
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0002bd56
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0003db0d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0039ec7a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0039ecc7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x003aad9f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003aadec
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003b4ff3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003b5040
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003bb417
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003bb464
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003bc836
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003bc883
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003bd788
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003bd7d5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003bd8be
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003bd90b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003c11db
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003c1228
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x003c580b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x003c5923
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x003f9e53
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x003f9f6b
libdvdread: Elapsed time 0
libdvdread: Found 11 VTS's
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:926
    for vts_ptt_srpt->zero_1 = 0xcbb7

*** libdvdread: CHECK_VALUE failed in ifo_read.c:928 ***
*** for vts_ptt_srpt->nr_of_srpts < 100 ***

libdvdnav: ifoRead_VTS_PTT_SRPT failed - CRASHING!!!
vlc: vm.c:202: ifoOpenNewVTSI: Assertion `0' failed.
Aborted (core dumped)
```

Xine:

```
>: xine
This is xine (X11 gui) - a free video player v0.99.5.
(c) 2000-2007 The xine Team.
libdvdread: Using libdvdcss version 1.2.9 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000190
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0002bd56
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0003db0d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0039ec7a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0039ecc7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x003aad9f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003aadec
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003b4ff3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003b5040
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003bb417
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003bb464
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003bc836
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003bc883
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003bd788
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003bd7d5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003bd8be
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003bd90b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003c11db
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003c1228
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x003c580b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x003c5923
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x003f9e53
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x003f9f6b
libdvdread: Elapsed time 0
libdvdread: Found 11 VTS's
libdvdread: Elapsed time 0

*** libdvdread: CHECK_VALUE failed in ifo_read.c:927 ***
*** for vts_ptt_srpt->nr_of_srpts != 0 ***

xiTK received SIGSEGV signal, RIP.
Aborted (core dumped)
```

Mplayer:

```
>: mplayer dvd://1
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 79, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
There are 11 titles on this DVD.
There are 28 chapters in this DVD title.
There are 1 angles in this DVD title.
*** Zero check failed in ifo_read.c:1361
    for vts_tmapt->zero_1 = 0xaf08
*** Zero check failed in ifo_read.c:1535
    for c_adt->zero_1 = 0xb1b6
libdvdread: Invalid title IFO (VTS_01_0.IFO).
*** Zero check failed in ifo_read.c:761
    for pgc->zero_1 = 0x2004
*** Zero check failed in ifo_read.c:767
    for pgc->audio_control[i] = 0x00c0
*** Zero check failed in ifo_read.c:761
    for pgc->zero_1 = 0x0001
*** Zero check failed in ifo_read.c:767
    for pgc->audio_control[i] = 0x7100
*** Zero check failed in ifo_read.c:767
    for pgc->audio_control[i] = 0x0004
*** Zero check failed in ifo_read.c:767
    for pgc->audio_control[i] = 0x0001
*** Zero check failed in ifo_read.c:767
    for pgc->audio_control[i] = 0x3006
*** Zero check failed in ifo_read.c:767
    for pgc->audio_control[i] = 0x0002
*** Zero check failed in ifo_read.c:767
    for pgc->audio_control[i] = 0x00c0
*** Zero check failed in ifo_read.c:770
    for pgc->subp_control[i] = 0x000000c0
```

I had to quit Mplayer, but it was hanging the system.

As for accessing the files directly on a standard DVD data disc, I normally just
get input output errors. If you would like me to test something specific to help diagnose this, please ask.

I really would appreciate any help. Thanks.

---

### Post by SuprNoodles on 2008-03-15
Just to add another error, I tried to copy a file off of a DVD to my home directory, and received the following:

```
>: cp test.rar /home/davidwinter/Desktop/test/
cp: reading `test.rar': Input/output error
```

The DVD is in working order, I'm able to copy the file from it perfectly with Windows and OS X.

---

