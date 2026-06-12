---
title: "External Soundcard fully working with Ubuntu"
date: 2009-11-11
forum: Hardware
---

### Post by usercontrol on 2009-11-11
Hi!

After upgrading ubuntu 9.04 to 9.10, pulseaudio says that my Toshiba Multimedia Center soundcard is 4.0, but this is fake, because it's 5.1 surround sound card.

I'm tired by searching for good pulseaudio/alsa config, so I'm looking for external sound card fully working with Ubuntu.

My preferences:
* USB or ExpressCard interface
* full support in ubuntu
* 5.1 or 7.1 surround sound

I found Creative Extigy and Creative USB Sound Blaster X-Fi Surround 5.1, but I'm not sure that those cards will work fine.

What do you recommend?

---

### Post by Carrot.nl on 2010-01-14
Did you find anything? I'm looking for the same thing.:)

---

### Post by usercontrol on 2010-01-14
unfortunately no. I bought Audigy2 ZS Notebook for the same price. Pulseaudio in 9.10 suck.

---

### Post by Carrot.nl on 2010-01-14
Thanks for the quick response. I did a quick search and it looks like that card is supported. Can you recomand this card or did you run into problems wich ara hard to solve?

Carrot.nl

---

### Post by gtippitt on 2012-12-19
Even though this is an old message, I am posting this reply in case others are still looking for a solution with 5.1 on the Extigy.  I had a Creative Sound Blaster Extigy USB sound adapter that worked great with Ubuntu before PulseAudio, but has not worked with 5.1 since PulseAudio.  The Extigy worked with OSS, but not with PulseAudio.

I switched to a Zalman ZM-RSSC External USB 5.1 Sound Card , which works fine with Pulse and 5.1.  The Zalman RSSC is a discontinued product that you can still find really cheap on eBay, so I bought an extra to put away as a spare, since most USB sound adapters have fake 5.1 that simply upmixes the stereo to the other channels.

The Extigy has many features that the Zalman will not do, such as decoding digital input from my DVD player to the 5.1 analog on my Yamaha amplifier without the computer doing anything. I still use the Extigy for my DVD player, but it is no longer connected via USB to the PC running Ubuntu.  I have the Zalman for the PC running MythTV for sound output in stereo or 5.1.  I tried several USB sound adapters, but most didn't really do 5.1.  My wife and I are both hard of hearing, so I wanted to be able to separate the center channel dialog louder than the sound effects.  

I hope this helps others with Extigy USB sound adapters that need something else.

---

