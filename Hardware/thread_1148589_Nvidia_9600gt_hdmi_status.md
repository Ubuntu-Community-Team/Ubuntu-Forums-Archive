---
title: "Nvidia 9600gt hdmi status?"
date: 2009-05-04
forum: Hardware
---

### Post by Mazehero55 on 2009-05-04
Hey I'm having trouble setting up my brother's computer with windows. The problem is the Nvidia driver is coupling analog audio through the hdmi cable which we can't set the LCD to pick up. 

I have Ubuntu on my computer and I heard people have gotten it to work correctly in Linux. So he's letting me put Ubuntu on it with wubi to test it out. I'm just wondering sense it's connected to an hdtv through an hdmi cord will ubuntu set this up to work immediately or will I have to edit the xorg.conf to set it up to do that?
If I have to edit xorg what will I need to put in to enable hdmi output?

I have installed ubuntu 8.10 and it won't show a picture on it, I'm waiting to get my hands on the recent update of ubuntu to try that. In the mean time I'd like to play around with setting up hdmi on 8.10 so I'm not lost if I have trouble with 9.04. 

Thanks to the wonderful ubuntu community^^

---

### Post by Mazehero55 on 2009-05-06
bump?
does anyone know how to add hdmi to the xorg?

---

### Post by Gausian on 2009-05-07
Sending the picture over to an hdtv is pretty simple really.  just open your nvidia settings and switch it over to the tv.

you may need to adjust resolution and such.

as for audio, im not really sure i understand you problem there, but i got it to work by enabling it in the volume control settings of ubuntu.

---

### Post by Mazehero55 on 2009-05-07
I got a new cd of Ubuntu 9.04 and here's the problem really, I only have an hdtv that came with it. I suppose I can borrow a monitor and bring it over to his house but that'd be a pain with only a motorcycle as transportation. 
I've gotten it to work okay by setting the driver to 'vesa' but that's to basic for what he needs, and when I set it to 'nv' the hdtv stops getting a signal or a usable signal at least. 
I don't want to use the nvidia driver because it cause the audio problem to happen again(when it's on vesa there is sound)

I want to use the open source nv driver to have more advance graphics and still have sound. This is why I need to know how to set it up in xorg.conf cause once I set it on 'nv' I'm stuck with text mode until I can set it up right lol^^

Thanks

---

### Post by xur17 on 2009-05-28
This question is for anyone that has this card.  Does the card support dual screens (2 monitors).

Also, would a hdmi to dvi adapter work for this?

---

