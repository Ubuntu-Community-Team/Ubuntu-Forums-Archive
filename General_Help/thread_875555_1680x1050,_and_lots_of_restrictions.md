---
title: "1680x1050, and lots of restrictions"
date: 2008-07-30
forum: General Help
---

### Post by Seks on 2008-07-30
That's my monitor's preferred res, and I've been working all night to figure out how to use it. Some quality loss is present otherwise.

* system>preferences>screen resolution yaps to me about not supporting the xrandr extention

* nvidia-settings complains that I don't have the x display driver, when I do and it works flawlessly, it even says this with compiz disabled

* command line xrandr -s 1680x1050 says size not supported

* the disableedid tweaks (xorg.conf modification) throws me into something like 400x300 and still won't support the right size

* modelines, modes, metamodes of 1680x1050, tried them all with no effect

Five minutes with google, the monitor's driver, and a custom timing thing got the res to work in windows xp. The question is how to force ubuntu to use it, I've tried everything! Help would be greatly appreciated!

specs:
Nvidia geforce fx 5500 via AGP, acer AL2216 LCD via DVI

---

### Post by kuja on 2008-07-31
That's a weird error for nvidia-settings to be throwing (it really is the easiest way to get your resolution straight so long as it works). I would focus on that issue. Do you have the "nvidia-glx-new" and "nvidia-settings" packages installed? If so, try reinstalling them ```
sudo apt-get remove  nvidia-glx* nvidia-settings
sudo apt-get install nvidia-glx-new nvidia-settings
sudo nvidia-xconfig
```
Then reboot and try this over again ... hopefully this will work.

---

### Post by Seks on 2008-07-31
Just checked, yah I have that one installed. I'm guessing it's the [Option "NvAGP""1"] that messes it up, but if I remove it ubuntu won't even load (or load a little and then freeze), requiring me to fix the xorg.conf with a live cd.

---

### Post by kuja on 2008-07-31
Hmm, well, it is a fairly old card, perhaps it would behave better with the older drivers instead? Lets find out?

```

sudo apt-get remove nvidia-glx-new && sudo apt-get install nvidia-glx

```

Then Restart X (log out, then ctrl+alt+bksp)

Then log back in and go to nvidia-settings and see if it wants to play nice ... we can hope :)

---

### Post by Seks on 2008-07-31
update


I got both the nvidia settings and the resolution thingy to work by removing xserver-xgl, weird since I thought that was like a core part of the system. Didn't seem to affect anything.

Problem is my resolution isn't listed and it says no valid modes for it in the log :(

The worst part is the monitor wrongly reports the native res as 1600x1200, gonna mess with the control panel some more...

---

### Post by kuja on 2008-08-01
XGL isn't critical ... it's an alternative X Server. 
>  Xgl provides a GL-based X server, performing its drawing through a GL stack. In combination with a GL-based compositing manager, this allows for high-speed transformations of windows.


It's generally not considered to be requisite with an nvidia card, especially seeing as it has some major drawbacks. (opengl apps are hard to get to work with xgl).

I'm not sure about the other part ... I probably won't really have any time to look around until Monday, until then, take a look at this: [http://help.ubuntu.com/community/FixVideoResolutionHowto](http://help.ubuntu.com/community/FixVideoResolutionHowto)

---

