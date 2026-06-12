---
title: "NVIDIA Driver installation (6 screens problem)"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by biebo on 2009-11-12
hi all

i have been installing the NVIDIA Linux driver (190.42-pkg1.run) for my 103M card on my laptop.

It installs fine but when I reboot gdm it comes with 6 small screens ....

i am also posting a snap of my screen.

[IMG]http://img20.imageshack.us/img20/5859/12112009.jpg[/IMG]

---

### Post by biebo on 2009-11-19
still waitinig

---

### Post by biebo on 2009-11-26
still waiting !! :(

---

### Post by pedja_portugalac on 2009-11-26
Really bizard. First time I see something like that. May be you should ask for help on nvidia site or just use default driver from Ubuntu installation CD. I presume your screen isn't High Definition so why using nvidia driver outside of synaptic repository?

---

### Post by Sergio7676 on 2010-01-09
This problem has alreay been solved just follow the link [http://ubuntuforums.org/showthread.php?t=1182311&highlight=nvidia+103m&page=3](http://ubuntuforums.org/showthread.php?t=1182311&highlight=nvidia+103m&page=3)

On the other hand, I found another solution. It is quite easy all you have got to do is:

1- Download the beta drives for the 103m from nvidia (195) in your Desktop.

2- Remove the driver that ubuntu is using, (if any).

3- press ctrl + alt + f1

4- sudo service gdm stop

5- cd Desktop

6- sudo sh NVIDIA-Linux-x86-195.30-pkg1.run.part' 

7- sudo reboot


After this you should be done and you should have just one screen!. I hope
it works for you!

:D

---

### Post by 3ijoe on 2010-03-20
The best solution is here:

When you get 6 screens in Ubuntu, replace the whole written in xorg.conf and paste this ..

Section "Device"
Identifier "Default Device"
Driver "nvidia"
Option "NoLogo"     "True"
Option "ModeValidation"    "NoTotalSizeCheck"
EndSection

.......... i.e in xorg.conf , you should have only the above paragraph. but remember you should either login as root or ctrl+alt+f1 i.e tty mode and type ..
edit the xorg.conf by using this command... vi /etc/X11/xorg.conf 
save it. and start ur x server i.e type sudo /etc/init.d/gdm start

..............i faced the same problem and now my graphics just fine........good luck.

---

### Post by 5735guy on 2010-03-20
How To Install Nvidia 185.xx, 190.xx and 195.xx Drivers In Ubuntu, From A Launchpad Repository
[http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html](http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html)

---

