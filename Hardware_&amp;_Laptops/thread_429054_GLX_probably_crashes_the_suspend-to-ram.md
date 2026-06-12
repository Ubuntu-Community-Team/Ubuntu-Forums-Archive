---
title: "GLX probably crashes the suspend-to-ram"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by Laervian on 2007-04-30
I have done some experimenting with my Ubuntu Feisty + nvidia drivers in order to make suspend-to-ram and -disk work, and I have discovered that the GLX option is the one which actually crashes the suspend. I have tested this on my Dell Inspiron 6400, with NVIDIA 7300 card, TL5600 core duo processor. My xorg.conf file at the graphics card section reads so, using the latest nvidia driver (have not tested it with the nvidia-glx):

Section "Device"
    Identifier     "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
    Driver         "nvidia"
    Option         "NoLogo" "True"
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "False"
    Option	   "AllowGLXWithComposite" "False"
EndSection  

The suspend works fine but beryl/compiz do not function well: beryl for example gives the following error: Xlib:  extension "GLX" missing on display ":0.0".
If I change the two last options to "True" and reboot, beryl/compiz will work, but when resuming from suspend-to-ram/disk the screen will be black with the cursor floating, no option of calling the terminal screen (ctrl+alt+f1), forcing a reboot. I think therefore that it is not the NVIDIA driver itself, but rather the GLX option which causes the crash.
I also have to report that I think I met this same bug once before, on my old laptop, an IBM Thinkpad R50e with a i810 graphics card. While I was trying to fix suspend on that machine I accidentally ruined my driver, in that I was no more able to launch xgl/aiglx applications such as beryl or compiz, and as a consequence suspend began to work. I do not remember how I did it and in fact I was no more able to repeat the accident, but these two experiences combined make me suspect that it is the xgl/aiglx projects which are causing the suspend bugs.

The bug has been already submitted to the launchpad.

---

### Post by meldroc on 2007-05-10
I'm noticing the same thing - I'm running Feisty with the latest nvidia proprietary drivers (1.0-9755), with the nvidia-glx-new package providing the GLX libraries.

So far, the behavior's pretty consistent.  If I run a non-3D desktop - straight KDE with no-frills kwin, I can suspend and resume with no problems.  If I run beryl, then try a suspend2ram, the video freaks out when I try to resume, crashes the machine, usually with either a black screen or a screen full of garbage, forcing me to reboot.

I'm currently running on an Asus A8Js, with an Nvidia Go7700 GPU and 512MB video RAM.

One person suggested that I go into Beryl's settings and disable vertical blank refresh, which eliminates (or at least somewhat alleviates) a related bug that causes the display to freak out and crash when I switch to a virtual console.  It still crashed hard when I did a suspend2ram.

Any ideas on how to fix this?  I suppose I'll have to go on nvnews.net and wail on the Nvidia developers until they fix their drivers...

---

### Post by Laervian on 2007-05-10
Uhm sorry I can't help you. I forgot to update the post, but I actually solved my problems disabling the Sync to Vblank (I do not even know what that means, and I do not particularly care, if I have to be earnest :D ). Beryl is still quite buggy, but that is an entirely different problem. Guess I will wait 'till kwin 4 beta come out... :)

---

