---
title: "looking for a laptop: ATi Mobility or intel X3100?"
date: 2008-04-06
forum: Hardware &amp; Laptops
---

### Post by CC_machine on 2008-04-06
OK, so i need/want a new laptop. my current machine is getting a lil old with the integrated intel 950 for graphics, and i'm sick to the back teeth with the Linux drivers. no shader effects(they work in Sauerbraten in windows) and much lower FPS than in windows. I want to be free, darn it! =[

what I would like:
- Ability to play Sauerbraten (this means support for hardware occlusion queries, Sauerbraten really really needs them to run well) - [http://sauerbraten.org](http://sauerbraten.org) - runs ~20 fps on my intel 950  on small maps, much much less on bigger (SP) maps which is what i really want, since my laptop is portable
- Compiz shouldn't be too much hassle to set up - I hear the X3100 is blacklisted by compiz but there are workarounds which work fairly well :confused:

I can find mostly Dell laptops and Thinkpads with intel X3100 integrated or ATI from like X700 up to X1400 mobility cards or so.

If ATi works i'm sure it'd be the better option... are the new AMD/ATi opensource drivers really good enough to buy an ATi laptop yet, or should i stick to intel :( ?

about nVidia: since ati/amd have been putting in a good effort with opensource drivers I _want_ to support them.. and I've never liked the nVidia blob drivers anyway.

---

### Post by -=Ghostlike=- on 2008-04-06
Ehmm, I have an ATi card in my laptop (X1100 = X300m without dedicated memory) and it's just crappy. In Hardy my system locks up with the fglrx driver on initializing OpenGL at the moment, and my videocards melted 6 times in a year because of external displays with wrong resolutions (if you plug a screen in that has a max resolution of 1024x768 and the laptop screen is set to a higher resolution the driver fails on some devices)

There are no good opensource drivers for < 2k series cards, so if you want ATi you should go vor a 2400 Mobile+ card.

Intel cards are slow. OpenGL 2.0 support will come in september this year I believe so you are years behind when using an intel card with Sauerbraten, lots of OpenGL calls run in software

My opinion as Intel/ATi user is: buy an nVidia ;-)

That's my opinion.

---

