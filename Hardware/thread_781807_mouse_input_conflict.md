---
title: "mouse input conflict"
date: 2008-05-04
forum: Hardware
---

### Post by izach on 2008-05-04
First off, I'm on Hardy.  I was installing a bunch of package a while back, and all of a sudden my mouse input conflicts my keyboard.

Let me explain: Whenever I have a button pressed on the keyboard, the USB mouse won't move the pointer.  The touchpad still works fine.

So the keyboard and USB mouse are  probably writing to the same buffer somewhere.

I already reconfigured xorg, it didn't help.

It's not a gnome or kde issue, it happens in both, same thing with kdm and gdm and window decorators.  Compiz is off.

I'm looking for one of 3 solutions:
1) tell me how to get a list of package installation history so I can hunt down the problem and remove it.
2) tell me what package is the problem so I can remove it.
3) give me a conf file to edit.

If you need any more info, let me know.  Thanks in advance.

---

### Post by izach on 2008-05-04
[http://ubuntuforums.org/showthread.php?t=781200](http://ubuntuforums.org/showthread.php?t=781200)

For anyone interested, this:

```
sudo dpkg -l | grep 'mouse'
```

got me a list of potential problem packages:

ii  crystalcursors                             1.1.1-9                     X11 mouse theme with the crystal look&feel
ii  kmousetool                                 4:3.5.9-0ubuntu1                     KDE mouse manipulation tool for the disabled
ii  kodo                                       4:3.5.9-0ubuntu1                     mouse odometer for KDE
ii  mouseemu                                   0.15-8ubuntu3                     Emulate mouse buttons and mouse wheel
ii  mousetweaks                                2.22.1-0ubuntu2                     mouse accessibility enhancements for the GNOME desktop
ii  xserver-xorg-input-mouse                   1:1.2.3-2                     X.Org X server -- mouse input driver
ii  xserver-xorg-input-vmmouse                 1:12.4.3-1ubuntu1                     X.Org X server -- VMMouse input driver to use with VMWare

Not sure which one was the culprit, but I did a:

```
 sudo apt-get remove crystalcursors kmousetool mouseemu mousetweaks
```

My money is on kmousetool, since I'm not disabled.

---

