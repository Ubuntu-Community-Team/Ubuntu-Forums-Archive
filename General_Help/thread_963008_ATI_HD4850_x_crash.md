---
title: "ATI HD4850 x crash"
date: 2008-10-29
forum: General Help
---

### Post by crembz on 2008-10-29
Hi,

I've been using ubuntu as my main system for the past 3 or 4 months now. After years of hopping on and off the linux bandwagon, I had finally managed to get everything setup the way I wanted.

Last week I upgraded my graphics card from a Nvidia 7800gt to the ATI hd4850. I have always had issues running ati with linux but I couldn't look past the price/performance ratio atm ... ati wins handsdown at this price point.

Anyways, took me a while to get gnome up and running after installing the latest official drivers from the ati site. I thought all was looking good but I've noticed that every hour or so the system hangs completely. I have compiz and emerald enabled for visual effects and I'm happy to turn these off if it's really necessary. 

I've tried looking for a solution but I have the feeling this is 4850 specific issue and not ati specific. My laptop has a mobility x1400 and it runs fine in a similar setup with compiz.

Can anyone point me in the right direction. I would HATE to go back to using windows after all this.

---

### Post by nitrousoxide82 on 2008-10-29
Check the temperature of your 4850. I have one of them (made by Powercolor) and so far had no issues, but its idle temperature is way too high. This is specific to early-run 4850's, and luckily there is a driver-based workaround for that (as with Windows). To check the temperature, run [font="Courier New"]aticonfig --odgt[/font] on a terminal (you may have to run [font="Courier New"]sudo aticonfig --initial[/font] before, to initialize some xorg.conf settings for the fglrx driver). Mine idles on 80 something degrees C (which is fairly high). This is due to a firmware issue in our cards that is too aggressive (in terms of generated noise) and keeps the fan running at a very low speed until the GPU is about to cook itself. Use [font="Courier New"]aticonfig --pplib-cmd "set fanspeed 0 xx"[/font], with xx varying between 40 and 70 depending on the noise level/cooling desired, to speed up the fan "by hand". You may want to put this command into [font="Courier New"]/etc/gdm/Init/Default[/font] (edit it and add it at the end of the script) so that the fan ramps up as soon as X starts.

---

### Post by crembz on 2008-10-30
Thanks I'll try that ... i have a powercolor 4850pcs+ which is factory overclocked and has an aftermarket cooler on it ... The reviews said it's meant to run about 20 degrees cooler. 

I have vista installed for games and can game for hours without a single hitch (no stuttering or artifacts so id say no heat issues) yet it crashes in ubuntu on the desktop. I read that ATI drivers don't like openGL and 3D stuff in linux ... is this true?

---

### Post by Yashiro on 2008-10-30
My 4850 runs OK. I doubt your issues are heat related either.
It's more likely to be a driver install problem. Check this guide [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Of course it is worth trying the aforementioned fanspeed change first.


Where did you discover the aticonfig --pplib-cmd "set fanspeed 0 xx" command by the way nitrousoxide82?
I've not seen this anywhere else before yet it does indeed work.

---

### Post by nitrousoxide82 on 2008-10-31
> **Yashiro said:**
> My 4850 runs OK. I doubt your issues are heat related either.
It's more likely to be a driver install problem. Check this guide [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Of course it is worth trying the aforementioned fanspeed change first.


Where did you discover the aticonfig --pplib-cmd "set fanspeed 0 xx" command by the way nitrousoxide82?
I've not seen this anywhere else before yet it does indeed work.

I found it in another thread here in the Ubuntu forums. Do a search, I don't quite remember the exact post (thanks to the people there again, my 4850 now runs a good 20°C cooler than without the workaround. Good while it waits for me to install an aftermarket cooler ;) )

[quote=crembz]I read that ATI drivers don't like openGL and 3D stuff in linux ... is this true?[/quote]

Seems so. Many things DO work, but I have been experiencing some issues with [font="Courier New"]fglrx[/font] and some OpenGL applications. Also, Direct3D emulation in Wine won't work for me. Compiz is OK here so far but I've seen people complaining elsewhere. I'd say, sure ATI/AMD improved a lot on Linux, but they've still got to catch up (or maybe the surfacing of an open-source 3D driver will improve things in the future, as has already happened for the older Radeons).

---

