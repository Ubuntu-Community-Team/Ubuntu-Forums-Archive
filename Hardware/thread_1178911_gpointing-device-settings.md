---
title: "gpointing-device-settings"
date: 2009-06-05
forum: Hardware
---

### Post by afeasfaerw23231233 on 2009-06-05
From this thread
[http://ubuntuforums.org/showthread.php?p=7366299](http://ubuntuforums.org/showthread.php?p=7366299)
it said gsynaptics is obsolete from 9.04 on, it suggested gpointing-device-settings instead. 

But I've got ```
E: Couldn't find package gpointing-device-settings
```
when 
```
sudo apt-get install gpointing-device-settings
```

Thanks in advance.

---

### Post by Richardcavell on 2009-06-06
I have the same problem.

Richard

---

### Post by afeasfaerw23231233 on 2009-06-08
bump

---

### Post by inzaneg on 2009-06-24
Yeah, it isn't available in repos until karmic koala. I installed it on 9.04 from this repo: [https://launchpad.net/~sarvatt/+archive/ppa](https://launchpad.net/~sarvatt/+archive/ppa)

remember to choose jaunty for sources.list

---

### Post by afeasfaerw23231233 on 2009-06-26
This howto about synclient solved my problem:
[http://ubuntuforums.org/showthread.php?t=886449](http://ubuntuforums.org/showthread.php?t=886449)

---

### Post by mhall119 on 2009-07-20
You can also download the source code from here: [http://live.gnome.org/GPointingDeviceSettings](http://live.gnome.org/GPointingDeviceSettings)

I had to symlink /usr/local/lib/libgdps.so.0 to /usr/lib/libgpds.so.0 for it to work, but that's it.

---

### Post by CraigMcW on 2009-08-08
Can someone direct me to how to install th is?   I downloaded the gpointing-device-settings-1.3.1.tar.gz and cannot figure out what to do with it given the Ubuntu instructions for installation of non-repo software.  

make doesn't work (probably obviously) nor does sudo make install.

---

### Post by onguarde on 2009-12-13
[http://aur.archlinux.org/packages.php?ID=25663](http://aur.archlinux.org/packages.php?ID=25663)  yaourt -S gpointing-device-settings  on Arch.

---

### Post by btocb on 2009-12-25
[FONT=Arial]Hi dude,

(This works perfectly to me!)

You can download the devian package and install it from here:

[http://packages.debian.org/squeeze/i386/gpointing-device-settings/download](http://packages.debian.org/squeeze/i386/gpointing-device-settings/download)

just chose your architecture, download and install it:

To install a *.deb* file, simply double click on it, and then select [B]Install Package

[/B]               Or you can also install a *.deb* file by opening a terminal and typing:

            sudo dpkg -i package_file.deb


see ya!:guitar:[/FONT]

---

### Post by manjunathsinge on 2010-02-19
Use configure-trakcpoint - [http://tpctl.sourceforge.net/configure-trackpoint.html](http://tpctl.sourceforge.net/configure-trackpoint.html)

---

### Post by jaykee on 2010-03-04
Hey guys. I installed [Sysfsutils]("http://tpctl.sourceforge.net/configure-trackpoint.html") on my Ubuntu  9.10 (sony vaio VGN-CR31S) because of the problems with my touchpad, the tap responding is really bad and works only when it wants to. 

I wonder how to configure this program (sysfsutils)? How do i open the program, the installation was succesful.

---

### Post by bionaught on 2012-12-15
Glad I'm not alone...... Same o same o.....
Install  something in Linux and then discover there is no way of starting the interface.
Even after hours of going around in circles reading forums.
Still better than windows, but people thicker than me have have no chance at all of moving to Linux

---

### Post by howefield on 2012-12-15
Old thread back to sleep.

---

