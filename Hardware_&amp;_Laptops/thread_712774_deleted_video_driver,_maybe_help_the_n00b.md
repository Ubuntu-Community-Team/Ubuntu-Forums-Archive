---
title: "deleted video driver, maybe: help the n00b"
date: 2008-03-02
forum: Hardware &amp; Laptops
---

### Post by cognoscento on 2008-03-02
...so this is the part where the hapless n00b (played by me) asks for help from some magnanimous guru (perhaps you?) because of something stupid he likely did.

So, the story goes a little something like this:

1) n00b decides to think about ditching Win. Vista (hiss hiss!) and so installs ubuntu on his nice and shiny new laptop (HP dv6358 or something like that... ).

2) n00b wrestles a little with display settings to get proper resolution working (installed 915resolution, switched to the appropriate intel driver (this laptop uses the intel 945 integrated video controller) and did some half-remembered other stuff, but got it working fine.

3) n00b installs a whole bunch of random other things, mostly interesting-looking software packages and life is good. OpenGL screensavers look gorgeous and Tremulous looks like fun.

4) N00b finds the Synaptic package manager, gets over-excited and deletes a bunch of stuff. Apparently the wrong stuff.

So, the n00b (Me!) is now left with a system that works, for the most part, but everytime Google Earth is run, the system logs itself out (literally!). Also, any desktop effects (compiz) look abysmal and choppy.

Diligently, I searched forums (especially this one), did google searches and other stuff, but don't really know what I'm looking for.

For troubleshooting purposes, I've pasted below what I hope is useful information. (Seems to be what gurus (you?) ask n00bs (me?) when this sort of stuff hits the fan. First, the results of running "compiz" in terminal:

-----
Checking for Xgl: present.
Checking for nVidia: not present.
Checking for Xgl: present.
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
-----

Just to point out, this laptop doesn't use nVidia hardware, so I'm not sure why that's coming up.

Next, the highlights from running glxinfo...

----
name of display: :1.0
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2

[...]

client glx vendor string: SGI
client glx version string: 1.4

[...]

OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)
-----

Lastly, my monitor (from System => Screens & Graphics) is listed as LCD Panel 1280x800 (widescreen) and the graphics card driver is listed as the i810

So, what do I (the n00b) need to do to troubleshoot  this? What steps should I be taking to make sense of this? (I couldn't find a decent document that made sense of how the display adapter, driver, xserver, opengl and all the other bits play together so I'm not sure where to even look.

Guru, help?

---

### Post by jocko on 2008-03-02
> **cognoscento said:**
> ...so this is the part where the hapless n00b (played by me) asks for help from some magnanimous guru (perhaps you?) because of something stupid he likely did.

So, the story goes a little something like this:

1) n00b decides to think about ditching Win. Vista (hiss hiss!) and so installs ubuntu on his nice and shiny new laptop (HP dv6358 or something like that... ).

2) n00b wrestles a little with display settings to get proper resolution working (installed 915resolution, switched to the appropriate intel driver (this laptop uses the intel 945 integrated video controller) and did some half-remembered other stuff, but got it working fine.

3) n00b installs a whole bunch of random other things, mostly interesting-looking software packages and life is good. OpenGL screensavers look gorgeous and Tremulous looks like fun.

4) N00b finds the Synaptic package manager, gets over-excited and deletes a bunch of stuff. Apparently the wrong stuff.

So, the n00b (Me!) is now left with a system that works, for the most part, but everytime Google Earth is run, the system logs itself out (literally!). Also, any desktop effects (compiz) look abysmal and choppy.

Diligently, I searched forums (especially this one), did google searches and other stuff, but don't really know what I'm looking for.

For troubleshooting purposes, I've pasted below what I hope is useful information. (Seems to be what gurus (you?) ask n00bs (me?) when this sort of stuff hits the fan. First, the results of running "compiz" in terminal:

-----
Checking for Xgl: present.
Checking for nVidia: not present.
Checking for Xgl: present.
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
-----

Just to point out, this laptop doesn't use nVidia hardware, so I'm not sure why that's coming up.

Next, the highlights from running glxinfo...

----
name of display: :1.0
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2

[...]

client glx vendor string: SGI
client glx version string: 1.4

[...]

OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)
-----

Lastly, my monitor (from System => Screens & Graphics) is listed as LCD Panel 1280x800 (widescreen) and the graphics card driver is listed as the i810

So, what do I (the n00b) need to do to troubleshoot  this? What steps should I be taking to make sense of this? (I couldn't find a decent document that made sense of how the display adapter, driver, xserver, opengl and all the other bits play together so I'm not sure where to even look.

Guru, help?

From what I can see your problem may be that you have installed xserver-xgl.
You shouldn't need to have that when you have an intel graphics card. Try to uninstall that, restart the xserver (ctrl+alt+backspace) and see if it works better.

---

### Post by Yellow Pasque on 2008-03-02
First, do as poster above suggested and remove xgl
If that doesn't fix everything, you may need to switch to the intel driver.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by cognoscento on 2008-03-03
> **jocko said:**
> From what I can see your problem may be that you have installed xserver-xgl.
You shouldn't need to have that when you have an intel graphics card. Try to uninstall that, restart the xserver (ctrl+alt+backspace) and see if it works better.

Done. Things are running smoother now but still some problems, including the fact that Google Earth flashes everytime you doubleclick anywhere on the screen. If you turn off all the compiz effects, the flicker is dimished, but still there.

Also, I've noticed that in all the 3d screensavers, there's a glitch where distance-order isn't respected. (farther objects seem to occlude nearer objects).

More ideas?

---

### Post by cognoscento on 2008-03-03
> **Temüjin said:**
> First, do as poster above suggested and remove xgl
If that doesn't fix everything, you may need to switch to the intel driver.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reinstalled the intel driver... things are better now, although if compiz is turned on, then I get that darned flicker whenever I double-click the googleearth screen, or otherwise interact with it. 

Also,still some problems with the 3d screensavers, regardless of whether compiz effects are on or off. (the center cylinder for each of the gears, for example, isn't properly occluded when it should be...

C.

---

