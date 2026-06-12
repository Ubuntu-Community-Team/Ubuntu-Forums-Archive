---
title: "LCD brightness issues with Hardy on Toshiba Satellite A100"
date: 2009-01-16
forum: Hardware
---

### Post by MrCartwheel on 2009-01-16
Hi there,

have recently installed Ubuntu Hardy 8.04 (Kernal 2.6.23-24-generic) on my Toshiba Satellite a100 series laptop.

I cannot control lcd brightness. Have tried using the echo command:

```
sudo echo -n 50 > /proc/acpi/video/VGA/LCD/brightness 
``` 

But this results in the following 

```
bash: /proc/acpi/video/VGA/LCD/brightness: Permission denied
```

I was attempted to follow instructions from a similar issue on [this thread]("http://ubuntuforums.org/showthread.php?t=839694") but I got a bit lost - I'm a newbie 

I have tried the following:
- using the LCD brightness Applet
- looking at Bios

Would welcome any suggestions...

---

### Post by 0xbaadf00d on 2009-03-28
*bump*

I have been trying to fix the same problem on my A355D

---------EDIT-----------

do this: first sudo su or sudo -s

then cat the brightness file to determine supported brightness levels.
choose one of those levels, replace 50 with that, and it should work

---

### Post by wmunguiam on 2011-02-05
I have the same issue with brightness control

I tried>  but without success

```
root@server:~# echo -n 44 > /proc/acpi/video/GFX0/DD02/brightness 


```

I could change that value> from 72 to 44  BUT brightness is still high

```
root@server:~# more /proc/acpi/video/GFX0/DD02/brightness 
levels:  8 20 32 44 58 72 86 100
current: 44 
```

Some idea?

---

