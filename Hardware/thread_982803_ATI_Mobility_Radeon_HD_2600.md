---
title: "ATI Mobility Radeon HD 2600"
date: 2008-11-15
forum: Hardware
---

### Post by Eneekay on 2008-11-15
Hello people! Iwould like to reopen an issue that has been discussed here before: ATI Mobility Radeon HD 2600 problems. I had Ubuntu 8.04 installed and could not get Compiz to work along with OpenGL applications both with Proprietary and Xorg drivers.

Each one works well individually, but when together, OpenGL applications are not displayed well (Slow FPS. "cracks" on the screens, displaying the desktpo from within the application etc.)

Does anyone know if this has been fixed with the latest drivers or with 8.10? Or else, does anyone know a way to fix this for sure? I will not be able to install ubuntu on the meanwhile to test your propositions and I am really sorry for this cause I do not have Ubuntu installed, but I have to work on my machine...

Thank you very much people! I will reply later in the afternoon

---

### Post by Eneekay on 2008-11-15
I have installed 8.10 and will be able to reply to whatever you suggest!

---

### Post by binbash on 2008-11-15
It will not be fixed till DRI2

---

### Post by Eneekay on 2008-11-15
What is DRI2?

---

### Post by thisptr on 2009-02-24
I installed the latest proprietary drivers v9.2 for x86_64 in my laptop (with HD2600 of course). With the former drivers I had not been able to configure my system for dual screen with an hp vs17 monitor. 

The new drivers finally allowed me to use dual head (by using aticonfig with the --initial=dual-head option) and I could not believe my exitement. 3D rendering and compiz were working wonderfully for both screens, however I wanted to be capable of moving windows between the two desktops and for that I had to enable xinerama.

Now I can move windows between desktops but lost the 3D openGl functionality and of course that means compiz is not working. I have read that sun's SPARC opengl brings back the 3D functionality, has somebody tried this?

Thx

---

### Post by drubin on 2009-05-08
> **thisptr said:**
> I installed the latest proprietary drivers v9.2 for x86_64 in my laptop (with HD2600 of course). With the former drivers I had not been able to configure my system for dual screen with an hp vs17 monitor.

Hi Did this ever solve you issue, I am in the same boat I installed the proprietary drivers to get dual head working and ended up disabling compiz..

More importantly then compiz is the dual view though.

---

### Post by arashispencer on 2009-09-20
I've installed this Graphic Card recently and I noticed tt compiz's wobbly window doesn't work like it did on my office's desktop..

I've installed the Kubuntu Jaunty onto my USB HDD and I boot it up once in a while when I need it to be updated as I've no connection at home.

After reading this forums, I noticed that I'm having the same problems like 'cracky' screen on the Kubuntu bootup screen and a lot of desktop effect don't work even after disabled and enabled...

---

