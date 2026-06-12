---
title: "Getting HDMI audio 2 work?"
date: 2010-03-18
forum: Hardware
---

### Post by GeoPrude on 2010-03-18
Is it actually possible? I have tried messing around with the sound settings for ages but it just doesn't seem 2 work, even though there is an HDMI tab in the audio manager.

---

### Post by tilixibr on 2010-03-18
same thing here. 
I was using a Toshiba Sattelite A300 and i plugged the HDMI cable from the TV to the laptop and I only got the image but no sound. And I also had the HDMI tab just like you!!!
I had to use the speakers. No big deal since the laptop speakers are great!(harman/kardon):p

---

### Post by Bullwinkle_Moose on 2010-03-19
From a terminal prompt, try this:

amixer -c 1 sset 'IEC958' unmute

More info (somewhat buried) in this article: [http://michigantelephone.wordpress.com/2010/01/01/some-notes-on-creating-a-home-theater-pc-using-the-acer-aspire-revo/](http://michigantelephone.wordpress.com/2010/01/01/some-notes-on-creating-a-home-theater-pc-using-the-acer-aspire-revo/)

---

### Post by Goveynetcom on 2010-03-20
I'm in the same boat, HDMI outputs video, but no audio. I was playing with the setting but I don't have anything HDMI to output right now, and I am not on my laptop right now.

I will post back later with any info I dig up.

Here's to good luck :popcorn:...

---

