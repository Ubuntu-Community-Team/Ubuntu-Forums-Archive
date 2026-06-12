---
title: "Audio: both channels playing through left speaker"
date: 2009-07-24
forum: Hardware
---

### Post by php_penguin on 2009-07-24
Hi,

I've been googling this for about an hour, to no avail.

All my sounds are only playing out of my left speaker - to make it odder, it is playing both channels through that speaker!

I ran ```
speaker-test -c2 -li -twav

``` and it says "Front Left" and "Front Right", both playing through the left speaker.

I've checked using [i]alsamixer[i] but it seems to be all 100% volume so im totally lost right now :(

I experienced something like this a while back with a previous machine (U8.04 i think) and there *was* a moderately easy fix for it but I can't remember it...

Thanks for any help you can provide - if you live in the UK i'll post cookies or something :D

---

### Post by dagoth_pie on 2009-07-24
Does this happen on every operating system, if you can test it that would be helpful, it sounds like its playing a mono output rather than stereo, if you happen to find any settings that are set to mono then switching them to stereo might help, but if you can test it on windows or some other OS, as it is possible its a hardware problem

---

### Post by php_penguin on 2009-07-24
I have Windows 7 on here for gaming and it seems to be fine (two channels) but I heard something about stereo emulation in the Windows sound system where the mono channel is played through both?

---

### Post by dagoth_pie on 2009-07-25
weird, what sound card are you running? it definately sounds like its a software problem, but have you tried plugging in a headset or something, just to rule out the possiblity of the speakers being at fault?

---

### Post by php_penguin on 2009-07-26
Ok, i'm really sorry about this guys... but the cable was loose.

Having had this problem in an old comp I instantly assumed it was the same problem, but after plugging my iPod up to the speakers and the same problem occuring, I checked the cables and voila

I feel like such a tard :(

---

