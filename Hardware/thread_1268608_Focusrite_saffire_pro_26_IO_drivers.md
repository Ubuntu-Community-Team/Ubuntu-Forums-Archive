---
title: "Focusrite saffire pro 26 I/O drivers"
date: 2009-09-17
forum: Hardware
---

### Post by paulbent on 2009-09-17
Hi

I'm a newbie and still trying get my head around the whole command line thing... Is there a driver available for the saffire pro so i can use it in Ardour? At this point I'm not even sure Ubuntu studio has recognized my fire wire card. Any tips would be greatly appreciated. I'm sorry if this is a dumb question... I'm trying to learn to navigate the new OS and get some recording at the same time!!

Thanks

Paul

---

### Post by IcarusR on 2009-09-17
Have you tried it to see if it is recognised & works at all ??
It looks like the [[COLOR="Red"]ffado[/COLOR]]("http://www.ffado.org") project supports your device & will provide drivers
Looks like you will have to compile from source.

---

### Post by paulbent on 2009-09-18
Hi
Thanks for the info...After some local help and trial and error I have it recognized on the system but it is unstable. And I can't seem to get the sound back out or monitor through the headphone outputs. Are there any online resources that I could learn about compiling from source code? Should it be in ffado already for Ubuntu studio/ardour?
Thanks
PB



> **IcarusR said:**
> Have you tried it to see if it is recognised & works at all ??
It looks like the [[COLOR=Red]ffado[/COLOR]]("http://www.ffado.org") project supports your device & will provide drivers
Looks like you will have to compile from source.

---

### Post by IcarusR on 2009-09-19
Not familiar with > Ubuntu studio/ardour but as the only info on this item related to Linux was the Ffado project I would guess that it is not supported. Mainly due to ,I would guess, it not being a mainstream device & the manufacturers does not release hardware details needed to create drivers. ie does not support Linux. This means that the likes of the ffado project have to reverse engineer the windows drivers, together with trial & error to get Linux drivers.

Do a google search for howtos on compiling from source, there's loads of info out there.
Any problems you have post & someone will help.

---

