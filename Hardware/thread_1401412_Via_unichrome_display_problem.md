---
title: "Via unichrome display problem"
date: 2010-02-08
forum: Hardware
---

### Post by keno.mentor on 2010-02-08
Hello,

I have recently installed Ubuntu 9.10 having heard that the display driver for the via S3 unichrome onboard graphics chipset had been developed.  However, the display still has low resolution and looks very 'jagged'.  The strange thing is that the opening 'loading' screen has perfect resolution but as soon as the desktop opens, the resolution is drastically reduced.

I have a Fujitsu-siemens notebook.

I am a complete Linux newbie so please be gentle with technicalities :)

Much thanks,
keno

---

### Post by pi/roman on 2010-02-08
You probably need to create an xorg.conf file. Use this terminal command:
```
sudo X :1 -configure
```Press Alt/F2 to open the xorg.conf you just created type:
```
sudo gedit ~/xorg.conf.new
```Press Alt/F2 again to open your existing xorg.conf type:
```
sudo gedit /etc/X11/xorg.conf
```If xorg.conf is empty just copy everything into it.  If it is not then look up a guide on editing it.
Look in your xorg.conf manual by typing in a terminal:
```
man xorg.conf
```

---

