---
title: "Lenovo Thinkpad X1 Carbon 3rd Gen"
date: 2016-04-17
forum: Hardware
---

### Post by grappler on 2016-04-17
I'm using a Lenovo X1 Carbon 3rd Gen running ubuntu. A couple of days ago I upgraded to Ubuntu 16.04 running Gnome as my desktop.
I normally disable the trackpad (why do they bother with that - it essentially makes the computer unusable) in the bios. At first everything worked fine but after I did a subsequent 
"sudo apt-get dist-upgrade"  the trackpad started working - though still disabled in the bios. There seems to be no way to disable it, either  in the bios or in the gnome extension that supposedly handles mouse and touchpad config.

The only way I have found to turn it off is to modify /usr/share/X11/xorg.conf.d/50-synaptics.conf by replacing   the line MatchIsTouchpad "on" to "MatchIsTouchpad "off" in Section "inputClass". 
Unfortunately this also turned off the trackpoint and the computer is unusable.  


Is there a way to modify the config file to allow trackpoint to work without touchpad.  Sorry if this is the wrong topic but not sure whether this is a hardware or a software issue.

Thanks.

---

### Post by grappler on 2016-04-17
> **grappler said:**
> I'm using a Lenovo X1 Carbon 3rd Gen running ubuntu. A couple of days ago I upgraded to Ubuntu 16.04 running Gnome as my desktop.
I normally disable the trackpad (why do they bother with that - it essentially makes the computer unusable) in the bios. At first everything worked fine but after I did a subsequent 
"sudo apt-get dist-upgrade"  the trackpad started working - though still disabled in the bios. There seems to be no way to disable it, either  in the bios or in the gnome extension that supposedly handles mouse and touchpad config.

The only way I have found to turn it off is to modify /usr/share/X11/xorg.conf.d/50-synaptics.conf by replacing   the line MatchIsTouchpad "on" to "MatchIsTouchpad "off" in Section "inputClass". 
Unfortunately this also turned off the trackpoint and the computer is unusable.  


Is there a way to modify the config file to allow trackpoint to work without touchpad.  Sorry if this is the wrong topic but not sure whether this is a hardware or a software issue.

Thanks.


I have found a workaround. First I typed 

xinput list 

on the command line to find the touchpad device id. 

It came up as SynPS/2 Synaptics TouchPad id=11 

Then I put the following in startup applications - having first checked that it worked on the command line:

/usr/bin/xinput set-prop <device-id> "Device Enabled" 0

where in my case <device-id> was 11. 

The touchpad still works on the login screen but after that it stops, but the trackpoint continues to work. Yes!  But I would like to know why the bios disable does not work any more.

---

### Post by kurt18947 on 2016-04-17
There is a way to enable/disable a touchpad in Ubuntu-gnome without editing files. Click on the 'power button' in the upper right corner of the top panel then select the icon that looks like a wrench & screwdriver.  Mouse & touchpad should be one of the choices. There is a nice 'off' button for the trackpad on 16.04. It IS curious why the BIOS setting was overridden though.

---

### Post by grappler on 2016-04-17
Thanks kurt but I tried that  and it had no effect on the touchpad - it continued to work even when the switch was set to off.  I've used that before and it worked but not this time.

---

