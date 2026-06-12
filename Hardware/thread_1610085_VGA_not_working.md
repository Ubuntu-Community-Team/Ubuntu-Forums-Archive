---
title: "VGA not working"
date: 2010-10-31
forum: Hardware
---

### Post by Chriswa on 2010-10-31
I bought a Dell Mini 12 a while back and changed it to Ubuntu 10.10 netbook recently.  The only problem i am having is that it wont detect the VGA connection.

I have tried the xrandr --output VGA --auto and it replies saying output VGA not found, i would really like to get this working.

Thanks in advance!

---

### Post by IcarusR on 2010-10-31
I believe it is 'VGA1'

To find all displys available in a terminal run

```
xranr
```

I get the following

```
~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     75.0     70.1     60.0  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     60.0     59.9  
   720x400        70.1  
LVDS1 connected (normal left inverted right x axis y axis)
   1280x800       60.0 +
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV1 disconnected (normal left inverted right x axis y axis)

```

See the xrandr manual for details how to use.

```
man xrandr
```

---

### Post by Chriswa on 2010-10-31
when i type in xrandr it only shows the default (laptop screen) and not my VGA monitor. Although it does say failed to get size of gamma output display.  
No luck yet

---

### Post by P4man on 2010-10-31
Most laptops have a Fn+function key to enable external VGA. Have you tried that yet?

---

### Post by Chriswa on 2010-11-01
doesn't help.  And its not a hardware problem; i've tried many different set-ups.  I'm thinking maybe i am missing a driver?

---

### Post by P4man on 2010-11-01
Seems you have a GMA500 in that laptop. Perhaps this helps:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

---

### Post by Chriswa on 2010-11-01
trying now.  I was under the impression that 10.10 had GGMA500 support inbuilt

---

### Post by Chriswa on 2010-11-01
worked, thanks guys

---

