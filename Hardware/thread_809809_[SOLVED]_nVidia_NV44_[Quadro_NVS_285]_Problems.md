---
title: "[SOLVED] nVidia NV44 [Quadro NVS 285] Problems"
date: 2008-05-27
forum: Hardware
---

### Post by madscientist on 2008-05-27
I just got a new video card (lspci says nVidia NV44 [Quadro NVS 285]) and an extra monitor.  I have two Dell 19" LCD (1280x1024) monitors.  I'm connecting both monitors to my video card via VGA connectors.  My old video card was ATI, but I booted up and it offered to switch me to the nvidia proprietary drivers.  I accepted and it downloaded the nvidia-glx-new package 169.12+2.6.24.12-17.36.  I'm running an up-to-date Ubuntu 8.04 (Hardy) system.  Now when I start X I see the nvidia splash screen, which is good.

I'm having two problems:

First, I wanted to use nvidia-settings to configure the dual screen support but (contrary to many posts I've found elsewhere) there is no nvidia-settings program in the nvidia-glx-new package.  I've looked both on my system and in the .deb package itself and it's not there.

So I tried to install the separate nvidia-settings package, but when I try to run it I always get an error: "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

However, this is not true: I am absolutely running the nVidia driver.  Anyone have any ideas as to why it doesn't seem to recognize that?  I even tried the suggested fix of running nvidia-xconfig again and restarting but that didn't help.


Second: I edited the xorg.conf file by hand and added the TwinView setting and now I have both monitors running.  However, the window manager treats both monitors as one big screen, which I don't like.

I have another computer with an ATI card (also using the proprietary ATI driver) and dual monitors, and on that system the window manager knows that there are two monitors there.  So, my panels only span one monitor, and when I maximize a window it only takes up one monitor, and when popups appear they (mostly) appear in the middle of one monitor, not straddling both, and when I open a window it is always placed on the same monitor, etc.

How do I do that with my nVidia card?  Is that something I'd be able to configure with nvidia-settings if I could get it to work?

I tried to use System -> Preferences -> Screen Resolution, but I get an error saying "The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available."


Any help for these issues would be appreciated.

---

### Post by madscientist on 2008-06-05
Found a post elsewhere that recommended removing the xserver-xgl package.  So I did that, logged out and back in, and hey presto!  Everything works properly now.

Odd, but there you go.

Hope this helps someone else!

---

### Post by Youresorock on 2008-06-05
I have the same card, Dell NVS 285.  I had mine working after a good 4 hours of installing configuring reinstalling removing etc etc etc right at 8.04 release.  Now I just ran an update in the update manager and I can't get it working again.

I've been trying every solution on every forum on the internet and the best I can get is basic VESA support.

I'm running 8.04 x64 server kernel.  I've tried the restricted driver way, envy, driver off nvidia.com, basic nvidia driver-- nothing.

Very frustrated.  

Good Tip:  running sudo telinit 1, fix xserver, resume boot will get vesa working quickly.

I'm going to try a fresh install, full update then nvidia install on a spare harddrive.  I have 4GB ram, so I don't want to use the 32bit version, but I might try that if it's easier.

---

### Post by lekonna on 2009-09-15
Just installed 9.04 ubuntu with the same hw combo as per the original post described. 

I get one of my monitors doing a seizure inducing flashing effect and the other has defaulted to somewhere around 1280x1024 resolution. 

The display preferences just states that Monitor: Unknown

the Xorg.0.log shows no warnings or errors, seems to see both displays and detect the card ok. 

Couldn't find the nvida-settings anywhere anymore, what next ?

---

