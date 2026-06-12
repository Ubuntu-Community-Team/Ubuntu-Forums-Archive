---
title: "xorg.conf missing"
date: 2010-05-26
forum: Hardware
---

### Post by sqrooup on 2010-05-26
I am having a problem with resolution; My highest is 800 x 680, and I have had this problem in Jaunty, Karmic, Lucid, Xubuntu Lucid, and Linux Mint (the last two are on my desktop right now), and to a lesser extent XP!
Looking at other posts and forums I am to edit /etc/X11/xorg.conf; the only problem is, there is no xorg.conf! Someone on the Linux Mint forum suggested I create one by hand, but I don't know how.

The monitor is a Relisys, but no system has recognised it (even in its XP days), but it is capable of 1280 x 1080, using "inxi -G" I got the graphics driver;
```
sqrooup@hal-desktop ~ $ inxi -G
Graphics:  Card Intel 82G33/G31 Express Integrated Graphics Controller X.Org 1.6.4 Res: 800x600@60.3hz 
           GLX Renderer Mesa DRI Intel G33 GEM 20090712 2009Q2 RC3 x86/MMX/SSE2 GLX Version 1.4 Mesa 7.6

```
As you can see it is an Intel driver.

---

### Post by mhgsys on 2010-05-26
True; In new versions of ubuntu the xorg.conf file is no longer there by default; however,. when created it will use it.

You can generate a xorg.conf

```
Switch to a tty ( press ctrl+alt+f1 (f2,f3 etc)
```
login with your username and password.

stop xdm with
```
sudo service xdm stop
```

then generate a xorg.conf with 
```
sudo Xorg -configure
```

this will create a xorg.conf.new in your home directory)
move the auto-generated xorg.conf.new to /etc/X11/xorg.conf


```
sudo mv xorg.conf.new /etc/X11/xorg.conf
```

Make changes you want to try 
```
sudo nano /etc/X11/xorg.conf
```
and start xdm again with

```
sudo service xdm start
```

---

