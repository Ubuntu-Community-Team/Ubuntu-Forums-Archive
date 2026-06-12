---
title: "Problems with ATI Drivers, they don't seem 3d accelerated, compiz or XGL doesn't work"
date: 2008-09-21
forum: General Help
---

### Post by Predator106 on 2008-09-21
Hello, I'm running Ubuntu Hardy.

This computer was trying to use a 9200 SE ATI card, but then I found out it isn't really supported. So I tried the much newer X1600PRO ATI card. I installed the proprietary drivers, but when I enable compiz, the screen will blank out, going completely gray.

I have tried to install XGL so I can use compiz, it seemed like it was fine until I realized how EXTREMELY laggy it was. Typing in this textbox makes it get somewhat laggy. It's almost like the graphics card is doing absolutely nothing, and the CPU is doing all of the work.

I looked at this guide: [http://ubuntuforums.org/showthread.php?t=168618](http://ubuntuforums.org/showthread.php?t=168618)

But where it says to type in: fglrxinfo
Mine returns the following:

```
server@server-P4:~$ fglrxinfo
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)
```

It says to make sure it shows the ATI driver, NOT mesa.

What do I do, I really want compiz to work, and I want 3D acceleration, this is annoying, ATI drivers seem to suck so bad compared to Nvidia's. Nvidia's it was just drop it in and it works with the restricted drivers fine, no problems with compiz. Not the case with all the ATI cards I've tried. And apparently anything below a 9500 isn't supported... I didn't notice that until after I had tested a bunch of cards that were such.

Please make this speedy as I can't do anything on my server (this computer) until I have 3D acceleration.

I use this over VNC, so it actually is doubling the lag, I thought it was VNC that was being laggy, but it was actually the computer itself... It's HORRIBLE. It takes 5 Sec to change send a window to back.

It just gets sooo laggy, even scrolling down in this textbox or web page.

---

### Post by Predator106 on 2008-09-21
Also, for some reason, every time I reboot now with this card, X server automatically goes into that bulletproofX mode, where it asks you to choose a driver, or else not have any high res. or 3D abilities.

---

### Post by Brain-free on 2008-09-21
OK, I looked into it and from what I read in the [Unofficial Wiki for the ATI Linux Driver]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide") the problem lies in your xgl installation.

Do 
```
sudo apt-get remove xserver-xgl
``` 
and then to check if this has worked
```
DISPLAY=:0 glxinfo | grep render
```

It should say direct rendering "yes" and ATI X1600PRO.

If after that compiz doesn't work folow the instructions in the article above, in the section "Removing Mesa Drivers"

---

