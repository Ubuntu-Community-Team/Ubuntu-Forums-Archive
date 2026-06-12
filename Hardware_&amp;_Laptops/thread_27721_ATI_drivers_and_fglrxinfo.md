---
title: "ATI drivers and fglrxinfo"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by i-tech on 2005-04-17
I tried to install ATI drivers edited xorg.conf and restarted xserver. when i execute fglrxinfo is says 
 > root@ubuntu:/home/itech # fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org]("http://www.mesa3d.org")
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
 
help please!

---

### Post by telmo on 2005-04-17
[QUOTE=i-tech]I tried to install ATI drivers edited xorg.conf and restarted xserver. when i execute fglrxinfo is says 
  
help please![/QUOTE]

You haven't installed it right.

Maybe this can help:

```

Download the ATI Xorg driver from ATI website
Find and delete all fglrx files and directories.
(Ctrl+Alt+F1)
#/etc/init.d/gdm stop
#alien <driver package name>
#mv /lib/modules/<kernel version>/kernel/drivers/video/fglrx.ko $HOME
#dpkg --force-overwrite -i <driver package name>.deb
#rmmod fglrx
#cd /lib/modules/fglrx/build_mod
#sh make.sh
#cd ..
#sh make_install.sh
#cp fglrx.ko /lib/modules/<kernel version>/misc/
#depmod -ae
#fglrxconfig
#modprobe fglrx
#/etc/init.d/gdm start

$fglrxinfo
```

Good luck! ;)

---

### Post by HackeR_54 on 2005-04-17
Maybe you have the same problem as i had

add to your xorg.conf

Load "GLcore"

Option "UseInternalAGPGART" "no"

look up where they are supposed to be set and put them in if they aint there

DONT FORGET TO REBOOT COMPUTER!!

---

### Post by i-tech on 2005-04-18
there's GLCore and  Option         "UseInternalAGPGART" "no" in my xorg.conf so it didnt work out seems not the same problem :?  
  >  Find and delete all fglrx files and directories
How will i do it?

---

### Post by HackeR_54 on 2005-04-18
I also got the same problem now!  :roll:

---

### Post by Dinler on 2005-04-18
[QUOTE=HackeR_54]I also got the same problem now!  :roll:[/QUOTE]
Mee too!

---

### Post by rotorwash on 2005-04-18
Visit [this](http://www.ubuntuforums.org/showthread.php?t=24557&highlight=fglrx+install) thread. It will get you going.

---

### Post by alastair on 2005-04-18
And if you are still stuck - post :

a) /var/log/Xorg.0.log
b) /etc/X11/xorg.conf

NOTE - you never need to restart your system to change X config - just restart the X server e.g.

a) log out and CTRL+ALT+BACKSPACE at the GDM login screen or
b) from a VT terminal : /etc/init.d/gdm restart

---

