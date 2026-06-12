---
title: "[Lucid] Asus laptop, wish to disable touchpad click"
date: 2010-05-25
forum: Hardware
---

### Post by tdennist on 2010-05-25
Hello,

I'm fairly new to Ubuntu as a full-time user.  My setup is an Asus UL30A (laptop) running 32 bit 10.04 with kernel 2.6.32-21.  I'm trying to find a way to disable the touchpad *click*.  I want to use the touchpad (and multitouch) but I don't want tapping on it to register as a click.  It is a bit too sensitive for my tastes.

After some googling, I've tried several things, which I will report on here.  First, I removed 'xserver-xorg-input-synaptics', which I read should simply disable the entire touchpad.  However, the touchpad is still working (tapping and all) even though:

```
$ aptitude search synaptics
p   gsynaptics                                                  - configuration tool for Synaptics touchpad driver of X server          
v   xfree86-driver-synaptics                                    -                                                                       
v   xorg-driver-synaptics                                       -                                                                       
p   xserver-xorg-input-synaptics                                - Synaptics TouchPad driver for X.Org server                            
p   xserver-xorg-input-synaptics-dev                            - Synaptics TouchPad driver for X.Org server (development headers)  
```

Then, I looked into the "mouse" configuration panel in Gnome, and it does not have any mention of a touchpad.  My xorg.conf file (which didn't exist, but I had one created) has no mention of synaptics or touchpads. It just has the one mouse input device.  lshal shows no mention of a touchpad:
```

# lshal | grep -i touchpad
# 

```

And yet, the touchpad still works!  Any pointers or ideas would be greatly appreciated at this time.  I will be happy to provide any other necessary details.  I posted everything I thought relevant.

edit: One more detail. Here is the output of 'xinput list'. It makes no mention of a touchpad.
```

$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Logitech Wheel Mouse             	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
...

```

---

### Post by tdennist on 2010-06-07
No ideas? This is still a problem for me.

---

### Post by roger_1960 on 2010-06-07
Hi

You could install, from synaptic, gpointing-device-settings, run it in terminal (and or create a launcher) and then set the tapping time as short as possible - this effectively turns it off on my laptop.

---

### Post by tdennist on 2010-06-07
Hello,

Thank you for your reply. Unfortunately, this does not seem to solve the problem for me. The only two entires in gpointing-device-settings are:

* Logitech USB Receiver
* ImPS/2 Logitech Wheel Mouse

I have a Logitech wireless mouse (with wheel), which is what I use exclusively. So, for a temporary hack I would even be happy with simply disabling the touchpad completely. However, the touchpad isn't showing up *anywhere*, as I detailed in my first post.

Still stuck on this. :-/

---

### Post by roger_1960 on 2010-06-07
Mmmm..  does 
> sudo lshw
give any mention of a touchpad?  Just to try and find out what type it is.

---

### Post by Arminho on 2010-06-18
> **tdennist said:**
> Hello,

Thank you for your reply. Unfortunately, this does not seem to solve the problem for me. The only two entires in gpointing-device-settings are:

* Logitech USB Receiver
* ImPS/2 Logitech Wheel Mouse

I have a Logitech wireless mouse (with wheel), which is what I use exclusively. So, for a temporary hack I would even be happy with simply disabling the touchpad completely. However, the touchpad isn't showing up *anywhere*, as I detailed in my first post.

Still stuck on this. :-/

I had a similar problem with my ASUS K50AF. Although I haven't found a clean fix, here's the workaround that I'm currently using:
My touchpad doesn't use the "synaptics"-driver, but "evdev". The touchpad in my case is "ImPS/2 Logitech Wheel Mouse" 
In order to catch this device I created a new .conf file in directory /usr/lib/X11/xorg.conf.d/ (e.g. "50-touchpad.conf"). It is important that the filename starts with a higher number than all other files in the directory (X11 processes the rules-files in lexicographical order and resolves conflicts by overwriting). In my case the content of the file is:

```
Section "InputClass"
	Identifier "disable touchpad click"
	MatchProduct	"ImPS/2 Logitech Wheel Mouse"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
	Option "ButtonMapping" "0"
EndSection

```

In your case the Device-name for clause "MatchProduct" could be different. You can list your Input-Devices with ```
xinput list
``` 

```
Option "ButtonMapping" "0"
``` disables the left mouse click (both, tapping and the button). This makes the mousepad pretty difficult to use...although it can still be used for right-click and to move the pointer. Since I'm not using the touchpad this workaround is fine for me - the touchpad doesn't mess around while typing anymore. I would be very interested if you find a better configuration of evdev (more info: ```
man evdev
```) to selectively configure tapping...

After saving the .conf-file you need to log-out and log-in (restart the X11-server) to enable the new settings.

---

### Post by vanadium on 2010-07-15
I am having the same problem with the same touchpad. The fix above makes the touchpad essentially useless. Are there other options or is this really exotic hardware?

---

