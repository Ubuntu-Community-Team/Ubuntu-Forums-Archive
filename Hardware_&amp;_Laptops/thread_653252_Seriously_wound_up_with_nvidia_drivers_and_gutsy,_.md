---
title: "Seriously wound up with nvidia drivers and gutsy, help!!"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by tom1979 on 2007-12-29
Ive search and tried several lots of terminal script and using syneptic , but when im trying to install packaged they dont complete, when i close the installer it informs me not all packages were installed.

Now my laptop keeps freezing on reboot and when it eventually boots its in low graphics mode!

Really confused and need a line by line diagnosis and fix from somebody clever!! thanx a lot, tom.

---

### Post by taurus on 2007-12-29
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Now, restart your X server again with <Ctrl><Alt>Backspace.

---

### Post by tom1979 on 2007-12-29
I can only log in in recovery mode at the mo, using my thinkpad to post with. result of that command tells me failed to open package into file for reading: no such file or directory.

Not in recovery mode the graphics appear spot on and theres no internet access...

thanx, tom

---

### Post by tom1979 on 2007-12-29
ok thats weird, the reset command took me back into my 'proper' install and appears normall again with good graphics :S very confused, could you explain why this happened and is this a permenant fix? thanx a lot, tom

---

### Post by Vesslan on 2007-12-29
hi, i had similar problems some days ago when i re-installed gutsy 7.10 (amd64)
don't know if this helps you or if it is the best way but..

first, in that low-graphics mode i downloaded the driver from nvidia.com
then something like apt-get install build-essential
then i killed all X and gdm processes
logged in as root and sh Nvidia-Linux.169.04........
then rebooted

(the reason i use the 169.04 instead of 169.07 is because of the fan bug, if your video card don't have a fan it doesn't matter i guess)

---

### Post by tom1979 on 2007-12-29
Id need a line by line code to fix that, i have geforce 8400m g dont know if it has a fan or not!

At the moment i have a new problem where i cant download updates or install new stuff, like for the sound fix, or any extra software in synaptic :(

---

### Post by Vesslan on 2007-12-29
if the card have a fan and you install the latest nvidia driver you will, as i did, notice the sound of a jet engine coming from your computer since the fan get stuck on 100% :p

ok, this is how to get the proprietary nvidia driver. (i hope i get it right..)

- go to nvidia.com and download the driver you need. there is a thing to fill in that redirects you to the right driver. after downloading,

- press ctrl - alt - f1
   to get to the text based log in, there log in as usual with your name and password.
   (if you need to get back to the graphical mode press ctrl - alt - f7)

- type: sudo killall X && killall gdm

- go to the directory where you saved the driver file
  for example cd /home/yourname
  to list the files type ls

- try typing: sudo sh NVIDIA-Linux-x86_64-169.07-pkg1.run
  nb! the filename in that command was an example, use the name of the file you have downloaded.
  sudo sh nameofthefile

does this work? any error messages?

---

### Post by Vesslan on 2007-12-29
---

---

### Post by Vesslan on 2007-12-29
if you get an error message from the nvidia installer about libc header is missing
type: sudo apt-get install build-essential

if it says you need to shut down X
hm.. try "sudo killall X" again
remember, everything is always case sensitive..

also, you might have to change your /etc/X11/xorg.conf  so that

"Section "Device"
    Identifier     "nVidia Corporation NVIDIA Default Card"
    Driver         "nvidia"                                                                 <---- this says" nvidia" instead of "nv"
EndSection"

---

### Post by tom1979 on 2007-12-29
having problems installing packages, that includes the plugin for firefox to see flash boxes on nvidia's site!! made a new post about this one.... damn this installs being a pig, and i havent even touched the wifi yet :(

---

### Post by Vesslan on 2007-12-29
ok i'll try to give you the direct link,

 32bit OS :     [http://us.download.nvidia.com/XFree86/Linux-x86/169.07/NVIDIA-Linux-x86-169.07-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/169.07/NVIDIA-Linux-x86-169.07-pkg1.run)
 64bit OS:      [http://us.download.nvidia.com/XFree86/Linux-x86_64/169.07/NVIDIA-Linux-x86_64-169.07-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/169.07/NVIDIA-Linux-x86_64-169.07-pkg2.run)

---

### Post by tom1979 on 2007-12-30
I reinstalled and drivers were downloaded automaticly, but wifi didnt work, so now reinstalled 32bit and not 64bit gutsy, hopefully the wifi will now work!

---

### Post by g2g591 on 2007-12-30
the easy way to install drivers (the old ones though, not the 169s) sudo apt-get install nvidia-glx-new

---

