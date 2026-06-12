---
title: "glx - refusal of service | seeking advice"
date: 2006-04-11
forum: Hardware &amp; Laptops
---

### Post by nalmeth on 2006-04-11
-- OK --
I got a used video card (for free) from a friend who upgraded his. I had installed ubuntu on his computer previously, and had 3D-acceleration working seamlessly.
the card is an NVIDIA NV18 GeForce4 MX 440 and is now located on my agp slot.
My previous card was a built-in (to motherboard) intel i915G 128 megabyte card. 
At first the new card wouldn't work at all, but being as stupid as I am, I finally realized (a week later) that I had my monitor still plugged into the motherboard rather than into the new video card.
Well after I changed that, ubuntu booted up, and gave me an xserver error.
SO I dpkg-reconfigured the xserver-xorg to use the nv driver, and everything was cool.
I then tried to install NVIDIA via automatix. This did not work, I got an xserver error on boot.
I then tried it by hand, but never got Direct Rendering in glxinfo. 
I followed a few different guides for doing this, including the "Howto Newest Nvidia Drivers" For both dapper and breezy. I have both on this PC.
Since I have recompiled my kernel with preemption (for ubuntu studio) I cannot complete the guide because I can't get headers and restricted modules for my kernel.
When I tried to install nvidia drivers in dapper, all I get is a black screen as soon as the xserver attempts to start, and get no output at all.
When I throw a liveCD in like the Kororaa live or LG3D or anything with 3D that I had *working* on this card in the previous computer, I get merely the black screen, precisely like in dapper. Again no output. Sitting idle at a 100% black screen. [-(
I am totally at a loss as to what is wrong.
The card obviously works with the nv driver.
The card is quite supported.
I thought it might  be due to my having an intel chipset, but didn't experience any of the same problems as other's did with the i845 chipset. This seemed to make sense at first, because I'm trying to see why the card works totally fine in one computer and is semi-functional in another.
I have looked into the 915resolution program, but this does not seem to cater to my problems.
I, don't, understand.
Can a graphics card work semi-functionally? Could I have somehow damaged the card rendering any 3D-acceleration useless, while the rest of the card is fine?
This is the kind of thinking I'm reduced to.
PLEASE share ANY ideas you may have. As I am at the end of my abilities and knowledge about this.
-- THANK YOU --

---

### Post by cabber on 2006-04-25
Naimeth,

I'd like to try and help you out.  First things first:  What motherboard are you using now?  Does it have intel onboard graphics?  Did you disable to onboard graphics of the motherboard?

My first thought is make sure you go into the BIOS and shut off any onboard graphics..which I assume you have done.  Are you open to start a new install?  I can send you the DVD if you need one.  Lets figure this out.  All should be working with your set up.  Something must have gone wrong during the install.

---

### Post by nalmeth on 2006-04-28
[quote=cabber]Naimeth,
 
I'd like to try and help you out. First things first: What motherboard are you using now? Does it have intel onboard graphics? Did you disable to onboard graphics of the motherboard?
 
My first thought is make sure you go into the BIOS and shut off any onboard graphics..which I assume you have done. Are you open to start a new install? I can send you the DVD if you need one. Lets figure this out. All should be working with your set up. Something must have gone wrong during the install.[/quote]
Hey thanks for taking a dive on this one cabber.
I had stopped monitoring this, and moving on to other issues, but I want to get back at it.
I do have an onboard intel graphics chip, its a 915G, 128 megabytes.
I did not in fact disable the onboard graphics on the motherboard. I tried going into the BIOS when I first got the card, because all I got was a black screen, but couldn't find any settings for video.
I then of course realized that I had to plug the monitor into the video card.
So by not disabling the onboard card, it might still be active? I hope this is the case, because it seems like it might make sense! :D 
The card always worked perfectly with 3D in linux, and I've just been dumb-founded by this.
I am totally open to a fresh install, it would be worth it (drooling over XGL).
I am dual-booting dapper and breezy right now, and neither get's 3D.
I'm at work right now, not in front of the PC, but will be hope around 10 pm my time (it's 3:22 right now).
I hope you're right an have missed a BIOS setting. 
I should point out, if its not seen, that the card works fine with everything else. X sets up and works great, even fancy screensavers run pretty well (barring 3D of course).
Do you have any experience with this intel card? I can get you the motherboard specs if it will help anything.
Also any other info that might help I will gather.
Thanks again for the initiative

---

### Post by nalmeth on 2006-04-30
Have gone into BIOS settings, found one object that may be relevant
It had something to do with default monitor display, which was set to PCI.
I switched it to GEAR (my agp slot), and tried to install Nvidia GLX, but to no avail.
```

nalmeth@edubuntu:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault
```
There is a lot in the BIOS I don't understand. Do you know what I might try next?

---

### Post by [S|G] on 2006-05-01
Hello,

I also have a NVidia Geforce4 AGP and had some headaches with it. There are two ways to get it working (at least for me these two worked):

1: I highly recommend this one. Go to nvidia website and download the latest drivers ([www.nvidia.com](www.nvidia.com)) for linux. Drop them somewhere you can easily access from the shell, such as your user home directory. Then reboot your computer and login to shell as your user. do this:
```

chmod +x NVIDIA-Linux-x86-1.0-8756-pkg1.run
sudo ./NVIDIA-Linux-x86-1.0-8756-pkg1.run

```

Just change the file name to the one you've just downloaded. There'll be a couple of questions the installer will ask you; just make sure you compile a module for your kernel and say YES when it asks to write your default xorg.conf. Note: "yes" isn't the default, so don't just press enter on every screen! After installation finishes, try:
```

sudo /etc/init.d/kdm restart

```
You should get the graphical login at this point if everything went ok. 

**POSSIBLE PROBLEM**: your compiler may not be the same version as the one that compiled your current kernel. There are some posts in the forum that explain in detail how to fix that, though :)


Method 2: Install nvidia-glx, nvidia-kernel-common and nvidia-kernel-source from ubuntu repos:
```

sudo apt-get install nvidia-glx nvidia-kernel-common nvidia-kernel-source

```

NEVER use the two solutions together, as one will overwrite the other. It probably won't screw your install, but will leave broken files lying around.

---

### Post by nalmeth on 2006-05-08
Thanks for reply

I've tried both method's (tried the second one just recently) and still get no glx rendering.

On dapper here is my Intel Integrated video card config, spliced from xorg.conf:
```
Section "Device"
        Identifier      "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
=======================================================
Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
=======================================================
nalmeth@ubuntu:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
```
and the same for the AGP NVIDIA card:
```
Section "Device"
        Identifier      "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection
============================================================
Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
============================================================
nalmeth@ubuntu:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
============================================================

```

Anyone see anything out of place?

---

