---
title: "Sound only out of speaker jack"
date: 2005-08-11
forum: Hardware &amp; Laptops
---

### Post by traherom on 2005-08-11
Ok... so, I've got the usual troubles of Alsa not working so well, etc, but I've also got something I can't seem to find mentioned elsewhere. (If it is, please point me to it)

The sound that does work (an eMachines M5310) comes only out of my laptop speaker jack, something I only discovered while allowing a friend to charge his iPod in my USB port. (I was just playing with his earbuds and happened to be playing a game which had sound. The fact that I was playing a game alone is an unusual thing. ;-))

As far as I can tell, the speakers and the jack are definetly the same card.

I'm assuming that it's some configuration issue... I hope. :)

---

### Post by blind0wl on 2005-08-11
In a console type:

```
alsamixer
```

Select the second (Master M), it should have an MM in it...which means its muted....to enable, select it with your cursor and hit the letter 'm' on your keyboard...increase or decrease volume with the up and down arrows....

---

### Post by traherom on 2005-08-12
[QUOTE=blind0wl]Select the second (Master M), it should have an MM in it...which means its muted....to enable, select it with your cursor and hit the letter 'm' on your keyboard...increase or decrease volume with the up and down arrows....[/QUOTE]Nope... it was already all the way up. :(

---

### Post by blind0wl on 2005-08-12
Im pretty sure ubuntu comes with oss and alsa, have you tried playing mp3 through xmms at all?  I found that using oss players I couldnt get anything and to be honest havent bothered trying to fix it yet...mainly because I use xmms exclusively...give that a go...

---

### Post by traherom on 2005-08-12
[QUOTE=blind0wl]Im pretty sure ubuntu comes with oss and alsa, have you tried playing mp3 through xmms at all?  I found that using oss players I couldnt get anything and to be honest havent bothered trying to fix it yet...mainly because I use xmms exclusively...give that a go...[/QUOTE]Yeah, XMMS does work, but I can only hear the sound if I plug in headphones.

Also, I have an interesting issue that causes there to be a steady issue playing bzflag (2.0.2, I think. Maybe .3) (and, right now I'm logged into enlightenment and I'm getting the same thing.) This sound is only from the earbuds as well.

---

### Post by saivert on 2005-11-29
First of all some info:
Analog Devices SoundMAX integrated audio
Using snd_intel8x0 and ALSA

I have the same problems with sound only output via the jack when connected headphones or a cable to amplifier.

I tried to disable/enable "External Amplifier" and "Exchange Front/Surround" in alsamixer but it did not work.

I really hope they fix this "cable connected to jack" sensing bug.

---

### Post by teaker1s on 2005-11-29
edit volume control preferences  under edit and  tick all boxes to enable switches

---

### Post by edu65 on 2006-10-28
This is most strange. I had the same problem after going through the usual updates and switching to the 686 kernel in order to get SMP support.

I rebooted using the 386 kernel and got sound from the built-in speakers (just like after a fresh install).

Now the strange part... booting back to the 686 kernel has made the speakers work again!  

Sorry if this does not help anyone. I just wanted to share my experience...

Using Dapper with a 2.6.15-27 kernel (HDA Intel / alsa mixer) on a Dell Inspiron 6400.


> **traherom said:**
> 

The sound that does work (an eMachines M5310) comes only out of my laptop speaker jack, something I only discovered while allowing a friend to charge his iPod in my USB port. (I was just playing with his earbuds and happened to be playing a game which had sound. The fact that I was playing a game alone is an unusual thing. ;-)) 

---

