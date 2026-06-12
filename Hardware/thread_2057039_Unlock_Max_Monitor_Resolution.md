---
title: "Unlock Max Monitor Resolution"
date: 2012-09-12
forum: Hardware
---

### Post by chrisinpants on 2012-09-12
I used to use Rivatuner to create a custom driver inf on Windows so that my Dell e722p would run at a higher resolution than the driver allows it to by default. The monitor was fine with that, as someone, somewhere, said it would be. Windows is long gone anyway after finally jumping to linux for good. Does anyone know of a way I can achieve similar functionality on Ubuntu and get my monitor to display more than 1152x864? It's locked as this in the settings, by the driver, and oddly, is displayed as a 15" monitor, which it is not...

---

### Post by papibe on 2012-09-12
Hi chrisinpants.

Could you post the content of these files?
```
/etc/X11/xorg.conf

/var/log/Xorg.0.log
```
Please paste them separately here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and then post back the links here.

Regards.

---

### Post by chrisinpants on 2012-09-12
Sure, but I have no xorg.conf in the dir you specified. Is that strange?

My log Xorg.0.log:

[http://paste.ubuntu.com/1201645/](http://paste.ubuntu.com/1201645/)

locate gives me:

/usr/share/X11/xorg.conf.d
/usr/share/X11/xorg.conf.d/10-evdev.conf
/usr/share/X11/xorg.conf.d/11-evdev-quirks.conf
/usr/share/X11/xorg.conf.d/11-evdev-trackpoint.conf
/usr/share/X11/xorg.conf.d/50-synaptics.conf
/usr/share/X11/xorg.conf.d/50-vmmouse.conf
/usr/share/X11/xorg.conf.d/50-wacom.conf
/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
/usr/share/man/man5/xorg.conf.5.gz
/usr/share/man/man5/xorg.conf.d.5.gz

---

### Post by papibe on 2012-09-12
Thanks.

Try this:
```
xrandr --newmode "1024x768_75"  78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync

xrandr --addmode VGA1 "1024x768_75"
```
Let us know how it goes.
Regards.

---

### Post by chrisinpants on 2012-09-12
As sudo it went:

X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  23
  Current serial number in output stream:  23


As home user, no entering commands. My (gui) display settings are as they were before.

---

### Post by papibe on 2012-09-12
Could you post the result of this command?
```
xrandr
```
Regards.

---

### Post by chrisinpants on 2012-09-12
Hmm:


Screen 0: minimum 320 x 200, current 1152 x 864, maximum 4096 x 4096
VGA1 connected 1152x864+0+0 (normal left inverted right x axis y axis) 300mm x 225mm
   1024x768       75.0 +   85.0     75.1  
   1152x864       75.0* 
   800x600        85.1     75.0  
   640x480        85.0     60.0  
   720x400        70.1  
   1024x768_75    75.0  


It fibs

---

### Post by papibe on 2012-09-12
Could you try this commands, and post the output if there's any?
```
xrandr --output VGA1 --mode "1024x768"

xrandr --output VGA1 --mode "1024x768_75"
```
Regards.

---

### Post by chrisinpants on 2012-09-12
Sure and thanks for keeping up. I'll be back tomorrow

xrandr --output VGA1 --mode "1024x768" - **Changes screen mode to 1024**
xrandr --output VGA1 --mode "1024x768_75"
xrandr: cannot find mode 1024x768_75

---

### Post by chrisinpants on 2012-09-26
I got there in the end. I had to use cvt to get more specific details on the required mode and add that, courtesy of this guyde:

[http://myit-solutions.blogspot.co.uk/2010/09/how-to-add-and-set-custom-display.html](http://myit-solutions.blogspot.co.uk/2010/09/how-to-add-and-set-custom-display.html)

---

