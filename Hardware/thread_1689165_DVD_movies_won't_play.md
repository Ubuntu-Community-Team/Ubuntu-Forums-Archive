---
title: "DVD movies won't play"
date: 2011-02-16
forum: Hardware
---

### Post by mjf on 2011-02-16
I'm using Lucid 10.04 and followed the usual instructions here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

The DVD drive is recognized and even the DVD movie name is displayed.  However, of the three I tried, none play successfully.

When I try to play a DVD in VLC, the output is like this:

```

libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: Superbad
libdvdnav: DVD Serial Number: 378480b4
libdvdnav: DVD Title (Alternative): Superbad
libdvdnav: Unable to find map file '/home/mjf/.dvdnav/Superbad.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000178
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x00000178)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000203
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00000203)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0003f4b6
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x0003f4b6)!!
libdvdread: Elapsed time 0
...
libdvdread: Get key for /VIDEO_TS/VTS_19_1.VOB at 0x003b5748
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_19_1.VOB (0x003b5748)!!
libdvdread: Elapsed time 0
libdvdread: Found 19 VTS's
libdvdread: Elapsed time 0
[0x9faae30] main input error: ES_OUT_RESET_PCR called
[0x9faae30] main input error: ES_OUT_RESET_PCR called
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0x9faae30] main input error: ES_OUT_RESET_PCR called
[0x9faae30] main input error: ES_OUT_RESET_PCR called

```

Is it possible the drive is defective?  I just installed this drive. Windows XP cannot recognize it when I boot into that.

The output of dmesg may provide more clues:

```

[ 4309.866660] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4309.866665] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 4309.866670] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
[ 4309.866676] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 ed f8 00 00 02 00
[ 4309.866685] end_request: I/O error, dev sr0, sector 505824
[ 4309.866690] Buffer I/O error on device sr0, logical block 126456
[ 4309.866694] Buffer I/O error on device sr0, logical block 126457
[ 4309.972470] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4309.972475] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 4309.972480] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
[ 4309.972487] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 03 f4 b6 00 00 02 00
[ 4309.972495] end_request: I/O error, dev sr0, sector 1037016

```

---

### Post by David D. on 2011-02-16
Just a thought, since the DVD drive is not recognized by Windows, did you go into the BIOS and add the drive after installing the drive?

---

