---
title: "intel graphics power management"
date: 2011-01-23
forum: Hardware
---

### Post by 22namphcar on 2011-01-23
In Windows 7, my intel graphics card goes into power saving mode when I'm on battery, and I can adjust those settings in the power management settings.  Do the linux drivers for intel graphics (specifically, the 5700mhd module that come with the core i5 processor) support power management?

---

### Post by pixel_pusher on 2011-01-28
I've been tinkering with power mgmt and intel drivers too. Have an asus laptop running a core 2 duo and integrated video (intel gma 900). Intel supplies open source drivers, although it doesn't seem like ubuntu knows what to do with them. I have gotten some improvement with power consumption using pm-powersave, but no luck with display brightness or HD audio for that matter...

---

### Post by pixel_pusher on 2011-03-06
I finally got around to looking at this again, and I found a workaround that might be useful to others using Ubuntu with an intel chipset.... xgamma. From a terminal do: 
```

 xgamma

```
to view the current levels, or use the -gamma option to set the levels: 
```

xgamma -gamma 0.75

```
this will set the brightness to 75%.

Now, what I figured I'd try doing is just make a quick script to 
call xgamma and use that with pm-utils:
```

#! /bin/sh
######################################################################
# set the gamma levels to 75% on powersave mode
########################################################################
xgamma -gamma 0.75

```
(...on my monitor 0.75 is still rather bright, so edit the value to your taste.)

Stick this file into either  /etc/pm/power.d/, OR 
/usr/lib/pmutils/power.d/  and make sure to set execute permissions, otherwise, pm-powersave won't be able to run the script. (I just did chmod 777 ./filename out of laziness :)). 

..and if you don't have pm-utils, obviously you'll need to install it... just look for it in synaptic or do an apt-get.

Then, just do: ```
sudo pm-powersave true
``` 
Money!!! 

Nothing particularly fancy, but I'm glad I can finally have something close to battery-mode display settings. 
Main thing I'd like to do, is to automate turning pm-powersave on and off when the power source changes, and to have it switch the gamma vals back to default which I do not yet know how to do. Guess I'll look that up too...
 
Hope somebody else finds this useful!

Some other handy info:
a description of how to set xgamma automatically on startup, by modifying your xorg.conf file:
[http://ubuntuforums.org/showthread.php?t=414180](http://ubuntuforums.org/showthread.php?t=414180)

pm-powersave man pages:
[http://manpages.ubuntu.com/manpages/hardy/man8/pm-powersave.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/pm-powersave.8.html)

of course, I'm open to any suggestions on how to improve this little hack...

---

