---
title: "HP DV3 Brightness on Ubuntu 11.04"
date: 2011-05-26
forum: Hardware
---

### Post by tjameson on 2011-05-26
I found some older threads about HP DV3 on older versions of Ubuntu, but I just wanted to post about the current version.

I am running Ubuntu 11.04 on my HP DV3 2155. Pushing the brightness button doesn't work. I can tell that Gnome Indicator Applet is registering the command, but the screen brightness does not change.

I am able to get the brightness working through a script:

Dim.sh

```
#!/bin/bash --
#Decrease Brightness
#get current brightness in hex and convert to decimal
var1=`sudo setpci -s 00:02.0 F4.B`
var1d=$((0x$var1))
#calculate new brightness
var2=`echo "ibase=10; obase=16; a=($var1d-16);if(a>15) print a else print 15" | bc`
echo "$0: decreasing brightness from 0x$var1 to 0x$var2"
sudo setpci -s 00:02.0 F4.B=$var2
exit
```

Bright.sh

```
#!/bin/bash --
#Increase  Brightness
#get current brightness in hex and convert to decimal
var1=`sudo setpci -s 00:02.0 F4.B`
var1d=$((0x$var1))
#calculate new brightness
var2=`echo "ibase=10; obase=16; a=($var1d+16);if(a<255) print a else print 255" | bc`
echo "$0: increasing brightness from 0x$var1 to 0x$var2"
sudo setpci -s 00:02.0 F4.B=$var2
exit
```

On old versions, I could set this once I booted up and it would stay forever, but now Ubuntu is resetting the brightness every time that I wake from sleep.  I would really like to solve this problem. I've tried the solutions on other pages in the past, but not on this version.

---

