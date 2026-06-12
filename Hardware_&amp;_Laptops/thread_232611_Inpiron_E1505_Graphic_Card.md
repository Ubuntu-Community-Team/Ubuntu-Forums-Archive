---
title: "Inpiron E1505 Graphic Card"
date: 2006-08-08
forum: Hardware &amp; Laptops
---

### Post by rukawa on 2006-08-08
Hi... im thinking purchase a laptop dell inspiron e1505 and i need your help to choose the best of these 2 video cards...

256 MB ATI Radeon X1400 HyperMemory
256 MB GeForce Go 7300 TurboCache

which is the best to work with Ubuntu dapper?? 

thanks to all...

---

### Post by vanilla.gorilla on 2006-08-09
I am a linux newbie, but in my knowledge, Nvidia is much more supported.  I read all these posts about changing .xorg files and what not for ATI.  I have this same laptop with the nividia card and Ubuntu picks it up right nice.  Full resolution first boot, even with the live cd.

---

### Post by rukawa on 2006-08-09
thanks... i m going to consider this...

---

### Post by UltraMathMan on 2006-08-09
I have an E1505 with the 256 MB ATI Radeon X1400 HyperMemory. First note that this is really a 128MB card (the other 128MB is "shared" with the system (ie RAM). I'm not sure if this is the case with the Nvidia card but you might want to check that out. That said, I had no real problems installing the fglrx and ATI drivers but I had to reconfigure the X-server in order to get widescreen resolutions[that is detailed here]("http://www.ubuntuforums.org/showthread.php?t=218610"). Installation of XGL/Compiz was flawless, but I felt a couple (1-3) crashes (of mostly Firefox) every 2 weeks was too much so I went back to Gnome. Otherwise the ATI card is working well, but like I said you might want to do some research on the Nvidia card.

-Hope this helps :) 

-P.S. I've run HL2 : Episode One in XP with this card and it looks great - just to give you an indication of it's gaming ability

---

### Post by rukawa on 2006-08-09
mmmm yeah i had had some problems with the XGL with my ATI Radeon 9550 for PC... so for this reason and all problems about ATI in the forum i think is not the best match for ubuntu XGL... 

well im going to search info about NVIDIA... if anyone knows about it tell us please....
thanks to all

---

### Post by TheJC on 2006-08-13
I have a E1505 with the Nvidia card and it seems to be working very well without installing the nvidia driver. I have a problem right now where the screen flickers and flashes before it goes into the screen saver. I'm trying to debug that issue right now. I tried to install the nvidia driver but I had problems doing it. I've been doing this in my spare time in the last 2 days so I haven't been able to give it much attention yet.

Edit:

I just ran sudo nvidia-xconfig and it seemed to configure my video card drivers correctly. I had some other parameters on that command the first time I ran it and it didn't seem to like it. I can't remember what those parameters were though.

---

