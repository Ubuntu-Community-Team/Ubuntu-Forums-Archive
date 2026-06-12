---
title: "Help with set up pchdtv 5500"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by bowens44 on 2009-03-21
Ok, I purchased a pcHDTV 5500 card for my PC. I am using Ubunut 8.10. The card works perfectly with NTSC. It is my understanding that I should be able to get unscrambled digital signals from the cable as well. I have read dozens of posts/wiki pages etc on how to set this up and I am more confused then ever.

What I need to know is;

1. Should I be able to view these channels with this card? 

2. How do I use scan or w_scan or dtvscan to get the channel info?
  

3. What is the best app for viewing.? I have tried to compile xine-hd from the pcHDTV site but have had no luck. Other apps I've seen mentioned are VLC,mplayer, gxine, Me TV and kaffiene

 4. is there an EASY to follow tutorial for this?

thanks

---

### Post by wirbel2 on 2009-03-22
1. yes - if you have a subscription at your cable provider
2. w_scan -fa -A2 <output_format>

output_format may be one of 
* X
* x
* k
*   (void, = use default)
depending on what kind of app you use. Different apps - different file formats.

I'm quite shure that these usage informations would be quite easy to find.

---

### Post by tom_in_atlanta on 2009-05-09
I am installing a pcHDTV in UBUNTU 9.4.  I followed your steps above.  I would like to try using Mplayer or Xine and need to create a channels.conf file.  When I executed w_scan I got the following results:

tom@tom-desktop:~$ w_scan -fa -A2
w_scan version 20081106
Info: using DVB adapter auto detection.
   Found ATSC frontend. Using adapter /dev/dvb/adapter0/frontend0
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
frontend LG Electronics LGDT3303 VSB/QAM Frontend supports
FE_CAN_8VSB
FE_CAN_QAM_64
FE_CAN_QAM_256
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
57000: 
63000: 
69000: 
79000: 
85000: 
177000: 
183000: 
189000: 
195000: 
(more numbers)...
831000: 
837000: 
843000: 
849000: 
ERROR: Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!
dumping lists (0 services)
Done.

Any suggestions?

---

