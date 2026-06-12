---
title: "Easy way to install nVidia 18x.xx driver?"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by beastrace91 on 2009-02-04
In the past I have had a less than positive experience trying to install nvidia drivers using the files provided right from nVidia's website... but I need to upgrade to the 18x.xx driver so Guild Wars will run properly, does anyone know if there is a repository out there or a script maybe that will auto install it for me? In the past I have always used Envyng or package manager, how ever neither of these have the latest drive I need.

~Jeff

---

### Post by avtolle on 2009-02-04
Don't know of anything out there for Ubuntu. Installing the driver following the directions found on the nVidia site wasn't too painful for me (did it to upgrade to the latest driver for a card that was working OK with the 177 driver supplied, but wanted to see if the latest and greatest gave me anything extra, which it might, but that's another story). How comfortable are you with the command line from the terminal, as this is where you will be to install directly?

---

### Post by ridetheteapot on 2009-02-04
the installer is that script, and prolly couldnt get any easier.
there are 2 downsides. 1, you update yourself -- phoronix always has a page up when new drivers come out, so thats the easiest way to stay on top of things. 2, when you upgrade kernel version you _have_ to recompile the module.

1. get the nvidia installer from the ftp (ftp has latest drivers)
[ftp://download.nvidia.com/XFree86/](ftp://download.nvidia.com/XFree86/) (directory structure : 32 or 64 bit installers, then by version, then get the one with pk1.run suffix)

2. open tty1 <ctrl><alt>+f1 and stop gnome "sudo /etc/init.d/gdm stop"
3. make sure the old module is not still loaded "sudo rmmod nvidia"
4. cd to the download directory and "chmod +x" the installer file
5. run the installer as root "sudo ./nvidia-blahblah"
6. follow instructions (pretty self-explanitory steps) and then when you get asked about running nvidia-xconfig say no. I am guessing that your xorg.conf is already been configured by a previous driver installation.
if you need to run it later you can by "sudo nvidia-xconfig" and it will backup your old one if you forget to. you can verify that your pretty much good to go by a "grep nvidia /etc/X11/xorg.conf"
if you see Driver "nvidia" you can try restarting gnome and checking it out.
7. "sudo /etc/init.d/gdm start"

---

### Post by beastrace91 on 2009-02-04
Alrighty, I will give that a try on friday (have a few papers to write between now and then and don't want to crash my system while I need it lol) and get back to you, thanks for the input.

~Jeff

---

