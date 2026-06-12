---
title: "Nvidia restricted drivers problem"
date: 2008-07-24
forum: General Help
---

### Post by GeordieToddy on 2008-07-24
Hi, I used to have a fully working desktop using the restricted Nvidia drivers for my graphics card (GeForce 7900GS), however I also have a Creative X-fi sound card which didn't work, so I tried recompiling the kernel so I could use my sound with ALSA (using this guide: [http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675)).

After much fannying around, I now have sound that works perfectly, but no restricted Nvidia drivers and so no desktop effects. Plus, I am a simple man - I liked the pretty colours, and now I'd like them back. I've tried reinstalling the drivers manually, but although the installer completes without errors and says that all went well, GNOME still doesn't recognise that they're there in the 'System->Administration->Hardware Drivers' dialog, and so desktop effects are stuck on 'none' ;(

Please help if you can, even if you're not sure it'll work, I'll give it a try....

....I LONG FOR THE CUBE!

Thanks, Toddy.

P.S. Running Hardy on a Dell XPS600.

---

### Post by tuxxy on 2008-07-24
Try the restricted drivers, in terminal;

```
jockey-gtk
```

Download Envy and try and install the drivers again;

```
sudo apt-get install envy-gtk
```

---

### Post by GeordieToddy on 2008-07-24
I tried that and got this:

E: Couldn't find package envy-gtk


EDIT:
ok, found envyng-gtk instead, which i think is what you meant for me to get...

but it changed nothing unfortunately.
Gonna try rebooting to see if it makes a difference - will edit this post in 5 mins according to what happens - brb.

EDIT2:

envyng-gtk did nothing, so i tried nvidia-glx-envy instead, and that destroyed my sound....

bugger.

---

### Post by GeordieToddy on 2008-07-25
Just something to add, when I tried jockey-gtk in terminal, the output was this:

```
WARNING: modinfo for module fglrx failed: modinfo: could not find module fglrx

WARNING: modinfo for module nvidia_new failed: modinfo: could not find module nvidia_new

WARNING: modinfo for module nvidia failed: modinfo: could not find module nvidia

WARNING: modinfo for module nvidia_legacy failed: modinfo: could not find module nvidia_legacy

```

Does this help?

---

### Post by GeordieToddy on 2008-07-25
*BUMP*

:eek:

---

### Post by GeordieToddy on 2008-07-25
BUMP!!!

hehehe.

XD

---

### Post by Neo0351 on 2008-07-25
you can try installing the nvidia drivers manually.  first download the drivers
for 32bit
[http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.05/NVIDIA-Linux-x86_64-173.14.05-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.05/NVIDIA-Linux-x86_64-173.14.05-pkg2.run)
for 64bit
[http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.05/NVIDIA-Linux-x86_64-173.14.05-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.05/NVIDIA-Linux-x86_64-173.14.05-pkg2.run)
then install following this thread
[http://ubuntuforums.org/showpost.php?p=4558708&postcount=37](http://ubuntuforums.org/showpost.php?p=4558708&postcount=37)

---

### Post by GeordieToddy on 2008-07-28
> **Neo0351 said:**
> you can try installing the nvidia drivers manually.  first download the drivers
for 32bit
[http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.05/NVIDIA-Linux-x86_64-173.14.05-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.05/NVIDIA-Linux-x86_64-173.14.05-pkg2.run)
for 64bit
[http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.05/NVIDIA-Linux-x86_64-173.14.05-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.05/NVIDIA-Linux-x86_64-173.14.05-pkg2.run)
then install following this thread
[http://ubuntuforums.org/showpost.php?p=4558708&postcount=37](http://ubuntuforums.org/showpost.php?p=4558708&postcount=37)

Thanks, but this is the installer that I used in my first attempt(s), which wouldn't work - and it messed my sound up... :(

---

### Post by ktrnka on 2008-07-29
can you provide the output of:

```
cat /etc/X11/xorg.conf
```

---

### Post by GeordieToddy on 2008-07-30
> **ktrnka said:**
> can you provide the output of:

```
cat /etc/X11/xorg.conf
```

Sure, here it is:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

---

### Post by GeordieToddy on 2008-08-02
bump...

---

### Post by crazyrk on 2008-08-02
I'm having this problem too, after trying to install the newest version of drivers by nvidia.com, and even after uninstalling and reinstalling ubuntu/envy/nvidia's restricted driver, my problem is almost exactly as his :(

---

### Post by GeordieToddy on 2008-08-03
> **Neo0351 said:**
> you can try installing the nvidia drivers manually.  first download the drivers
for 32bit
[http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.05/NVIDIA-Linux-x86_64-173.14.05-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.05/NVIDIA-Linux-x86_64-173.14.05-pkg2.run)
for 64bit
[http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.05/NVIDIA-Linux-x86_64-173.14.05-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.05/NVIDIA-Linux-x86_64-173.14.05-pkg2.run)
then install following this thread
[http://ubuntuforums.org/showpost.php?p=4558708&postcount=37](http://ubuntuforums.org/showpost.php?p=4558708&postcount=37)

In an attempt to try absolutely anything to get my desktop back the way it was, I decided to try your advice and risked my sound breaking...

IT WORKED! I've got my desktop effects back, but... i lost my sound again. :(

so... back to the creative x-fi threads, but at least I can do it with a decent looking cube...

@crazyrk:
let me know if this works for you so I can mark [this solved] if it does.

:guitar:](*,)

---

