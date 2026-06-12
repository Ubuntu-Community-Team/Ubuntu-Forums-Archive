---
title: "NVidia Driver resolution very tiny"
date: 2008-06-01
forum: Hardware
---

### Post by dragonfyre13 on 2008-06-01
For some reason, since upgrading to Hardy, my nvidia driver resolution is insanely small. Small enough that it doesn't correctly display the login page, and when I login from memory (username [enter] password [enter]) it shows everything so squished down that I can't even open the nvidia settings without it going off the screen. It's somewhere in the 320x480 range.

I've moved to the nv driver, with no compositing effects, no hardware rendering, etc. My CPU is pegged pretty consistently when doing anything with videos, which is a large part of what I use the computer for.

I've tried reconfiguring xorg every way I know how. I've stripped out all special parameters, and slimmed it down so that it only has the max resolution (1680x1050 I think) and that still doesn't affect it.

The card is a 6800GT. I'm using the Envy drivers (the repo drivers don't work. It can't find the kernel driver no matter what I reinstall, or configure, and hasn't been able to since Dapper. This is an upgrade from as far back as early Warty Warthog)

---

### Post by Will240 on 2008-06-01
I have a Dell Inspiron 1520 and I am having sort of the same problem. Can anyone help?

---

### Post by housam on 2008-06-01
try this : System > Preferences > Screen Resolution
If you didn't find your settings , try the following :

```
sudo nano /etc/usplash.conf
```
 you will got something like that 

> # Usplash configuration file
# These parameters will only apply after running update-initramfs.  

add the required resolution 

> # Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=[COLOR="red"]1280[/COLOR]
yres=[COLOR="Red"]800[/COLOR]  

 set [COLOR="red"]x & y[/COLOR] as you want then reboot and type :

```
sudo dpkg-reconfigure usplash
```
 then check for the new settings -- System > Preferences > Screen Resolution and select the new one.
__________________

---

