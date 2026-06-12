---
title: "using headset and mic as a bluetooth headset."
date: 2007-08-24
forum: Hardware &amp; Laptops
---

### Post by forgreatsource on 2007-08-24
hello everyone.
i did some searching and im just wondering if this would be possible.
i have a bluetooth phone and a bluetooth adapter.
i can transfer data back and forth no problem.

what im trying to do is set it up so i can use my computer headset and mic combo as a bluetooth headset for my phone.

i don't know it its even possible i couldn't find anything on the forums.

thanks.

ubuntu version 7.04

---

### Post by forgreatsource on 2007-08-25
bump

---

### Post by gammal on 2007-12-24
I've been trying to do that, but haven't succeeded so far. I'll give you a pointer and hope that you'll be luckier than myself: this page [http://bluetooth-alsa.sourceforge.net/](http://bluetooth-alsa.sourceforge.net/) says you can use Gammu to achieve that. I couldn't get it to work with my SonyEricsson T610 though.

---

### Post by BITstate on 2007-12-24
I have been trying something similiar. I have been trying to use the bluetooth earpiece that came with my phone, with the computers Bluetooth dongle so that I dont have the wires in the sound card.  The reason for doing this apart from having a completely wireless desktop, is because the cat loves to pull out the mic plug, nothing else, just the mic plug, if I tap it, I think the cat will get angry and eat the wire through.

---

### Post by BITstate on 2007-12-24
I have been trying something similiar. I have been trying to use the bluetooth earpiece that came with my phone, to work with the computers Bluetooth dongle so that I dont have the wires in the sound card. The reason for doing this apart from having a completely wireless desktop, is because the cat loves to pull out the mic plug, nothing else, just the mic plug, if I tap it, I think the cat will get angry and eat the wire through.

---

### Post by buccaneere on 2007-12-24
Sound cards which support high-end surround-sound (7.1, 5.1 (maybe)) can turn the mike port into a center channel sound OUTPUT, which might or might not cause a problem with configuration.

Something to keep in mind.........

---

### Post by BITstate on 2007-12-26
I dont understand running the mic as a center channel, he wants to route the headset from the soundcard out to the Bluetooth Dongle so it can be used as handfree with a Cellphone.

How would you direct the headset pluged into the soundcard to the bluetooth adaptor in the first place.  

I have been trying to use the Bluetooth earpiece from my Cellphone, with the Bluetooth Dongle in the computer for skype to keep my desktop totally wireless, and so I can move around and work in the room, while using skype, I still have not worked out how to do that.

---

### Post by buccaneere on 2007-12-28
> **BITstate said:**
> I dont understand running the mic as a center channel, he wants to route the headset from the soundcard out to the Bluetooth Dongle so it can be used as handfree with a Cellphone.

How would you direct the headset pluged into the soundcard to the bluetooth adaptor in the first place.  

I have been trying to use the Bluetooth earpiece from my Cellphone, with the Bluetooth Dongle in the computer for skype to keep my desktop totally wireless, and so I can move around and work in the room, while using skype, I still have not worked out how to do that.

Surround sound-capable cards have driver software that can turn the microphone INPUT port into a center-channel OUTPUT (standard sound output is limited to left and right channels, for stereo separation). If he does have the high-end card, then for starters, the proper drivers need to be loaded to configure the port. It might be by default configured for output...

I'm guessin' that also an auxilliary wireless device is involved, to X-mit from the pc to the headset...

---

