---
title: "Maya 44 USB sound card"
date: 2010-02-23
forum: Hardware
---

### Post by bobo.san on 2010-02-23
Hi 
I'm quite new to ubuntu and I want to setup my laptop PC (amilo one) to use it to play edit midi files and create one with a PC 300 roland keyboard.

since the sound card that come with amilo is very poor... (I can run jack only selecting playback option, not duplex) I want to use an external USB soundcard that I'm using under windows.

the sound card is MAYA 44 USB, it is recognized by ubuntu (9.10 version) as plug&play
but I guess it is driven via OSS and not ALSA.
So at the end I'm able to hear sound played via a player (using OSS) but I can't use this device seting it in jack. I've tried to select OSS in kack as well but device is not started.

resuming i guess problem is :
- maya usb can use ALSA but only OSS;
- settings OSS in jack I get error in startgin the device.

any idea?
am I doing something wrong?
is it a good idea to use an external usb sound card for this purpose? (i.e. play midi files and play pc roland keyboard)

Many Thanks.

roberto

PS I can use ext sound card and pc ronlad to play real-time (with 5ms of latency) under windows... so I guess I could do at least the same with linux.

---

### Post by bobo.san on 2010-02-26
Hi
just to let you know if someone has same problem I was able to solve it.
Actually as said ext usb maya 44 card was recongnized, I just force disable the default one (the internal audio card) and have only maya 44 usb as active one.
Then once in Jack audio server I select device 1, the one associated with maya 44 usb (it is listed also the audio card name) and then try some settings to not have a lot of XRUN.
And it works... actually I get a latency of 2,9 msec selecting 64 as frame/period and 2 as periods/buffer.

ciao

---

### Post by krzakx on 2011-07-28
Are there works all inputs and output? or just two like in windows by plug&play drivers?

---

