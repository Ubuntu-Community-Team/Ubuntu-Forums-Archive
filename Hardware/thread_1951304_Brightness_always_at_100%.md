---
title: "Brightness always at 100%"
date: 2012-04-02
forum: Hardware
---

### Post by x-shaney-x on 2012-04-02
I am currently using an Acer 5742 which has various problems with brightness control.

Using "acpi_backlight=vendor" in the grub line does give me back full control via the brightness keys and it does automatically dim on inactivity but the problem is the brightness is set to full all the time unless I manually alter it.

Is there any way to get it to dim when on battery in unity?

In Windows 7 and KDE it does this without me having to change anything, I just pull out the plug and it dims automatically but not in unity.  Always 100% in unity :(

---

### Post by Toz on 2012-04-06
> **x-shaney-x said:**
> Is there any way to get it to dim when on battery in unity?

What is the contents of your /sys/class/backlight directory? Mine is:
```
$ ls /sys/class/backlight/
acpi_video0  intel_backlight
```

My active backlight interface is the acpi_video0 one. The contents of that directory is:
```
$ ls
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power	   device      power	       type

```

The max_brightness file holds the maximum brightness value my system can handle:
```
$ cat max_brightness 
24

```

The actual_brighntess file contains my current brightness value:
```
$ cat actual_brightness 
24

```

You should be able to manually manipulate the brightness by echoing a value between 0 and the contents of max_brightness to the brightness file:
```
echo 12 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

If that works (you can manually manipulate the brightness), then changing the brightness when the system goes to battery can be accomplished by creating a script in the /etc/pm/power.d directory.

1. Create a file called battery_brightness:
```
sudo gedit /etc/pm/power.d/battery_brightness
```
...with the following content:
```

#!/bin/bash

case $1 in 
   true) #on battery mode
      echo xxx > /sys/class/backlight/yyy/brightness
      ;;
   false) # on ac mode
      echo zzz > /sys/class/backlight/yyy/brightness
      ;;
   *) ;;
esac
```
...where:
- xxx = the lowered brightness value (on battery) that you want
- yyy = the directory name of the valid backlight interface 
- zzz = the normal brightness value (on ac) that you want

2. Save the file

3. Make the file exectuable:
```
sudo chmod +x /etc/pm/power.d/battery_brightness
```

4. Test.

---

### Post by x-shaney-x on 2012-04-06
Many thanks for that info.  It certainly looks doable now but seems a lot of work to do something that Windows and KDE can both do automatically.

In particular, KDE (Kubuntu) is the same system and it appears to be something Gnome/Unity related that is not allowing the brightness to automatically dim on battery.
I'm not sure whether or not Gnome does this by default on any system actually.

---

### Post by thaelim on 2012-04-07
This is a feature that was removed in the transition from Gnome 2 to Gnome 3. I have no idea why this would have been done, as it is an absolutely critical piece of power saving configuration. After all, the screen backlight is the biggest power drain on most notebook computers.

I am currently working on an extension for Gnome that will bring back the ability to control the backlight brightness with more fine-grained detail. PM me for more info.

---

