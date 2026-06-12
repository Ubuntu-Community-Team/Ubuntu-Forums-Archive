---
title: "Lenovo N5901 wireless keyboard"
date: 2010-12-29
forum: Hardware
---

### Post by sombertattoo on 2010-12-29
I recently picked up the N5901 keyboard for Christmas to go with the htpc I'm building with Mythbuntu 10.04

For the most part, it works out of the box. Plug and play. Volume works great and the orange explorer key works great too.

Problems are the rewind,pause,play,forward buttons. They work within Rhythmbox but not mplayer where I actually need them! I tried playing with the input.conf file for mplayer but mplayer doesn't seem to obey that file.

MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team

Any advice?

xev output:
FocusOut event, serial 33, synthetic NO, window 0x2000001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 33, synthetic NO, window 0x2000001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  4294967230 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 33, synthetic NO, window 0x2000001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 33, synthetic NO, window 0x2000001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 



The line with "keys:" is quite disturbing. I tapped the rewind key twice and notice how the keys:  4294967230 changes to keys:  2

---

