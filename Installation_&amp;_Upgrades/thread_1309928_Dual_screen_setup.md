---
title: "Dual screen setup"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by TBlake on 2009-11-01
I did a clean install of 9.10.  I'm running it on a Dell B130 with a second monitor (Envision LCD).  I am having troubles running it as a dual screen seutp.  I can run either monitor with 1024x768 resolution, just not at the same time.  When I do, I get a black screen with a single pixel wide orange bar down the left side of the primary monitor.  After waiting, the system reverts back deciding that it's not what I wanted.
Any ideas for a solution?  I was running 9.04 on this exact machine with not troubles.

---

### Post by Kokopelli on 2009-11-01
Try "xrandr"  from the commandline.  What I would like to know are:
- screen0 maximum resolution
- the names of the devices.  

I am guessing but your maximum resolution for your screen might currently be 1024x768, or at least below 2048x768.

---

### Post by TBlake on 2009-11-01
xrandr results
```
Screen 0: minimum 320 x 200, current 1856 x 768, maximum 4096 x 4096
VGA1 connected 832x624+1024+36 (normal left inverted right x axis y axis) 304mm x 228mm
   1024x768       60.0 +   75.1     70.1  
   832x624        74.6* 
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0 +
   1024x768       85.0     75.0*    70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV1 disconnected (normal left inverted right x axis y axis)
```

In "Display Preferences" screens labeled as Laptop 15" and EPI 15"
I'd like to have them each run at 1024x768.  
My laptop is more rectangular than my extra monitor.  While I was running 9.04, the laptop screen had black bars on the sides to bring it to equivalent proportions to the external.  I'd rather use the full extents of each screen if possible but what ever works so long as they both have decent resolution.

---

### Post by Kokopelli on 2009-11-01
not a permanent solution for you, but try this
EDIT: misread your results no need to reboot.
```

xrandr --output VGA1 --right-of LVDS1 --mode 1024x768

```

from the output of xrandr it looks like the external monitor is active at a resolution of 832x624, which is the weirdest resolution I have ever heard of. Your laptop monitor is active at 1024x768, which is not native for the panel, or at least not optimal.

You could try the following sequence

```

xrandr --output LVDS1 --left-of VGA1 --mode 1280x800
xrandr --output VGA1 --off
xrandr --output VGA1 --right-of LVDS1 --mode 1024x768

```

That activates your laptop panel at its native mode (1280x800), turns off the external monitor (maybe not needed), and then activates the external monitor at its native resolution (1024x768 ).

Theoretically this kind of thing can be done via the gui but I unfortunately am a command line junky so have no idea how to use the GUI.  Besides this is more useful and faster for me since I switch secondary monitors all the time.  I have an alias in my bashrc so all I have to type is "duall 1024x768" as an example.  If this works though someone else may be able to tell you how to do it via a gui.

---

### Post by TBlake on 2009-11-01
I tried the first line of code and resulted in both screens going crazy.  FWIW, the mouse pointer was still legible.

---

### Post by TBlake on 2009-11-04
I've not yet found a viable solution... might half to go back to Jaunty.  Any other suggestions?

---

### Post by Kokopelli on 2009-11-04
Sorry I do not have any ideas.  Can you post your xorg.conf?  Maybe that might shed some light on the problem.

---

### Post by TBlake on 2009-11-04
With much pleasure... how?  I'm still on the bunny slopes of the learning curve mountain.

---

