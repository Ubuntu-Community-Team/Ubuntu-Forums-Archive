---
title: "nvidia Geforce 8200 flickeing screen"
date: 2008-12-17
forum: Hardware
---

### Post by britstar on 2008-12-17
hi, 
I have been having a problem with getting the on board video to work on my mobo its a elitegroup GF8200A v 1.0. i have tried ubuntu 8.0 and 8.1 but each has the same problem. after installing the Nvidia driver 177 and rebooting their is a white overlay that flickers on and off on the screen. after days of trouble shooting i am stuck. currently i have installed ubuntu 8.0 32bit with the nvidia driver version 173.14.12 i got from installing envyNG witch seems to work better then any other driver even the new 180 witch made 3/4's of the screen dark brown. it seems that at any resolution 800X600 and lower the problem does not occur. if you have any suggestions please post.

Thanks, Brit

---

### Post by starcannon on 2008-12-17
[LEFT]My manual install guide is here (be sure to print it out and have the latest stable driver downloaded from nvidia before starting any of this):
[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

Brit, I generally manually install my nvidia drivers; that said, I have had great luck with the 177's on my 8400m gs. Something to try before doing anything too radical may be lets try installing the 177's using envy since you already have that handy. Then open a terminal:
Applications>Accessories>Terminal
and try:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo rm /etc/X11/xorg.conf
sudo nvidia-xconfig

```
The first line backs up your  current xorg.conf in case we need it to get you back to square one.
The second line removes the xorg.conf
The third line builds a new one.

If this fails and you get stuck at a command line then a manual install may be just the thing to do next.

My manual install guide is here (be sure to print it out and have the latest stable driver downloaded from nvidia before starting any of this):
[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

And whatever you do, please backup anything important; while installing a video driver really isn't a detriment to your data, you can never be to careful, especially if you don't have /home on its own partition.

GL and if you get really stuck, remember you can always put in the LiveCD to get back here for help and support.


[/LEFT]

---

### Post by britstar on 2008-12-18
does envyng support the 177 driver yet? on mine i just have 173.14.12

thanks, Brit

---

### Post by britstar on 2008-12-18
i did a manual install of the 177.82 driver using your instructions but i still have the white flickering screen.

Thanks, Brit

---

