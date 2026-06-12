---
title: "Logitech Cordless Mini Optical Mouse doesn't work at all"
date: 2006-09-03
forum: Hardware &amp; Laptops
---

### Post by mixandgo on 2006-09-03
any ideea how to fix this ? I've searched and tryed everything on this forum but I still can't make my mouse work, at all.

---

### Post by ShuaM75 on 2007-09-29
I also have this same problem. 
Mine is a Logitech Cordless Optical Mouse for laptops.

Any help would be great.

---

### Post by Triskal on 2007-10-01
I plugged mine in and it worked out of the box.  It is logged as using lmpcm_usb.c: v0.5.5:USB Logitech MdeiaPlay Cordless Mouse driver.  I'm using 2.6.20-16-generic kernel.

---

### Post by java_java_and_more_java on 2007-12-01
Mine also worked out of the box except for side-scrolling. Any ideas?

---

### Post by evilteddy on 2008-01-17
I too have this problem with a wireless optical v220 logitech mouse. It recognizes the mouse reciever but how do I get this to work as a mouse?

---

### Post by Yellow Pasque on 2008-01-17
evilteddy,

EDIT: Make sure you have the evdev driver.
```
sudo apt-get install xserver-xorg-input-evdev
```

Make a backup of you xorg.conf and get the device info
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
cat /proc/bus/input/devices
```

Then use the following block of code in xorg.conf, but fill in the Dev Name and Dev Phys with the info you got from the cat command:
```
Section "InputDevice"
        Identifier  "Logitech V220"
        Driver      "evdev"
        Option      "Dev Name" "Logitech USB Receiver"
        Option      "Dev Phys" "usb-0000:00:1d.0-2/input0"
        Option      "SendCoreEvents"
        Option      "evBits" "+1-2"
        Option      "keyBits" "~272-287"
        Option      "relBits" "~0-2 ~6 ~8"
        Option      "Pass" "3"
EndSection
```

Then put the following line in the ServerLayout section:
```
InputDevice "Logitech V220"
```
Save and reboot.

---

### Post by arbulus on 2008-03-30
> **Temüjin said:**
> evilteddy,

EDIT: Make sure you have the evdev driver.
```
sudo apt-get install xserver-xorg-input-evdev
```

Make a backup of you xorg.conf and get the device info
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
cat /proc/bus/input/devices
```

Then use the following block of code in xorg.conf, but fill in the Dev Name and Dev Phys with the info you got from the cat command:
```
Section "InputDevice"
        Identifier  "Logitech V220"
        Driver      "evdev"
        Option      "Dev Name" "Logitech USB Receiver"
        Option      "Dev Phys" "usb-0000:00:1d.0-2/input0"
        Option      "SendCoreEvents"
        Option      "evBits" "+1-2"
        Option      "keyBits" "~272-287"
        Option      "relBits" "~0-2 ~6 ~8"
        Option      "Pass" "3"
EndSection
```

Then put the following line in the ServerLayout section:
```
InputDevice "Logitech V220"
```
Save and reboot.



I did this and my mouse still isn't recognized.  Any ideas?

---

### Post by LiamGaerity on 2008-05-27
Hi all. Newbi here. I've followed the instructions to modify /etc/X11/xorg.conf file to what was posted. However, the tilt wheel buttons still does not work. My xorg.conf file looks like: 

```
Section "InputDevice"
        Identifier  "Logitech V220"
        Driver      "evdev"
        Option      "Dev Name" "Logitech USB Receiver"
        Option      "Dev Phys" "usb-0000:00:1d.0-2/input0"
        Option      "SendCoreEvents"
        Option      "evBits" "+1-2"
        Option      "keyBits" "~272-287"
        Option      "relBits" "~0-2 ~6 ~8"
        Option      "Pass" "3"
        Option      "HWHEELRelativeAxisButtons" "7 6"
EndSection
```

Can anyone please provide further suggestions on how to get the tilt wheel to scroll forward and backward in Firefox, etc ..., ?

Thanks.

---

### Post by tobiasly on 2008-06-04
> **LiamGaerity said:**
> Can anyone please provide further suggestions on how to get the tilt wheel to scroll forward and backward in Firefox, etc

Liam, have you tried btnx? Much better than manually screwing w/ xorg.conf. It has a "capture" mode that automatically detects all your buttons (scrolling is considered just another button click on a mouse), then you can assign any mouse button to any action you want.

It worked wonders to get my Logitech MX Revolution mouse working. It has 2 scroll wheels and 5 regular buttons and it was able to map them all.

[http://ubuntuforums.org/showthread.php?p=2727025](http://ubuntuforums.org/showthread.php?p=2727025)

---

### Post by LiamGaerity on 2008-06-05
Tobiasly, That worked like a charm!!! Thank you very much.

---

