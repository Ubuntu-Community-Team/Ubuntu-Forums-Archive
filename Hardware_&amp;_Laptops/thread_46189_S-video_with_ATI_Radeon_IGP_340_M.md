---
title: "S-video with ATI Radeon IGP 340 M?"
date: 2005-07-03
forum: Hardware &amp; Laptops
---

### Post by anno on 2005-07-03
Hello!
I am getting into this Ubuntu/Kubuntu world. Now more and more seem to work, but still some problems.
Getting my s-video connection to tv seems to be a problem. I have searched all over for info about help for my
graphics card, ATI Radeon IGP 340M in a HP pavilion ze5500 notebook. 
What I have concluded so far is that ATI does not support linux as well as Nvidia, but is there still possibilities for
making the s-video cabel work. That would be nice, since I'd like to connect my pc to the TV for multimedia purposes. Can anyone help me?

---

### Post by mtron on 2005-07-03
i do not have this graphics card, but try to follow the guide 
[http://www.rage3d.com/content/articles/atilinuxhowto/Linux_ATI.html#SECTION000143000000000000000](http://www.rage3d.com/content/articles/atilinuxhowto/Linux_ATI.html#SECTION000143000000000000000)

start with something easy, like clone, if it works backup your xorg,conf file, and try some better configuration

it needs some reading and investigating, but the xorg.conf file is pretty easy to understand. just do not forget that you need two definitions for monitors & device, ect.

---

### Post by anno on 2005-07-03
[QUOTE=mtron]i do not have this graphics card, but try to follow the guide 
[http://www.rage3d.com/content/articles/atilinuxhowto/Linux_ATI.html#SECTION000143000000000000000](http://www.rage3d.com/content/articles/atilinuxhowto/Linux_ATI.html#SECTION000143000000000000000)

start with something easy, like clone, if it works backup your xorg,conf file, and try some better configuration
it needs some reading and investigating, but the xorg.conf file is pretty easy to understand. just do not forget that you need two definitions for monitors & device, ect.[/QUOTE]

Thanks for the suggestion. I have tried some more with these drivers now, but they seem to knock out the X-server. I use the xorg and it wants X86 or something. I think this graphics card is not so supported. Ubuntu uses something called "mesa" and it works ok, but no choices for s-video.

Not sure what to try next...

---

### Post by ag65151 on 2007-07-31
I got it to work, but it is not pretty. I also have an HP ZE5500 with ATI Radeon 330M/340M/350M card. 

The first thing I did was get the console tool "atitvout". It is available on Synaptic [Miscellaneous - Text Based (Universe)] Then, make sure you boot with the s-video cable connected and the TV on.

Once you can get to a terminal, you use the tool to switch modes:

> sudo atitvout -f t (forces the tool to treat your card like an ATI Rage card and enables the tv-out port)

> sudo atitvout -f l (switches back to the built in display - lcd)

I say it doesn't work so well because it just completely shuts off the lcd and transfers all video to the tv. I have my screen resolution at 1024X768 and that is blurry on my TV. But it works well for Impress presentations that have large letters which is all I needed it for. 

Once again, it is not an elegant solution, but it marginally works.

---

### Post by zkeng on 2007-08-15
Have you checked this tread?

[http://ubuntuforums.org/showthread.php?t=382333&highlight=igp+340](http://ubuntuforums.org/showthread.php?t=382333&highlight=igp+340)

---

