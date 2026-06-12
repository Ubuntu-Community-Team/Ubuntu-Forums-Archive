---
title: "Lenovo IdeaPad Y570 with Nvidia GT 555m - no Compiz, games are screwy"
date: 2011-12-27
forum: Hardware
---

### Post by missingno on 2011-12-27
I just got this new laptop, only to find that I can't get graphics acceleration working. Installing the official proprietary driver then running nvidia-xconfig prevented X from starting up at all, forcing me to uninstall the driver and delete Xorg.conf

I'm not sure what fallback driver it's using, but what I do know is that Compiz won't work, Minecraft is full of graphical glitches, and Super Meat Boy crashes. Haven't tested anything else yet, but it doesn't look good so far. One way or another, those are what I want to get working.

I've attempted to find a solution through Google, but all I can figure out is that this laptop model has the card set up a little funny so the driver isn't recognizing it, and the Optimus graphics switching isn't supported under Linux. Does that mean I can't use the Nvidia card at all, or is there a way to enable it without the graphics switching? Or could I get the other integrated Intel card to run Compiz and whatnot, framerate be damned?

---

### Post by missingno on 2011-12-27
Trying to see if I can just get everything to work on the alternate card. It's an Intel HD Graphics 3000, and I can't find any specific drivers for it listed anywhere. Has anyone had any luck getting Compiz to work with that?

---

### Post by missingno on 2011-12-27
[Got the Intel card working from this PPA.](https://launchpad.net/~oibaf/+archive/graphics-drivers/) I guess it'll have to do.

I'm having two minor issues though with Compiz. When I switch workspaces, the windows from the previous workspace flicker for a moment after the cube animation. Additionally, using ctrl-alt-left/right to move a window from one workspace to another shows the animation of it moving, but then it vanishes back to the previous workspace. Anyone know what the deal is with those?

edit: And by "Got the Intel card working", I mean "Minecraft still has graphical weirdness". Sigh. At least Super Meat Boy and Compiz work...

---

### Post by missingno on 2011-12-27
Sorta fixed the Compiz woes by switching from Desktop Cube to Desktop Wall. Gonna miss that cube, but this is better than the flickering and busted keyboard shortcuts. Still having issues with some other games I'm trying, OpenGL still just isn't happy with this setup. I've attached my glxinfo if it helps at all.

---

### Post by missingno on 2011-12-28
Tried to get Ironhide to work as a last resort, no dice. The config utility couldn't autodetect my laptop's display and so I wasn't sure what manual name to type - I went with TFT-0, and the error log suggests that was the wrong answer. Tried CRT-0 and DFP-0, also no go. Anyone know how I can find the right one?

---

### Post by Lekensteyn on 2012-01-22
Both the Lenovo Y470 and Y570 are not supported by the nvidia driver yet: [https://lists.launchpad.net/bumblebee/msg00070.html](https://lists.launchpad.net/bumblebee/msg00070.html)

For being able to use your Intel graphics, uninstall the nvidia drivers and remove the xorg.conf file, possibly generated with nvidia-xconfig as well:
```
sudo apt-get purge nvidia-current
sudo rm /etc/X11/xorg.conf
```

Reboot and greet 3D again.

---

