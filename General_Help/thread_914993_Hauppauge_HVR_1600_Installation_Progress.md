---
title: "Hauppauge HVR 1600 Installation Progress"
date: 2008-09-09
forum: General Help
---

### Post by sbhargav21 on 2008-09-09
Hi All,
I started recently with building a DVR & just wanted to share my experiences & progress with this.

**My Hardware:**
Hauppauge HVR 1600
ATI Radeon x1300 pro AGP 256mb
Celeron
1 GB RAM
40 GB Harddrive
400 GB SATA Harddrive (Not yet connected)
CD Drive

**Start:**
1. Downloaded 8.04 distribution ISO
**Problem #1:**
Was trying to burn it on a CD but was not getting detected. 
 - Stupid me realised later that ISO needed to be burnt using ISO to CD maker.
 - Downloaded one of the free ISO to CD burner & then it was detected. :)

2. Started installation of Mythbuntu
Followed [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=850841](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=850841) tutorial.

**Problem #2:**
Installation worked till steps 10. The part where he says /bin/cat /dev/video0 > test.mpg did not work!. :(
 - Please read later on for the continuation of this fix.

**Problem #3:**
The display on TV was not full, most parts of the output were off the screen. I had to guess using the installation manual & tabs which field I was in & what I was supposed to enter.
 - Followed the following installation guide to get a proper output on my TV.
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
 - Display was corrected :)

**Problem #4:**
The display was still black & white on TV. I tried to play with xorg.conf settings but nothing worked.
 - Was thinking of changing the s-video cable as suggested by some posts. Switched the ends of the cable. Connected the previous TV end to card & card end to TV.
 - Color display :)

**Problem #2 Revisited:**
 - I was having same issue as sofasurfer in post #25 at [http://ge.ubuntuforums.com/showthread.php?t=813429&page=3](http://ge.ubuntuforums.com/showthread.php?t=813429&page=3).
 - Followed post #26 by willoconley.
 - Card detected :)


 - Meanwhile any advice on this is appreciated

---

### Post by sbhargav21 on 2008-09-10
**Update on Sept 10, 2008**:

**Problem #5:**
I have connected the output of my Cox settop to Tuner Anlog input. Not able to scan any channels. Not sure what to do next.
When I try cat /dev/video0 > test.mpg. No picture but just hissing sound!. :)
 - I had to define a video source. Defined as no guide data as I do not have a subscription to scheduledirect yet. Named 'Analog Digital Cable'
 - In the input connection in the Tuner 1 had to select input source defined earlier 'Analog Digital Cable'
 - Scan button was enabled, detected Channels 3,4 & 48 
 - Channel 3/4 is regular TV Settop output, not sure what channel 48 is.
 - Starting channel set as 3.
 - Tuner able to tune & channel gets displayed on TV :)

**Problem #6:**
The TV display freezes up. When I record a channel it is recorded but playback freezes. I can use VLC player to play the recorded .mpg file & it plays well.
 - Am fiddling with the playback settings but nothing has worked so far :(
:confused:

- Meanwhile any advice on this is appreciated

---

