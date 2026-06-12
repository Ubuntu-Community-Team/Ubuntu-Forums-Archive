---
title: "scd0 problem"
date: 2008-01-09
forum: Hardware &amp; Laptops
---

### Post by charlo_be on 2008-01-09
I bought an Acer Aspire 5310 a week ago and after struggling to get the sound and the wifi working, it now seems that Ubuntu doesn't want to play dvd's. Every common codec or libdvd* has been installed, but still no dice.

Dvd-player shows up as follows in /etc/fstab:
```
/dev/scd0    /media/cdrom0    udf,iso9660 user,noauto, exec  0    0
```

Both do not work when opening in VLC, data reads fine though. In fact, VLC just crashes when opening a dvd.

Anybody any ideas? Or did I stupidly miss a scsi driver or something?

---

### Post by Bartender on 2008-01-10
I think you're going to find that DMA is not working.  That appears to be the problem with my 5920.  I think it's a kernel issue but not sure.  Hope it's fixed soon!

---

### Post by charlo_be on 2008-01-10
Damn. And there's no other way around that?

---

### Post by Yellow Pasque on 2008-01-10
Do the following to check tranfer mode:
```
hdparm -i /dev/scd0
```

---

### Post by charlo_be on 2008-01-10
The hdparm-command brings this up:

```
charlo@charlo-laptop:~$ hdparm -i /dev/scd0

/dev/scd0:

 Model=MATSHITADVD-RAM UJ-850S                 , FwRev=1.61    , SerialNo=        HC00  162242
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode
```

---

### Post by Yellow Pasque on 2008-01-10
DMA looks fine to me.

---

### Post by mc4man on 2008-01-10
run vlc from the terminal, try to open disk (dvd (menus) ) and see what is reported

---

### Post by charlo_be on 2008-01-10
Hmmm, it seems that he's having some troubel with the css key:

```
charlo@charlo-laptop:~$ wxvlc
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: DAVINCI_CODE
libdvdnav: DVD Serial Number: 44D4AEE3___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/charlo/.dvdnav/DAVINCI_CODE.map'
libdvdnav: DVD disk reports itself with Region mask 0x00e50000. Regions: 2 4 5

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000018c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00007431
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00007431)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0003e832
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x0003e832)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00369070
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00374313
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0037cae9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0037cb36
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00382943
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00382990
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00389d94
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00389de1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00391971
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003919be
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x0039734c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00397399
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003a1a71
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003a1abe
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003ace47
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003ace94
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x003ae87f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x003ae8cc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x003afc9e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x003afceb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x003b429b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x003b42e8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x003b51ed
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x003b523a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x003b6182
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x003b61cf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x003b9138
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x003b9185
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_0.VOB at 0x003b927f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_1.VOB at 0x003b92cc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_0.VOB at 0x003bcbde
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_17_0.VOB (0x003bcbde)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_1.VOB at 0x003bccf6
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_17_1.VOB (0x003bccf6)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_0.VOB at 0x003f9e44
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_18_0.VOB (0x003f9e44)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_1.VOB at 0x003f9f5c
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_18_1.VOB (0x003f9f5c)!!
libdvdread: Elapsed time 0
libdvdread: Found 18 VTS's
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x05
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x06
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed - CRASHING
wxvlc: vm.c:218: ifoOpenNewVTSI: Assertion `0' failed.
Aborted (core dumped)
```

and something 'bout a map he can't find -> libdvdnav: Unable to find map file '/home/charlo/.dvdnav/DAVINCI_CODE.map'

maybe i should try to reinstall libdvdcss and nav?

---

### Post by mc4man on 2008-01-10
The unable to find map doesn't matter, the error cracking key does. That title probably has some form of structure protection, unfortunatly I don't have a copy to see if it will run. Usually structure protection has no effect on playback, only ripping. If I can test playback later today I'll post back. 
Have you tried other titles?

edit:what region is your dvd drive set to ?  While i've had no problems with playback of titles from other regions (I'm region1) _sometimes_ vlc can't crack the css key from a mismatch of regions. If the main movie is in VTS_01 then that _may_ be why it's crashing

---

### Post by charlo_be on 2008-01-10
Yeah, I tried a few titles, some more recent than others, but all refused to play.

---

### Post by mc4man on 2008-01-10
see edit - does that apply

further thought  - if this was a new pc and you never set the region with windows before installing ubuntu then the drive is region 0. I believe you have to set a region for proper playback.

---

### Post by charlo_be on 2008-01-10
Right, I did some more testing, and it turns out that movies released (roughly) after the second half of 2007 don't play. Older movies actually do play, with a few exceptions.
Could it be that they upgraded their security or something?

And how do I check and set my region then?

---

### Post by Yellow Pasque on 2008-01-10
Before messing with region codes, I would take a look at this post:
[http://ubuntuforums.org/showpost.php?p=4111202&postcount=8](http://ubuntuforums.org/showpost.php?p=4111202&postcount=8)

---

### Post by charlo_be on 2008-01-10
I had libdvdcss2 already installed, but reinstalled it. Same outcome, still not playing all dvds, just a minority.

---

### Post by Yellow Pasque on 2008-01-10
Then I guesss we need a libdvdcss3 :\

---

### Post by charlo_be on 2008-01-10
...which is of course long from available, correct?

---

### Post by charlo_be on 2008-01-11
I could be mistaken, but when I did a "libdvdcss3" search on Google it did turn up some results. Found nothing downloadable, so I fear it was just people naming it the wrong way.

---

### Post by mc4man on 2008-01-12
I think maybe your giving up on this to easily. There's no reason open source players like vlc can't play virtually all titles. The title mentioned in your log is a sony release from late 2006. While it has  ARccoSS protection, that would have no effect on playback. As far as getting the css keys vlc will be successful 100% of the time when there's a region match. When the regions don't match vlc will try to brute force the keys and will usually retrieve them all, though it can fail to on some individual vts's. Even then playback is possible, the effected vts(s) would be scrambled. Possibly if there there was no key retrieved for the 1st. vts to play vlc would crash. 
The other protection this disk has is rce which is solely designed to prevent playback on regionfree standalone players. How that translates to pc's I'm not sure but I can't imagine it's a good thing. There's no reason not to ck. what region your drive is set to, if it hasn't or shows region0 then set it to whatever region your in. Your not forced to change anything by running regionset.

---

### Post by charlo_be on 2008-01-13
Okay, in that case: where can I check the current region setting?

Oh, and I wasn't giving up, just "letting it rest" for a few days ;-)

---

### Post by mc4man on 2008-01-13
install regionset fron synaptic, then run regionset from terminal with disc in drive

---

### Post by charlo_be on 2008-01-13
I did regionset, with following outcome:
```
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF

