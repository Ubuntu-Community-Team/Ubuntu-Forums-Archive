---
title: "Acer TravelMate 2480-xxxx Laptop (Intel 945 Graphics Card Issues)"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by Espionage724 on 2007-04-28
I have a Acer 2480-xxxx Laptop
I am running Kubuntu 7.04

I am trying to get direct rendering to be enabled on my Intel 945 card. It was enabled once before but for some reason its not enabled anymore. I want direct rendering enabled so that I can play World of Warcraft. Any tips?

---

### Post by Angry penguin on 2007-05-04
People in this thread are reporting the same issues with the intel 950 chipset doing the same thing, working for a while then stopping. Perhaps this can shed some light.

[http://ubuntuforums.org/showthread.php?t=358380&highlight=acer+travelmate](http://ubuntuforums.org/showthread.php?t=358380&highlight=acer+travelmate)

sorry i couldnt be of more help.

---

### Post by ramjet_1953 on 2007-05-05
Are you using 915resolution as the graphics driver?

If so, try removing it and using Synaptic download the package [COLOR="Red"]xserver-xorg-video-intel[/COLOR] .
After this is done, do a re-boot.

If you are using 7.04. there should be nothing else to do. It should detect the optimum setting for you screen and also add all of the resolution options in the selection menu.

This new driver is supposedly much better at switching resolutions "on the fly", when playing games.

Regards,
Roger :cool:

---

