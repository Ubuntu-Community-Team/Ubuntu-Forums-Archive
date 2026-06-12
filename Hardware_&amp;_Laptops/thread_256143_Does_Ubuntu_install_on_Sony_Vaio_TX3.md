---
title: "Does Ubuntu install on Sony Vaio TX3?"
date: 2006-09-12
forum: Hardware &amp; Laptops
---

### Post by Evertype on 2006-09-12
My install stalled. It gave some errors like:

INIT ID 5 respawning too fast, disabled for 5 minutes...

Then ended on:

INIT: no more processes left in this runlevel

There wasn't anything else. A friend suggested there was an issue with Ubuntu understanding the graphics of the new TX3s.

(I am normally a Mac user.) 

Help?

---

### Post by jhkuo on 2006-12-04
Hope you have got your problem resolved, the installation of 6.10 on my TX3 failed, but the 6.06 installation CD worked fine. I was able to then proceed to 6.10 upgrade successfully.

So far, the following works works on my TX3

* LCD with 1366x768
* sound
* CD drive
* USB ports
* wireless (still a bit temperamental, initial connection may take some time, also connection lost after wake from suspend)
* sound recording
* CPU speed control, I was able to also change the scaling monitor to let me change the speed manually.
* bluetooth file transfer

the following doesn't work
* built in SD card slot
* external keys don't work properly - mute, AV Mode, play and volume up/down are recognised as the same key by keyboard shortcut app. eject key is ignored.
* external monitor port doesn't work by default, I can get it to work by heavy xorg.conf editing.
* bluetooth - pairing with phone works in 6.06, but my phone wasn't able to find any services. In 6.10 I wasn't even able to pair.

---

### Post by tomranson on 2006-12-14
> **jhkuo said:**
> Hope you have got your problem resolved, the installation of 6.10 on my TX3 failed, but the 6.06 installation CD worked fine. I was able to then proceed to 6.10 upgrade successfully.

So far, the following works works on my TX3

* LCD with 1366x768
* sound
* CD drive
* USB ports
* wireless (still a bit temperamental, initial connection may take some time, also connection lost after wake from suspend)
* sound recording
* CPU speed control, I was able to also change the scaling monitor to let me change the speed manually.
* bluetooth file transfer

the following doesn't work
* built in SD card slot
* external keys don't work properly - mute, AV Mode, play and volume up/down are recognised as the same key by keyboard shortcut app. eject key is ignored.
* external monitor port doesn't work by default, I can get it to work by heavy xorg.conf editing.
* bluetooth - pairing with phone works in 6.06, but my phone wasn't able to find any services. In 6.10 I wasn't even able to pair.

All above appears to work on my TX3XP also. Currently playing with the built-in finger print reader- watch this space!...

[http://ubuntuforums.org/showthread.php?t=305141](http://ubuntuforums.org/showthread.php?t=305141) <--- this post worth noting with regard to LCD brightness control on VAIO's in Edgy (else you could end up with poor battery life!)

---

### Post by jmads on 2007-08-09
Hello All
did some one solve the fingerprint reader problem. I've a TX3 and I want to get rid of M$F...

---

### Post by quini on 2008-04-07
> **jmads said:**
> Hello All
did some one solve the fingerprint reader problem. I've a TX3 and I want to get rid of M$F...

Hi!  I'd also like to know if anyone has the fingerprint reader working !!

Mine's a TX3XP/B  :popcorn:

---

### Post by inferiorwang on 2008-04-07
I have a vaio VGN-CR123E and from what I understand, sony put some extra propietary stuff in there that makes it difficult to get the unitek touchchip working under linux (assuming your fingerprint scanner is similar to mine).  Someone was working on it, but I lost the url.

---

