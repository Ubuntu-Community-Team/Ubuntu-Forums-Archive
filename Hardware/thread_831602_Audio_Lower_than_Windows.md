---
title: "Audio Lower than Windows"
date: 2008-06-17
forum: Hardware
---

### Post by open_coder on 2008-06-17
I noticed a problem recently that has me a little irritated. In windows the audio coming out of my headphones is a lot lower than in Windows. At first I thought maybe my headphones were going bad, but when I went to the computer lab on campus, the audio was much much louder using the same set of headphones.

Is there a way to increase the volume level of the headphone jack to match the one coming from windows?

--Alex

---

### Post by powerpleb on 2008-06-17
There is the volume app in the task bar (obviously). You can also fiddle with alsamixer which I suppose gives you lower level control.
Open a terminal and type 'alsamixer'

---

### Post by open_coder on 2008-06-17
Thats the problem. The max volume in Ubuntu is nowhere near as high as the max in Windows. And I already used alsamixer. I am running Kubuntu-KDE4 Remix. Is there something with the driver that I can do to fix it.

---

### Post by Pjotr123 on 2008-06-17
Install alsamixergui. Make sure that all sliders are visible in that app (maximize the window). Note: don't have all sliders open at the same time and don't put any slider at above 90 % (distortion).

---

