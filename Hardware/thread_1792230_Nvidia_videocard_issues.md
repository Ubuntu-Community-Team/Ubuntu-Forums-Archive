---
title: "Nvidia videocard issues"
date: 2011-06-27
forum: Hardware
---

### Post by freeallforever on 2011-06-27
Half the stuff I find is several years old and obsolete so here is my problem.

anonymous@anonymous:~$ glxinfo | grep rendering
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

I have the nvidia proprietary driver that says it is activated but not in use.

 I have tried reinstalling it and restarting and some synaptic addons and i DO NOT want to reinstall/repair my entire Linux again. What are my options? 

I have customized this gaming PC and I believe wine can make the games I like work if only my video card was working properly.

Let me know any additional details you may need, I am a Linux newbie but am comfortable going all over the terminal or doing anything intense.

---

### Post by papibe on 2011-06-27
Could you post your conf file?
```
/etc/X11/xorg.conf
```
Regards.

---

### Post by freeallforever on 2011-06-28
> **papibe said:**
> Could you post your conf file?
```
/etc/X11/xorg.conf
```Regards.
/etc/x11/xorg.conf: No such file or directory

---

### Post by papibe on 2011-06-28
Then the nvidia driver is not being used. Run this:
```
$ gksudo nvidia-settings
```
then when you find your settings acceptable, go to X Server Display Configuration and select Save to X Configuration File.

Hope it helps.

---

### Post by freeallforever on 2011-06-28
> **papibe said:**
> Then the nvidia driver is not being used. Run this:
```
$ gksudo nvidia-settings
```then when you find your settings acceptable, go to X Server Display Configuration and select Save to X Configuration File.

Hope it helps.
*"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."*

So I type:
```
sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```Then I saved but nothing changes and when i run the gksudo command you give me its still not using.

---

### Post by papibe on 2011-06-28
Restart your machine.

---

### Post by freeallforever on 2011-06-28
> **papibe said:**
> Restart your machine.
I did this and then it would not load up, it would try loading things and then it would stop, i restarted second time and it kept doing that and just paused at checking battery state.

I am now running LIVECD, how can I fix this current issue so we can get back to resolving my graphics card, thank you. :D

---

### Post by freeallforever on 2011-06-28
Offline... I will have to do some form of reinstall/repair and we can try this again later. :lolflag:
I know went with the 3D experimental support, testing now.

Checking that thread MG...

---

### Post by MG&amp;TL on 2011-06-28
Just had this exact same problem. Tried to install Unity 2d, on 10.10, went fine, but would not boot normally. Asked for login and password via the black screen (you know, the terminal/MS-DOS type thing you often get when it boots, only this time I was stuck. :confused:

I ran grub and ran in 'failsafeX' low graphics mode. :( This worked (evidently) but my screen's shifted a couple of centimetres to the left. The Nvidia Xserver thing gives me exactly the same thing as you, but I do have a xorg.conf file.

I don't know, maybe it's because I have separate graphics card issues. :)
See here:
[http://ubuntuforums.org/showthread.php?t=1789382](http://ubuntuforums.org/showthread.php?t=1789382)

---

### Post by freeallforever on 2011-06-28
Okay seems the experimental driver was the way to go, this issue is solved. Thank you! :p

---

