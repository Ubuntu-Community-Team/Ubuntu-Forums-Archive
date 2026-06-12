---
title: "nVidia GTX 280 Problems"
date: 2011-02-17
forum: Hardware
---

### Post by jdb91 on 2011-02-17
Hi all,

Just put 10.10 on my new box and having problems with gfx drivers.  Basically, it was running in 800x600 through the install and then when finished, prompted me to install 3rd party driver for the nVidia card, which I let run.  I could then get a max of 1200x800 res which is no where near what I usually run on that monitor which is 1600x1200.

So I got the proper driver off the site, installed it and now (maximux) is 640x320 which is pretty hard work to use!

And suggestions?

---

### Post by cascade9 on 2011-02-17
Sounds like yoru monitor didnt report the EDID properly. 

Manually installing the drivers from the nvidia site just makes your life harder. Personally, I'd remove them and get the drivers via jcokey.  

sudo apt-get --purge remove nvidia-*

You dont have to do that though. 

To get 1600x1200, try using the 'detect displays' button in nvidia x server settings. If that doesnt work, you might have to edit the config file to give you 1600x1200.

---

### Post by jdb91 on 2011-02-17
Ah ok, that makes sense as the monitor is actually a tv with a VGA input, so may not be that good at compatibility.  Can you point me in the direction of the config file (I'm assuming it's the x conf) it's been a while since i manually intervened with one.

---

### Post by cascade9 on 2011-02-17
/etc/X11/xorg.conf.d

By defualt there is no xorg.conf. You might need to save the nvidia configuration file there before it appears (lauch with "gksudo nvidia-settings", go to 'x server display configuration', hit the 'save to x configuration file' button).

---

### Post by jdb91 on 2011-02-17
Thanks for the help, will try it this evening.

---

### Post by cascade9 on 2011-02-17
No problem, good luck ;)

---

### Post by jdb91 on 2011-02-23
Added it but can't get it to work :/

---

### Post by cascade9 on 2011-02-24
Which bit didnt work? 

BTW, I havent ever seen a TV that does 1600x1200. What TV is it?

---

### Post by jdb91 on 2011-02-24
Generated the xconf file and tried to force 1600x1200.  It's a cheap Vistron, but I always run it at that res and it performs fine.  It's not bluffing on the OS either, if I go into info, it says 1600 x 1200 @ 70Hz.

I also tried using xrandr but i just kept getting the error "Cannot calculate gamma" or something very similar.

---

