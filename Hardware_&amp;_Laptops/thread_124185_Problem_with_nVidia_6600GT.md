---
title: "Problem with nVidia 6600GT"
date: 2006-01-31
forum: Hardware &amp; Laptops
---

### Post by wilsonisme on 2006-01-31
I searched the forum, read the walkthrough, but still need help. When linux is done booting, and gnome starts, my screen immediatly turns into a garbaled mess. My sound works fine, I can hear the startup sound

From what I have read I understand that ubuntu does not have native support for the 6600 GT, and you must install the drivers yourself. however I have a few questions:

How do I do this if I cant see what I am typing, because the display is messed up, because my card doesnt like gnome? I assume you need to some how switch to just the console and type it in manually but I do not know how to do this nor do I know the commands, and I want the latest and greatest drivers for the 6600 GT and not legacy drivers. From what I have read, it doesnt sound like the 6600GT drivers are available with apt-get, so where do I go from here?

:KS  Thanks :KS

---

### Post by o_fortuna on 2006-01-31
[QUOTE=wilsonisme]I searched the forum, read the walkthrough, but still need help. When linux is done booting, and gnome starts, my screen immediatly turns into a garbaled mess. My sound works fine, I can hear the startup sound

From what I have read I understand that ubuntu does not have native support for the 6600 GT, and you must install the drivers yourself. however I have a few questions:

How do I do this if I cant see what I am typing, because the display is messed up, because my card doesnt like gnome? I assume you need to some how switch to just the console and type it in manually but I do not know how to do this nor do I know the commands, and I want the latest and greatest drivers for the 6600 GT and not legacy drivers. From what I have read, it doesnt sound like the 6600GT drivers are available with apt-get, so where do I go from here?

:KS  Thanks :KS[/QUOTE]
If you get to the ugly screen, hit Ctrl-Alt-F2 on your keyboard (like Ctrl-Alt-Del in Windows). This will bring you to a black-and-white console (you'll need to log in probably, and note that you won't see your password as you type it in). Then you just type
```
sudo apt-get install nvidia-glx
```
When that's done, type
```
sudo nvidia-glx-config enable
```
Now you need to restart the X server. Type this:
```
sudo /etc/init.d/gdm stop
```
then
```
sudo /etc/init.d/gdm start
```
That should do it. Now Ctrl-Alt-F7 brings you back to the graphics. Hopefully. You may want to restart, which means going back to the console, Ctrl-Alt-F2, then hit Ctrl-Alt-Del to restart.

If you want the "latest and greatest" you can then go [here]("http://www.ubuntuforums.org/showthread.php?t=75074").

---

### Post by wilsonisme on 2006-01-31
Okay if I follow your exact instructions, can I then perform the following operation for the new shiny drivers from that link you provided? I am asking this because it feels like I would then have two drivers installed. Would linux know to use the new one or would I have to do something special other then the exact walkthrough below?








> sudo apt-get install nvidia-glx nvidia-settings linux-restricted-modules-`uname -r`
 > 
Make sure you have both the Universe and Multiverse repositories enabled.
 

finally, once I get the drivers (hopefully) installed from the console, it says to > sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
sudo nvidia-glx-config enable 
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

and obviously after the gedit to add:
> [Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;

Then it says to save the edited file. How do you go about saving in the console?

Sorry for all the noob questions, but im trying to learn, thanks for your help!

Oh, one more question! Does enabaling repositories in the package manager also enable them for when you are installing stuff in the console?

---

### Post by wilsonisme on 2006-02-01
\\:D/ Poke \\:D/

---

### Post by GameGod on 2006-02-01
If you want the latest drivers (it's a good idea), definitely use JUST the guide in the link he provided...

I'm pretty sure I had the problem that you described for a while, where I kinda had two drivers installed... Now I just have the latest one from the NVIDIA site and none of the packages from Synaptic installed.. :)

---

### Post by Sutekh on 2006-02-01
You will be fine using the NVIDIA drivers in the repositories for the 6600GT (speaking from experience)

I personally would follow this guide.

[Ubuntu Guide - Installing NVIDIA Drivers]("http://ubuntuguide.org/#installnvidiadriver")

Or if you follow tseliots guide, just use method 1.

[QUOTE=wilsonisme]Oh, one more question! Does enabaling repositories in the package manager also enable them for when you are installing stuff in the console?[/QUOTE]
Yes it will.  Synaptic is just a GUI for apt-get, so they use the same sources.list

---

### Post by wilsonisme on 2006-02-01
Alright thanks. Just wondering though, if linux can't handle having new drivers installed on top of ones it is currently using what would someone do if linux is using generic video drivers and they want to install ones from the manufacturer?

---

### Post by Sutekh on 2006-02-01
[QUOTE=wilsonisme]Alright thanks. Just wondering though, if linux can't handle having new drivers installed on top of ones it is currently using what would someone do if linux is using generic video drivers and they want to install ones from the manufacturer?[/QUOTE]
Well if you look at tseliots guide you may notice there is some editing you need to do in the xorg.conf?

Basically changing the 'nv' to 'nvidia' changes the drivers from the generic ones to the nvidia proprietry ones.

---

### Post by GameGod on 2006-02-01
[QUOTE=wilsonisme]Alright thanks. Just wondering though, if linux can't handle having new drivers installed on top of ones it is currently using what would someone do if linux is using generic video drivers and they want to install ones from the manufacturer?[/QUOTE]

The generic Nvidia drivers ("nv" in your xorg.conf) do not conflict with the official Nvidia drivers ("nvidia" in your xorg.conf)...
I was talking about having two versions of the official drivers installed... one from the repositories (installed via apt-get/synaptic), and one straight from the Nvidia site. (The install paths may have been slightly different or something, causing my possible conflict...)

No worries though, you should be good to go. :)

---

