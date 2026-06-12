---
title: "Microphone not working"
date: 2008-08-07
forum: Hardware
---

### Post by cody0707 on 2008-08-07
Ok I have been playing with Ubuntu for about 3 days now (love it so far). I visited this how to: [http://ubuntuforums.org/showthread.php?t=385739&highlight=microphone](http://ubuntuforums.org/showthread.php?t=385739&highlight=microphone)

After walking through the steps I got to where the poster said to go to volume control preferences and click on all the tabs. Well when I open up my volume control preferences there are only 3 check boxes: Master, PCM, and Digital. 

I am using a motherboards Audio Chipset is ADI AD2000B. It is an 8-channel audio that works fine in XP.

What am I doing wrong here? 

My motherboard: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131296](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131296)

---

### Post by k0l0n0sc4p1e on 2008-08-07
> **cody0707 said:**
> Ok I have been playing with Ubuntu for about 3 days now (love it so far). I visited this how to: [http://ubuntuforums.org/showthread.php?t=385739&highlight=microphone](http://ubuntuforums.org/showthread.php?t=385739&highlight=microphone)

After walking through the steps I got to where the poster said to go to volume control preferences and click on all the tabs. Well when I open up my volume control preferences there are only 3 check boxes: Master, PCM, and Digital. 

I am using a motherboards Audio Chipset is ADI AD2000B. It is an 8-channel audio that works fine in XP.

What am I doing wrong here? 

My motherboard: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131296](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131296)

hi man

you need to add "analog mix" and unmute. now unmute your mic port (front or default) - you got basic sound. to use voip, record, etc - add "input source". select mix.

and you ready to go ):P

note, be sure to use the right mixer (alsa mixer) - the one that has the needed feature.


btw, how's the sound quality?

---

