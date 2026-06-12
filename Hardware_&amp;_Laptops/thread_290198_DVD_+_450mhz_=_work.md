---
title: "DVD + 450mhz = work?"
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by voided3 on 2006-10-31
Hello. When I am home over xmas break from school, I plan to Ubuntu-ize a 450mhz AMD K6-III equipped comp with between 256-384mb of PC-100 SDRAM (depending on what I have laying around) and either a Radeon 7000 or nvidia TNT, both with 32mb of ram (depending on which I use). I realized that all of the spare CD-ROM drives I have are complete worn out crap, so I think i'll spend the $20 or less and get a new one, but I was thinking about getting either a DVD-ROM or a CD-RW/DVD-ROM combo. Would this setup be powerful enough to play DVDs in Kaffiene or even burn CDs at low-medium speed when running Dapper? Thanks!!

---

### Post by jsandys on 2006-11-01
My guess is that this will have plenty of power to burn CDs, but not enough to play DVDs.  Are you planning to drive a monitor or the TV?  From my experience I would use the nvidia board and avoid the ATI board.  At 640x480 your system might play a DVD but you might have picture tearing or missed frames when there is a lot of motion or changes in the picture.

Give it a try, what have you got to loss?  If you can't play a DVD movie, you will still be able to get software off of DVD-ROMs.  And maybe it will be fast enough to play cartoons with static backgrounds like the Simpsons and Futurama.  There are a lot of tune up tips available, and maybe it would run faster with XFCE instead of KDE.

Report back to this thread after xmas and let us know how it turned out.

---

### Post by zgornel on 2006-11-01
DVD playback "should" work provided you put in a more powerful graphic card (geforce 2 or higher)

---

### Post by voided3 on 2006-11-02
Hey there. Now here is where I get weirded out, because I know i've seen less powerful computers come with DVD drives preinstalled, old Compaqs for example. Also, I used to have that very same 32mb Radeon 7000 in a comp running around 1.4ghz and it played DVDs perfectly, even with power hungry Windows Media Player (it was a dark time before the discovery of open source magic). However, I suppose having one third of the processing power behind it makes a difference... I suppose my ponderings will be answered after I press the good 'ol AT power switch and stick the Ubuntu CD in a newly installed DVD drive, but any thoughts on the are appreciated. Also, what programs do you reccomend for DVDs? I found Kaffiene to be the best for my Athlon XP system, but are there "lighter" players? Thanks again!

---

### Post by KingArthur10 on 2006-11-02
From experience, I was able to get a 333Mhz Intel Pentium II laptop with an 8Mb graphics card to run fullscreen DivX from the CD drive using MPlayer, so I'm guessing you'll be good to go with DVD playback.

---

### Post by wargames on 2006-11-02
Just a couple of months ago, I pulled my old workhorse PII 350Mhz from the corner of the room and decided to upgrade it a little and install Dapper on it. I installed a Dual-layer dvd burner, replaced the very old video card with a Geforce 4 MX 4000 64MB agp card and installed a front panel multi-card reader/writer with USB 2.0 jack in a 3.5" drive bay and installed a PCI Firewire/USB 2.0 card with internal USB headers for connecting the front panel USB jack. Anyway, after installing Dapper and installing the codecs and VLC the system plays DVD movies great with a monitor resolution set at 1024x768 on the old CRT that came with the system. Even plays them at full screen great. Your 450MHz should work just fine.

---

### Post by zgornel on 2006-11-05
Note: Pentium II CPUs have a much stronger FPU that K6/II/III-s.

---

### Post by voided3 on 2007-01-18
Hello. Well, I finally got it built, and for those who are curious it does play dvds, but not perfectly smooth. I ended up getting an external usb DVD burner which I what I used to play the dvds (obviously usb 1.1), and the system ended up having 192mb of RAM and the nvidia tnt2 64 running Xubuntu. On fullscreen, it gets worse, but windowed with a screen resolution of 1024x768 it does alright when using totem movie player or ogle. With usb 2.0 I probably would have better results, but not by much I would imagine. I also happened to acquire a computer with a 633mhz (OCed to 713mhz) intel celeron for free over break, and that also runs Xubuntu but with 384mb of RAM and a MX440. Even with a screen resolution of 1600x1200, totem movie player played DVDs from the external drive on usb 1.1 perfectly smooth both windowed and fullscreen. 

Alrighty, that's the result of my experiment. Perhaps an internal IDE DVD drive would fare better, but I didn't have a chance to try one. Thanks for the input!

---

### Post by jjabba on 2007-01-18
Yes it would, 
I use a 350 Mhx P2 as an ubuntu Videoplayer (stacked under the TV just like any DVD-player) It's got a crappy TNT2 64 MB video card and it works great, even för XviD as long as you stay away from the HD stuff. :-D

---

### Post by RandomJoe on 2007-01-18
Interesting...  I've had pretty poor luck playing video even on 1GHz P3 machines!  They would handle "standard" stuff fine, but if you got any action going, especially in anime (and _most_ especially the "flying stars" effect in Cowboy Bebop when they would travel through the jumpgates or whatever they called them) I lost A/V sync badly.

However, I have always been using MPlayer, whether playing DVDs or mpegs.  Perhaps VLC is more efficient?  Anyone tested that?  I may have to experiment this weekend...  (Supposed to get snowed in again anyway...!)  

The last time I really experimented was also when I was using a 1280x1024 FP at fullscreen - now I have a "home theatre" projector that is only 820x480 or so.  That should reduce the demand on the system considerably...

Right now, I have a P4 3GHz system on the projector, but if I could pull it off and use my 1GHz P3 I'd love to put it to more strenuous use...  (The P3 is also much quieter!)

---

### Post by voided3 on 2007-02-11
Hey, it could be a video driver issue, but experimenting with different media players is an excellent idea. A lot of the programs for Ubuntu are quite small, so download all you wish. Also, make sure you have all necessary codecs installed. I use Automatix to ensure this and it hasn't failed me yet. The memory amount could be a factor (256mb or more is plenty for light multitasking on Xubuntu), as well as the dvd drive's reliability if it's older; in my experiences, the first thing to go on a computer are the optical drives. Good luck!

---

