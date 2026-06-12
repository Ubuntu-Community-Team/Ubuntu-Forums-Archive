---
title: "Forcing a screen resolution and save it"
date: 2013-09-14
forum: Hardware
---

### Post by Fidle_Robichaud on 2013-09-14
Hi everyone,

On my HDMI port of my videocard, i've installed and HDMI splitter to send the same signal to a 24" DEL monitor and an 55" HD TV. Because of that, it become an "Unknow Device" and the highest resolution is 1024x728. It's easy to force the resolution with xrandr and adding the 1920x1080 to those screen, and it work well, my question is not for that. The problem comes when i logout or reboot the computer. I got an error message for my screen resolution (That the unknow device don't support the resoluton) and i'm back with a screen in 1920x1080 and the other with the 1024x728 resolution. Oh and also, it reverse my main screen and the secondary (The HDMI one is my secondary, and the DVI one is my main)

I was thinking of editing the Xorg.conf file to try to solve the problem, and i noticed that files don't exist anymore in /etc/X11/Xorg.conf . I've searched on google and on this forums, but i don't see any answer to that problem.

So can someone please explain me just how to simply save that forced resolution and how to save the new primary screen to the DVI one (instead of HDMI). It's a little bit frustrating to always redo the same thing each time i login.

Thanks guys

---

### Post by CatKiller on 2013-09-15
xorg.conf isn't there by default any more but it will be used if you create one.

---

### Post by grentthevampire on 2013-09-15
i used to have the same problem... although my solution wasnt the cleanest approach what i simply did is to add the codes i used in making the resolutions into a new startup application... copy-ing and pasting the codes into the command field

---

