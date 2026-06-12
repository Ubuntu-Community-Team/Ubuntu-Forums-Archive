---
title: "Cannot reconfigure xserver-xorg, cannot open display."
date: 2008-09-14
forum: General Help
---

### Post by korvics on 2008-09-14
Hi, I've installed ubuntu but when it loads I get a black screen. The most common solution to a problem is to use the following command 

```
sudo dpkg-reconfigure xserver-xorg
```

However when I do it, after I configure the keyboard layout the thing spits out this error message without even letting me to change the driver to vesa:

```
xserver-xorg postinst warning: overwriting possibly-customised configuration file
```

After following the guide at [HTML]http://ubuntuforums.org/showthread.php?t=839689[/HTML] I tried using the command:

```
gksu displayconfig_gtk
``` which was supposed to fix the problems with the xserver, however all when I type this command I get yet another error message:

```
gksu:6155 GTK-WARNINGxx: cannot open display
``` 

So this is where I am stuck. I am a newby to Ubuntu and this is my first experience which is turning out rather frustrating. I apologize for the lenghty post. All help would be appreciated. 



Monitor that I have:

Samsung Sync Master 17inch

Video Card:

Radeon 9800XT 

Thanx.

---

### Post by Pelham123 on 2008-09-15
Try booting into recovery mode and use 'xfix'

---

