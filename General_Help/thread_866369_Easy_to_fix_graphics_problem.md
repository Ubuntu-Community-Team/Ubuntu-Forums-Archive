---
title: "Easy to fix graphics problem"
date: 2008-07-21
forum: General Help
---

### Post by infiniah on 2008-07-21
**How would I remove my graphics drivers?** I think they installed incorrectly because my top resolution is only 800x600, desktop effects wont enable, and when Ubuntu starts it doesn't display that fancy NVIDIA logo like it used to before I reinstalled Ubuntu.

[I]Any help is very appreciated. I'll be watching this thread for any comments.

If you need to know what video card I have, it's a GeForce 9600 GT.
The drivers that are on now and that are not functioning correctly are the ones from [NVIDIA.]("http://www.nvidia.com/object/linux_display_ia32_173.14.05.html")
[/I]

---

### Post by infiniah on 2008-07-21
_**[COLOR=Red]Bump.[/COLOR]**_

---

### Post by rogier.de.groot on 2008-07-21
By "the one from NVIDIA" you mean you went to their website and downloaded it? Or did you let the restricted driver manager do it for you? The latter option is, IMHO, better unless you have some special reason to want otherwise. Also, install the handy nvidia-settings program to help you configure. The NVidia logo thing is disabled by default now, BTW.

---

### Post by infiniah on 2008-07-21
Oh damn, I screwed things up bad on here... well I'm just going to reinstall!

---

### Post by prince_niceguy on 2008-07-21
download envy and use it to install your drivers. you may not be required to reinstall if you tell what is screwed up.

---

### Post by infiniah on 2008-07-21
Okay so I reinstalled Ubuntu, and I have just finished restarting from installing the updates. The only thing I have installed so far is the "Linux Restricted Drivers" from the SPM.

Envy.
I searched that the keywords "envy" on the SPM, and I would like to know what is the exact file name?

*envyng-core?*

---

### Post by infiniah on 2008-07-21
Bump

---

### Post by prince_niceguy on 2008-07-22
[http://albertomilone.com/envyngfaq.html](http://albertomilone.com/envyngfaq.html) is where you would find envy

---

### Post by Rhubarb on 2008-07-22
Or just grab it from the repositories:
```
sudo aptitude install envyng-gtk
```
Then install the drivers using envy:
Applications --> System Tools --> EnvyNG

---

### Post by rogier.de.groot on 2008-07-22
Many people are Envy fans, but it never worked quite right for me; I stick to the restricted driver manager thing. What exactly is so special about Envy anyway?
Anyway, like I said before, the nvidia-settings program might help you configure graphics.
Good luck.

---

### Post by Rhubarb on 2008-07-22
> **rogier.de.groot said:**
> What exactly is so special about Envy anyway?
Envy allows you to have the latest nvidia drivers installed.
The latest nvidia drivers (from envy) fix up a few bugs that the nvidia drivers from the restricted driver manager offer.
Such as corrupted textures in UT2004, and big problems with sauerbraten ctf edition (the old nvidia drivers only work with all shaders turned off).
The latest nvidia drivers fix up all these problems (that some people may experience with a few games).

---

### Post by danwood76 on 2008-07-22
Envy is nasty. It often misconfigures things and is about as useful as a chocolate tea put.

I bet you had the drivers installed correctly but a wrong config in your xorg.conf file.
The nvidia drivers are quite annoying in the sense that they try and not use the xorg.conf which leads to lots of problems in Ubuntu.
A wrong setting in there will cause issues so its a good idea to reconfig it automatically.

Run this from the terminal to do a reconfig:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

---

