---
title: "Latency with NVIDIA Prime"
date: 2016-03-29
forum: Hardware
---

### Post by b_f2 on 2016-03-29
Hi,

After using Bumblebee to control the graphics switching on my NVIDIA Optimus laptop (GeForce 540M card), I decided to try Prime as I heard the fps was a lot higher.

And apparently it's true, the fps *is* a lot higher (going from 45fps to 90fps with a *higher* resolution :p). However, I also seem to be getting a constant latency/input lag on anything I do. For reference, the main game in question is Team Fortress 2 that I'm having a problem with. I have run steam from terminal with[I] 

    __GL_SYNC_TO_VBLANK=0 

[/I]as well as putting that same line in my launch options. Curiously, even before I used this line, turning vsync on or off did nothing (I hear you can't actually use vsync on Prime).

So, my question is, has anyone else experienced a sudden jump in latency/input lag since making the Bumblebee -> Prime switch and if so how'd you fix it?

Thanks for any replies!

---

### Post by Niklashbg on 2016-04-17
Hi b_f2,

I too have an issue with display output latency when using Nvidia PRIME. Compared to Intel graphics via MOBO and video output straight from the graphics card, the lag is annoyingly noticeable. Especially when playing games like CS:GO. Looking for a solution as well!

---

