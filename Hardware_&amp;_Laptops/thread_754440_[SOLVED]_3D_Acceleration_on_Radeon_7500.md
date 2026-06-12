---
title: "[SOLVED] 3D Acceleration on Radeon 7500"
date: 2008-04-13
forum: Hardware &amp; Laptops
---

### Post by guitarMan666 on 2008-04-13
I just installed a Radeon 7500 video card with tuner into my machine (specifications to follow).  I have tried every relevent remedy there is to restore 3D acceleration.

Replacing the driver value in xorg.conf to fglrx throws out an error (fglrx cannot be found, doesn't exist), using the radeon value doesn't change anything, deleting xorg.conf to force re-detection doesn't change anything.

The computer is a eMachines t4165 (desktop)
Pentium 4 1.6 GHz
256MB RAM
60GB HD, split to run Windows and Ubuntu

Running glxinfo | grep rendering yields:
$ glxinfo | grep rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

Running glxinfo | grep Mesa yields the same.

Running glxgears yields:
$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

Is there anything I can do?

You all have been extremely helpful and, as always i thank you in advance for your time.

---

### Post by overdrank on 2008-04-13
> **guitarMan666 said:**
> I just installed a Radeon 7500 video card with tuner into my machine (specifications to follow).  I have tried every relevent remedy there is to restore 3D acceleration.

Replacing the driver value in xorg.conf to fglrx throws out an error (fglrx cannot be found, doesn't exist), using the radeon value doesn't change anything, deleting xorg.conf to force re-detection doesn't change anything.

The computer is a eMachines t4165 (desktop)
Pentium 4 1.6 GHz
256MB RAM
60GB HD, split to run Windows and Ubuntu

Running glxinfo | grep rendering yields:
$ glxinfo | grep rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

Running glxinfo | grep Mesa yields the same.

Running glxgears yields:
$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

Is there anything I can do?

You all have been extremely helpful and, as always i thank you in advance for your time.

Hi and have you tried to reconfigure you xorg with the command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then you may try and use the driver under device in your xorg "ati"

---

### Post by guitarMan666 on 2008-04-13
Actually i did, i neglected to include that initially, it didn't do anything either.

---

### Post by jocko on 2008-04-14
> **guitarMan666 said:**
> Actually i did, i neglected to include that initially, it didn't do anything either.

The fglrx driver does not support such an old card (anything older than radeon 9500 was abandoned by ati almost two years ago).
You should be able to get the open source "radeon" driver working (by setting the driver to either "radeon" or "ati" in xorg.conf).
I doubt you will ever be able to use the tuner of that card.
Make sure you start with a fresh xorg.conf by using:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by guitarMan666 on 2008-04-14
I don't really care about the tuner so that is not an issue.  I will try this as soon as I get back home.  Should I do this from a terminal window or should I use the actual command prompt (ctrl+alt+F1) or does it make no difference?

---

### Post by jocko on 2008-04-14
> **guitarMan666 said:**
> I don't really care about the tuner so that is not an issue.  I will try this as soon as I get back home.  Should I do this from a terminal window or should I use the actual command prompt (ctrl+alt+F1) or does it make no difference?

It makes no difference if you do it from a terminal emulator or a "real" terminal.
Good luck!

---

### Post by guitarMan666 on 2008-04-14
It's giving me an error with what was given to me:

$ sudo dpkg-configure xserver-xorg
[sudo] password for eric:
sudo: dpkg-configure: command not found

These are other variations I attempted:

$ sudo dpkg -configure xserver-xorg
dpkg: unknown option -o

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

and

$ sudo dpkg --configure xserver-xorg
dpkg: error processing xserver-xorg (--configure):
 package xserver-xorg is already installed and configured
Errors were encountered while processing:
 xserver-xorg

Did you mean perhaps dpkg-reconfigure xserver-xorg?

---

### Post by jocko on 2008-04-15
Sorry, that should be dpkg-**re**configure..

---

### Post by guitarMan666 on 2008-04-16
Ok, still no joy.  Running glxgears is giving me the same errors as before.  No idea why!  I set the driver to ati (radeon was not an option in the config utility) I will try the Graphics and Screens utility again to see if there is any change.

Edit:  The full model name (off the box) of the video card is ATI All-in-Wonder Radeon 7500 if that makes any difference.  It also has 64MB VRAM.

---

### Post by guitarMan666 on 2008-04-16
According to the document at [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) my card has (supposedly) full 3D acceleration support.  It also says that it works with something called AIGLX and that I don't need to install XGL (which I tried a little while ago to major failure).

Following the directions provided, I re installed libgl1-mesa-glx and lbgl1-mesa-dri and confirmed that my xorg.conf was properly configured.

The instructions say to remove the fglrx package (which apparently wasn't installed anyway) to avoid conflicts.  I have done all of this and i STILL have no 3D, at all.  Not even slow software-rendering 3D.  I'm still getting the errors that I described in my above posts.  Is there anything else I can try?

---

### Post by guitarMan666 on 2008-04-17
Ok, I got fed up with all of this and so I re-installed Ubuntu.  The whole freaking thing.  I now have 3D acceleration and Compiz...but my resolution SUCKS.  To the best of any of your knowledge, is 1024 x 768 @ 60Hz supported by the driver?

---

### Post by jocko on 2008-04-17
> **guitarMan666 said:**
> To the best of any of your knowledge, is 1024 x 768 @ 60Hz supported by the driver?

I would be very surprised if it was not supported. My guess is that you need to set the correct vertical refresh and horizontal sync rates for your monitor, otherwise Xorg won't know what your monitor can handle.

Try to find the specifications of your monitor (do you have a manual? otherwise you'll probably find it online, try the manufacturer's home page).
If you can find it, run 'sudo dpkg-reconfigure xserver-xorg' again, and when you come to the section about the monitor, make sure to select the "Advanced" configuration to be able to give your own refresh and sync rate ranges.
While you reconfigure xorg, you should also be able to select which resolutions should be available.

---

### Post by guitarMan666 on 2008-04-17
> **jocko said:**
> I would be very surprised if it was not supported. My guess is that you need to set the correct vertical refresh and horizontal sync rates for your monitor, otherwise Xorg won't know what your monitor can handle.

Try to find the specifications of your monitor (do you have a manual? otherwise you'll probably find it online, try the manufacturer's home page).
If you can find it, run 'sudo dpkg-reconfigure xserver-xorg' again, and when you come to the section about the monitor, make sure to select the "Advanced" configuration to be able to give your own refresh and sync rate ranges.
While you reconfigure xorg, you should also be able to select which resolutions should be available.
I actually did do a reconfigure on it and everything works great, 3D, wobbly windows, the works.  I'm almost done re-setting-up my Ubuntu install (it ended up being a little bloated so it was time to start fresh anyway).  The only software that I had on my computer that isn't there right now are Wine and the kubuntu-desktop package (the latter of which i don't plan to install).  Do you think they were the cause of the issues I was experiencing?

---

### Post by jocko on 2008-04-17
> **guitarMan666 said:**
> The only software that I had on my computer that isn't there right now are Wine and the kubuntu-desktop package (the latter of which i don't plan to install).  Do you think they were the cause of the issues I was experiencing?
I have no idea what could have caused your problems, but I'm pretty sure neither wine nor kubuntu-desktop would interfere with the graphics driver.

---

### Post by guitarMan666 on 2008-04-17
Ok well then that's it thanks for all your help!

---

