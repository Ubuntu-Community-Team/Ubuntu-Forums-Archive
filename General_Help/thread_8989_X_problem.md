---
title: "X problem"
date: 2004-12-23
forum: General Help
---

### Post by techn9ne on 2004-12-23
I don't think I changed anything but now when I load ubuntu and it tries to load the login screen it flashes a bunch of time and gives me error msg.

Its saying that it cannot find a usable display.

How can I reset settings or fix this?

---

### Post by cacofonix on 2004-12-23
You need to reconfigure X and change the driver for your video card. What driver did you pick and what type of card do you have?


cacofonix

---

### Post by techn9ne on 2004-12-23
I'm using a nvidia card.

I got it from apt-get using these instructions : 

[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

---

### Post by nemin on 2004-12-23
[QUOTE=techn9ne]I don't think I changed anything but now when I load ubuntu and it tries to load the login screen it flashes a bunch of time and gives me error msg.

Its saying that it cannot find a usable display.

How can I reset settings or fix this?[/QUOTE]
Maybe you can post the exact error message here, it might give more detailed informatie about the problem...

---

### Post by Bagleemo on 2004-12-23
I have the same problem after performing a smart upgrade in Synaptic that included (I think) the newer Xfree86 and newer Nvidia driver / (X server?) .

If someone can tell me how to dump install history from Apt-get I can figure out the exact packages - (I can still boot to command line in safe mode.)

The problem seen is that during boot I only get the the Nvidia splash, then the X cursor and a blank background. When I move the cursor I get an error message saying something to the effect of the X server cannot find a suitable display and would I like to  try another one.  When I do the problem just repeats itself.

I have an Nvidia graphics card as well.  Athlon xp 2800, 512 ram, NForce motherboard.  Been good and stable with Ubuntu since release until this update fragged me. 

Tried going into XFree86-4 and changing the Nvidia line back to NV.... but this didn't help.  What is best course of action?  What other information would be useful?

Thanks -

Amos

---

### Post by techn9ne on 2004-12-23
Ok It happened after I installed firefox 1.0 from the hoary branch...

I've tried uninstalling and reinstalling the package "xserver-xfree86" and that didn't work.

I can drop to command line kill the X server manually login via console and then go "startx" and it loads up ok.

Is there any way to fix this without having to reinstall ? If I reinstall will I lose all my settings and email?

 ](*,)

---

### Post by techn9ne on 2004-12-23
Further explanation of the problem on boot is identical to that of what Bagleemo just posted.

---

### Post by techn9ne on 2004-12-26
I tried uninstalling, reinstalling all x packages. I setup backport project to re-download firefox. I tried uninstalling that completely and reinstalling from cd.

I ended up backing everythign up and reinstalling. Theres a wiki guide on here on updating to firefox 1.0 using pinning. Should be changed to using backport project so ppl dont follow it and break their systems.

---

### Post by nemin on 2004-12-26
[QUOTE=techn9ne]Ok It happened after I installed firefox 1.0 from the hoary branch...

I've tried uninstalling and reinstalling the package "xserver-xfree86" and that didn't work.[/QUOTE]
sudo apt-get install gdm was the only thing I needed. Are you sure that doesn't work for you?

---

### Post by Chokableu on 2004-12-29
I had the same problem when using synaptic to get the nvidia driver : the Xserver crashed then and I reinstalled Ubuntu.  My ubunta has been running smoothly for a few days before this. 
I had the same problem when I tried upgrading Firefox fom Hoary.

Another problem : my monitor is only recognised as a generic one, though it is a Mitsubishi DiamondTron 930SB Pro. I guess that is the reason why Ubuntu sets the refresh rate to 60 Hz although my NVidia card (GeForce FX5700) can handle higher refresh rates for this monitor.
I hope this NVidia problems will get solved soon, because it's a real drawback in an otherwise very good Linux distribution.

---

