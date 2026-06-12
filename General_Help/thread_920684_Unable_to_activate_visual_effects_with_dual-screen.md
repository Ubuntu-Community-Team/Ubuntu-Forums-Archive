---
title: "Unable to activate visual effects with dual-screen"
date: 2008-09-15
forum: General Help
---

### Post by Sillywombat on 2008-09-15
Got a little annoyance here, nothing major, but would be nice to know if I can do this or not.

I am currently using a nvidia GeForce 6600, with two screens in Xinerama.Got the right drivers (NVIDIA Driver Version: 169.12). Everything works like a charm. However, i can't seem to activate the visual effects. I know this is possible because i managed to get them in Ubuntu 7.04 when i only had one screen. 
When i try to turn on either Normal or Extra effects, i get "The Composite extension is not available".

So, am I not allowed to use them when i am in dual-screen? or is it something else? And if I am, could my little 6600 GPU handle it?

Any help would be greatly appreciated!

---

### Post by Sillywombat on 2008-09-15
Update:
i have since ran a check to see if its possible to run compiz on my pc:
```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV43 [GeForce 6600] (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [FAIL]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:00f2 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 

```

Hmm, thats annoying... Any ideas anyone?

---

### Post by Sillywombat on 2008-09-16
Please... Anyone?
How can i get the Composite extension?

---

### Post by roadrun777 on 2008-09-16
well first, it's "bald-headed men" lol, in your quote you have bold-headed.

Next, I think the issue is not an easy one to answer. I have no experience with your video card myself, but the simple fact that I just about went mad hunting through source code to figure out why my cheap radeon vid card wouldn't do composite when I had 2 monitors hooked up to it.

The answer that I eventually found was that the current radeon drivers had serious problems with dual-head set ups and the current xserver at the time (last years version) did not support acceleration or composite on 2 screens. It only supported it on one. I got real tricky and tried to outwit the drivers by running two completely seperate xservers for each video head. After 2 months 3 pounds of coffee and a new beard I finally gave up. Dual-head setups with any kind of video acceleration where just not implemented in the drivers at the time. Running dual xservers worked for the most part, it's just I had issues with keyboard and screen controlling and at the time there was no way to transfer a running applications window to another xserver. So it made it a real PITA to switch desktops, which completely ruined the whole reason I wanted a dual-head setup to being with. I imagine that is possible now, but whether it is implemented and working I can't say.

Go ahead and test this out. See if you can disabled the second screen. Reboot, or reload X, now see if it loads the composite. If it does than the bug is still present in the Xserver your using. So do yourself a favor and either grab a nightly live-cd and try it from that, or read up on how to compile X from source. Multiple monitor support WITH acceleration seems to be one of those things that is constantly being worked on but no real progress ever occurs.

---

### Post by Sillywombat on 2008-09-17
Haha, thanks for that. Never noticed.

SO far, i spent the night trying to fix up the problem; and i sort of got it working. turns out all i needed to do was move a couple of lines here and there and install xgl xserver.
However, once that it done, all the wobbly windows in the world couldnt replace the annoyance that messing up my X screen configuration has. Windows spanned across two screen, keyboard language kept changing, sometimes worked great, other times, was buggy. So i guess i can finially say it is possible, however, i have now reverted back to how it was before (almost, but getting there).
I had to try though, but the fact that i couldnt play eve with the xgl installed ended up making the final decision.
Thanks for the help!

---

### Post by nenopera on 2010-02-12
I'm one of those ati 9600 dual monitor users. Maybe this tips could help people trying to squeeze their systems as much as I do.

So, I have a 1,7Ghz, 2Gb DDR Ram and an ati mobility radeon 9600 with Ubuntu 9.10. I work with two monitors 1280x800, 1024x768 -using virtual resolution- with compiz enabled -cube rotation, shift window exchanger, group windows, etc- and a tablet mouse.

Nothing remarkable to setup this:

extract of xorg:
<<
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 2304 800
         EndSubSection
EndSection
>>

The only trick you need is (due to something related with virtual resolution):
you are here --> Logged in, using two monitors without extra visual effects.
you want to get --> Two monitors with compiz
Steps:
1 switch off second monitor
2 enable extra visual effects
3 switch on second monitor (you will see a few part of the second background screen garbled, but any window on it will show perfectly)
4 enable compiz

Seems that the virtual resolution (without the garbled part of second screen is 1280+768x800=2048x800. I hear something about fixed sizes in order to effects work with old graphics card... maybe, I don't know, in fact I use 2304x800 perfectly (but it's interesting that the cube effect has an empty hole in that garbled part. 

Some more trickys:

I need to switch on/off compiz because I work with the IntelliJ IDE and for any reason the scrollbar jams with compiz, so I need to switch it off -making scroll works smoothly again- 

As a switch for compiz, I have installed [compiz-switch]("http://forlong.blogage.de/entries/pages/Compiz-Switch"), which work reasonably well, 
but keeping in mind the trick to enable extra visual effects, compiz can't be enabled directly after switch compiz off, then around the command in his respective icon

$ compiz-switch -c -sa

I need to switch off the second monitor before, and switch on after. Ok, modify the command on icon of compiz switch and point it to a script, something like 

#!/bin/bash
xrandr --output VGA-0 --off
compiz-switch -c -sa
sleep 1 # compiz-switch doesn't seem to wait till its ends
xrandr --output VGA-0 --auto --right-of LVDS

read [this]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2") (recommended)

Furthermore you could want to add a shorcut key to your switch, read [this]("http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/") (consider the often forgotten <super> key for this)

If you switch off the second monitor, all the windows in it will go to the remain monitor, but after reload , their position and state (maximized, minimized) comes back, perfect!.

is preferable to make a export of your compiz settings before.

Only a question:

Why all this stuff (configured one, use whenever) if I actually/finally get two monitors with extra visual effects?

Maybe there is any command or log that shows info about troubles to start extra visual effects with my configuration (remember 2304x800), that info would by appreciated

Hope this two monitors step-by-step trick help you improve your productivity and/or skills using linux, but well that's another [story]("http://www.codinghorror.com/blog/archives/000012.html").

Hey, I left you in a tar these things: :D (i cannot resist to put an smiley)
compiz-switch.py (python graphical switch)
compiz-cubo.profile (my settings on compiz, effects, shorcut and all stuff)
.compiz-switch.sh (the script for de icon)

Bye

---

