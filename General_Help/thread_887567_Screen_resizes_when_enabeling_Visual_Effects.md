---
title: "Screen resizes when enabeling Visual Effects"
date: 2008-08-12
forum: General Help
---

### Post by Pff on 2008-08-12
Hi!

I'm having a problem with the desktop (or whats it's called) when I enable "Normal Visual Effects" or "Extra Visual Effects" in the "Appearance" window. I's seems like it resizes itself to 1400x1050 instead of keeping the 1680x1050 resolution. This renders a black bar (280 pxl wide, I guess) on the right hand side of the screen. I can see the mouse pointer when I hold it over the area, but windows and toolbars disappear. 

I have all drivers installed and working for my graphics card (Mobility Radeon X1600).


Does anyone know what might be the problem? 

Cheers!

//Pff

---

### Post by tuxxy on 2008-08-12
I had issues with ATI drivers and flawless compiz effects and even simple 3D graphics.  Never solved them completely until I upgraded to nvidia :)

---

### Post by Pff on 2008-08-12
I had those problems too before. Even the game "GNOME" that's included in 8.04 made my computer impossible to use :)

But that has been taken care of, and now it works fine. I just can't figure out what causes that black bar on the right.

Is there any options or conf-files for the visual effects?

---

### Post by tuxxy on 2008-08-12
Yes, I have ATI's catalyst control centre to play with settings although I wouldnt bet on it fixing all your ATI drivers issues

---

### Post by Pff on 2008-08-12
Well, I tried with the Catalyst Center. There where not any useful options at all in there...

I'm getting a feeling its not a driver related problem, but more of an config problem. There really isn't any options for the visual effects in the "Appearance" window?

---

### Post by lgsiller on 2008-09-02
I have the exact same problem here. I just configured my xorg.conf file with the open source ATI driver. I checked for direct rendering and it said "yes". So I went to the visual effects and enabled extra. For some strange reason a black bar renders to the right side of my screen. If i use 1024 x 768 resolution the black bar disapears, but this resolution is not the best fit for my laptop (HP pavilion zt3000). So anybody could help us out?? I need 1280 x 800 and the black bar is so annoying.

Please help.

---

### Post by cbaoth on 2008-12-06
Hi!

I had the exact same problem today when I reconfigured xorg (complete new config). In my case it's NVidia, but since it was a general xorg option that lead to the error, it may be the same thing.

In my case it was a false ModeLine entry in my xorg.conf. My second display only supports a maximum res. of 1280x1024, but for some reason the nvidia-settings app added a modeline for 1400x1050. Despite the fact, that my metamode option (in my screen section) stated, that display one should be 1920x1200 and two 1280x1024, I got a black bar on the right side of my second display (where the displays are split). When I commented out the mismatching modeline (so that 1280x1024 was the max resolution of my second display) the black bar was gone.

---

