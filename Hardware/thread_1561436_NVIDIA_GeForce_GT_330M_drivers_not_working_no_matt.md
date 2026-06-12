---
title: "NVIDIA GeForce GT 330M drivers not working no matter what("
date: 2010-08-26
forum: Hardware
---

### Post by anonomo on 2010-08-26
Hi sorry for new thread similar to much talked about topic
But i have tried following every recipe i found on other threads that i could get my fresh-to-linux head around and no successes

Currently - running in nomodeset
Using prepackaged driver
X.Org X server -- Nouveau display driver (experimental) i think thats what it is
=
video stutters, window animation lags, spash screen at startup looks is  a pixelated impression of a computer chip in a blizzard

Failed my attempts to fix this:


[LIST]
[*]    Remove nomodeset = No display whatsoever
[/LIST]


[LIST]
[*]    Install Firmware Driver from NVIDIA website = causes errors to boot
[/LIST]

>  (EE) screens found but none have a usable configuration etc.
after eventually displaying gnome splits the screen down the middle, and other wierdness



[LIST]
[*]     pasted and saved this in xorg.conf
[/LIST]
      S```
ection "Device"
      Identifier "Device0"
      Driver "nvidia"
      VendorName "NVIDIA Corporation"
      Option "ConnectedMonitor" "DFP-0"
      Option "CustomEDID" "DFP-0:/etc/X11/sonycw.bin"
      EndSection
```then run nvidia-glx-185_185.18.36-0ubuntu9_amd64.deb
in package installer
i havent copied the error message, but basically - failed to install


[LIST]
[*]installed  nvidia-glx-180 from a canonical repository somewhere
[/LIST]
on reboot it does a very long check for errors, slowly loads a pixeled version of the start up screen, gives you a bunch of options, the only one that lets you in to gnome is - &#341;un in low grapics mode


:o so as you can see i&#314;l give anything a go but i;ve got no idea what i&#7743; doing
would hugely appreciate some help on this,   
i&#7743; patient but cant wait to be editing  translating and subtitling videos which is the  main reason i just migrated here
;)


Vaio CW26 Ubuntu Studio 10.04 x64 / windows 7 x64

---

### Post by ellgor on 2010-08-26
Hi,

Found this guide that simply works:

1) Download Newest Nvidia drivers from their website
2) Open module blacklist as admin:

sudo gedit /etc/modprobe.d/blacklist.conf
3) Add these lines and save: 

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
4) Uninstall any previously installed Nvidia drivers: 

sudo apt-get --purge remove nvidia-*
5) Reboot your computer
6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
7) Login and cd to the directory where you saved your file
 Install drivers

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you have, be precise as errors will result in "no such file"
8) Follow the onscreen guide from Nvidia and when done
9) Start GDM

sudo service gdm start

Regards, Ellgor.

---

### Post by anonomo on 2010-08-29
hi ellgor thanks for the helpful directions
didnt reply cause was trying to find someone in this city who better knew how to follow them, but sofar noluck.

myself no problems up till #6

sudo apt-get --purge remove nvidia-*
indeed removed a bunch of stuff, (cant remember exactly what but 135MB worth)

but then reboot computer &

> 6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)

No Error Message! LoL i cant believe i&#7743; complaining about there NOT being error!
I guess that there&#347; no error because the noveau dispay driver is still doing the displaying?

So then I try going on from there anyhow, and going into sh 
tried from terminal and also from root in grub console

but from sh dont know how to cd (change directroy?) to home folder where NVIDIA firmware driver is kept?
cd /home or 
username@machinename home/
or a whole bunch of different variations i try just get : no such folder

hahah
really sorry its the really simple stuff stumping me
its just tough when the (hopefully) the hardest part is at the installation before getting familiar
but will keep trying 
cheers for helping!

---

### Post by ellgor on 2010-08-29
Hi,

Right, to cd to where the directory is, when you open in a terminal you are already at your home folder,ok, if you type in ls this will show all the folders, again type cd (example, cd Downloads) and this will show all the files in Downloads, if Nvidia is indeed in Downloads then thats it, follow the instructions as per guide make sure the file is the one you have and not the one shown on the guide.

Regards, Ellgor.

---

### Post by anonomo on 2010-09-04
just to say THANKYOU and resolved with the help of local friend :D
who did so by chucking some kind of edid info .bin file in etc/x11
kiling the x-server
and theres a brand new driver up at NVIDIA site as of 2 days ago,
all running fast and pretty :p

---

