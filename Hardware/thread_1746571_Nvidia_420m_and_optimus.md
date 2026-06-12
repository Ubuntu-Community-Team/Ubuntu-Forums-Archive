---
title: "Nvidia 420m and optimus"
date: 2011-05-01
forum: Hardware
---

### Post by iammeagain on 2011-05-01
I have disabled my nvidia card and am only using the intel for my video feed. The intel is from an i5 460m. The problem I am having is that opengl is not working for me. I disabled it through [this method.]("http://ubuntuforums.org/showpost.php?p=10754116&postcount=25") I'm hoping someone may be able to shed some light on my situation. I can't figure much more out.

When I try to run glxgears, I get the error:
```
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

``` 

glxinfo gives
```
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

It appears it may be from disabling the nvidia and not completely unistalling it. See [here]("http://www.linuxquestions.org/questions/linux-hardware-18/xlib-extension-glx-missing-on-display-0-0-a-200313/")

Here is the information I have dug up and tried to attempt. Although I haven't been able to get anything from these yet.
Info 1:
I can't install Nvidia drivers so I thought I may give intel drivers a shot. This is what I have dug up so far. Unsure how to install them though. [http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)
[http://intellinuxgraphics.org/2011Q1.html](http://intellinuxgraphics.org/2011Q1.html)
Info 2:
I tried to force load glx by adding glx "load" to the xorg.conf
That just caused my screen to black out at boot.
Info 3:
I want to try install installing the X.org edgers PPA like what was done here, but I am unsure how.
[Here]("http://ubuntuforums.org/showthread.php?t=1657319")
I found this which is related to X.org edgers, but it said it was for ATI, not nvidia or intel. So I didn't want to try [These.]("https://launchpad.net/ubuntu/+source/fglrx-installer/2:8.840-0ubuntu4/+buildjob/2494075")
Info 4:
I attempted to reinstall both xserver-xorg and xserver-xorg-video-intel. With no luck. 
I attempted the 'sudo dpkg-reconfigure xserver-xorg' but I don't have any options pop up to reconfigure anything.

---

### Post by iammeagain on 2011-05-02
I got this solved through this method:
```
sudo apt-get purge nvidia*
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

```

Which came from here:
[http://ubuntuforums.org/showthread.php?t=1301433&highlight=GLX+missing+display](http://ubuntuforums.org/showthread.php?t=1301433&highlight=GLX+missing+display)

---

### Post by xinwu on 2011-06-21
Thank you! It helps!

---

### Post by beew on 2011-06-21
> **iammeagain said:**
> I got this solved through this method:
```
sudo apt-get purge nvidia*
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

```Which came from here:
[http://ubuntuforums.org/showthread.php?t=1301433&highlight=GLX+missing+display](http://ubuntuforums.org/showthread.php?t=1301433&highlight=GLX+missing+display)

How is it solving the problem by turning the performance Nvidia card into an expensive  paperweight? You may as well have bought a  cheap machine with just a Intel card if all you care about is battery life.

Here you may find a better option

[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)

---

