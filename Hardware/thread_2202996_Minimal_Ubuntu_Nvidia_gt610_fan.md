---
title: "Minimal Ubuntu Nvidia gt610 fan"
date: 2014-02-01
forum: Hardware
---

### Post by EKRboi on 2014-02-01
I have built my HTPC from the ground up starting with ubuntu minimal. It boots straight to XBMC (as the window server) for my media and also the ability to launch any retro game emu under the sun. My config is Asus F1A55-M with and AMD Athlon II X4 651K, 4GB g. skill ram, and an Nvidia gt610. I have been running this setup for quite some time (1+ years?) with no trouble other than the fan runs @ 100% ALL THE TIME! I have looked into this before quickly googling things with minimal results. My "big rig" is a "monster" AMD FX-8350 build with 3x Nvidia 580's running windows 8.1, xubuntu 13.10 and OSX Mavericks... on the "big rig" in linux I can manually control the fan speed from nvidia settings after setting --cool-bits no problem. So I KNOW Nvidia fan speed control is possible with linux/ubuntu. Also with the "big rig" ubuntu/the nvidia drivers handle the fan speed without issue, idling very low and spinning up as needed. So the question is how do I get this working in a minimal situation like on my HTPC where XBMC is acting as the "window server"? I can use a command such as "nvidia-settings -a "[gpu:0]/GPUFanControlState=1" -a "[fan:0]/GPUCurrentFanSpeed=75"" on the "big rig" to spin up the fan on my first gpu and the second an so forth. When I try to use a similar command on my HTPC I get "ERROR: The control display is undefined; please run `nvidia-settings --help` for usage information." I am running this via SSH as I have no real way to run terminal commands from xbmc. I feel like there is a simple "service" I am missing or have over looked something simple so input from the guru's would be GREATLY appreciated. I have no need to really control the fan speed manually on the HTPC.. it would be nice it was "natively controlled" though as the gt610 at "full blast" is not only loud as hell but I can only assume its not great for the fan to run at 100% all the time either. 

If you would like me to post any other info please let me know!

---

### Post by mikewhatever on 2014-02-01
First, a small correction, I could be wrong, but xorg-server is usually the server, and XBMC is probably a window manager, similar to Compiz, Metacity, OpenBox, etc.
With that out of the way, have you installed the Nvidia graphics driver on the XBMC box? You have to do it, as the free nouveau driver doesn't have powermanagment yet.

---

### Post by EKRboi on 2014-02-01
Yep, latest official nvidia drivers.

---

### Post by jcdole on 2014-08-17
I have a similar problem. 
What I have discovered ( but not solved ) is that the command :
> nvidia-settings -a "[gpu:0]/GPUFanControlState=1" -a "[fan:0]/GPUCurrentFanSpeed=75" must be sent to a well defined X display. That mean that you are connected.
See "6. Connecting to Remote X Servers" from [http://www.makelinux.com/man/1/A/alt-nvidia-173-settings](http://www.makelinux.com/man/1/A/alt-nvidia-173-settings)
I don't know if it can help.

---