Would you like to change the region setting of your drive? [y/n]:y
Enter the new region number for your drive [1..8]:2
New mask: 0xFFFFFFFD, correct? [y/n]:y
Region code set successfully!

```

but dvds still don't play.

---

### Post by mc4man on 2008-01-13
try reinstalling vlc (complete removal) or clearing out the .dvdcss folder 
(in home directory - stores previously gathered info, keys for each title played or attempted to play)

edit:a quick ck. of removing vlc shows the .dvdcss folder is not cleared so you'll have to do it manually (don't delete.dvdcss - just the folders inside )

---

### Post by charlo_be on 2008-01-13
I think we're getting there. I removed vlc, emptied the .dvdcss folder and then reinstalled vlc.  One of the dvd's it wouldn't play, Da Vinci Code (DVC), actually gets recognised by both vlc and totem, but once you try to skip ahead in the main feature, both crash.

---

### Post by mc4man on 2008-01-13
Try some other titles, I'll see if i can get ahold of DaVinci, the ARccoSS does screw up the disk structure. When you say skip ahead is that next chapter or using the slider to seek.

Edit: do you know what brand dvd drive you have - I'm thinking it may be a MATSHITA which I've heard are a little touchy, barring a huge snowstorm tonight i think that's the brand in a laptop I'm getting tommorrow, if so will ck. out. On my desktop I'm not having any issues with casino royale (latest /last ARccoSS) , but that's on my desktop with benq and plextor drives

---

### Post by charlo_be on 2008-01-13
I meant the slider to seek. Pirates of the Carribean 2 has the same problem, as does Interstella-5555 by Daft Punk from 2003.

The dvd drive in the laptop is indeed a Matshita-devuce. On my desktop pc I have no problem whatsoever playing those titles (LG-reader and Sony-writer).

Good luck with the snowstorm.

---

### Post by charlo_be on 2008-01-16
*bump*

---

### Post by mc4man on 2008-01-18
Well I got the new laptop and it also has a MATSHITA drive - different model but the behavior is the same in all their laptop drives (at least recent few yrs.). At the moment it's only running vista and it will be a few weeks till I install ubuntu. A few things did become apparent - don't bother inserting a commercial dvd movie from a region other than what the drive is set to. You can look here for short explanation. [http://ubuntuforums.org/showthread.php?t=669795](http://ubuntuforums.org/showthread.php?t=669795) . 
I didn't find any issues playing back "normal' titles, but there are some issues with structure protected ones like da vinci. Vlc and the free wmp player had no problem with most protected titles in terms of playback ability though fast forwarding or next chapter could crash player if done at the wrong time. Generally it's better with these structure butchered titles to let the main movie/extras start before trying such actions. I haven't found any that once in the main movie or a legitimate extra that chapter forward, back or slider doesn't work. If you can't wait the navigation tab is a safer bet. Another option with problem disks is to use the open directory path instead of open disk, though odds are no difference.
As far as region 1 there are 2-3 titles that won't play in open source players or even wmp - rush hour 3, hairspray (recent and probably future new line cinema releases). Region2 will likely see more  widespread instances of these unplayable titles. In all cases commercial, licensed players will playback with no problems - win, powerdvd in windows, lindvd in linux. If you have some you think should play post terminal output and we'll take a look. 
These errors usually don't affect playback but do indicate structure protection
```
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
```

---

### Post by charlo_be on 2008-01-21
Right, i'll see what i can do tonight on the laptop. Thanks already for the advice.

---

