---
title: "Unusual touchpad problem."
date: 2009-07-28
forum: Hardware
---

### Post by Marblemouth on 2009-07-28
I've been searching the forums and googling this problem from every angle I can thnk of.  My touchpad stopped working for no apparent reason.  It was working this morning just fine.  I turned off the laptop, and turned it back on five hours later with the touchpad failing.  The pad itself is unresponsive along with the left, right and center buttons underneath the pad.  I have tried: System - Preferences - Mouse - Touchpad... it said the touchpad was enabled.  I have also tried: System - Preferences - Touchad... it said "GSynaptics couldn't initialize.  You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"  I spent several hours today trying to make the above happen with poor results.  Here is what my current xorg.conf reads as: 
 Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

As a guese, I'm missing alot of information in that file.  

When I enter this:
Section "InputDevice"
 Identifier "Synaptics Touchpad"
 Driver "synaptics"
 Option "SendCoreEvents" "true"
 Option "Device" "/dev/psaux"
 Option "Protocol" "auto-dev"
 Option "HorizEdgeScroll" "0"
 Option "SHMConfig" "true"
 Option "CorePointer"
EndSection

... I get graphical errors on reboot to go along with the other issues I'm having.  Does anybody have any suggestions as to whatelse I can try?
Thanks!

---

### Post by FlyingBuzz on 2009-07-28
Hello! I know that enabling SHMConfig is not so trivial =) I did it before, so I can quickly find the solution.
I Think that it's not why your touchpad doesn't respond but maybe.. Who knows. Try this:
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by Marblemouth on 2009-07-28
I came across that page earlier and had tried everything on it.  It did not help at all.  I'm pretty sure when I entered this: 
gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi

and added this:

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">True</merge>
    </match>
  </device>
</deviceinfo>

it caused my graphical errors.  

thanks anyways

---

### Post by ZaHACKieL on 2009-07-28
Have you tried the touchpad in Windows or another OS? Just to be sure is not a hardware problem

ZL

---

### Post by Marblemouth on 2009-08-02
I can't try it in Windows... I'm using a beat up laptop that does not have Windows anymore.  I have tried previous versions of Ubuntu and it worked fine in those installations.  The big problem I'm having here is that the touchpad works perfectly until I shut down the laptop.  Upon turning it back on, I have a dead touchpad.

Also, as an update.  I have since reinstalled 9.04.  The touchpad worked without any problems until I shut down the laptop.  Upon restarting the machine, the laptop tab in the mouse applet had disappeared and the touchpad is dead.

---

### Post by measekite on 2009-08-02
> **Marblemouth said:**
> I've been searching the forums and googling this problem from every angle I can thnk of.  My touchpad stopped working for no apparent reason.  It was working this morning just fine.  I turned off the laptop, and turned it back on five hours later with the touchpad failing.  The pad itself is unresponsive along with the left, right and center buttons underneath the pad.  I have tried: System - Preferences - Mouse - Touchpad... it said the touchpad was enabled.  I have also tried: System - Preferences - Touchad... it said "GSynaptics couldn't initialize.  You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"  I spent several hours today trying to make the above happen with poor results.  Here is what my current xorg.conf reads as: 
 Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

As a guese, I'm missing alot of information in that file.  

When I enter this:
Section "InputDevice"
 Identifier "Synaptics Touchpad"
 Driver "synaptics"
 Option "SendCoreEvents" "true"
 Option "Device" "/dev/psaux"
 Option "Protocol" "auto-dev"
 Option "HorizEdgeScroll" "0"
 Option "SHMConfig" "true"
 Option "CorePointer"
EndSection

... I get graphical errors on reboot to go along with the other issues I'm having.  Does anybody have any suggestions as to whatelse I can try?
Thanks!

I am using an Adesso USB SmartCat Touchpad with no Linux driver and it works fine.  It just does not have the horizontal scroll driver.

First I recommend that you find out if your Touchpad is damaged or broken in some way.  Here is how to do that.

Download Ubuntu Jaunty 9.04 Live CD and test your Touchpad.

If it does not work then "Game Over".  It is not worth fixing an old Laptop but you could get a cheap USB Touchpad from Amazon for about $30.00 and a SmartCat for $55.00 shipped to your door.

If it works then I would backup your data, reformat your drive and do a clean install of Ubuntu 9.04.

Give us a post if this works.

---

### Post by housty on 2009-11-04
I have the same problems with three different laptops and they all worked with 9.04.. I've a compaq an HP nx9500 and a Dell.

This is extremely annoying.. that only get's more annoying when others tell you it must be your touchpad!


If you install 9.10 the touchpad might work the first time you use it but after reboot its dead!

---

### Post by harrisdg on 2009-11-27
I'm having a similar problem, but not of the same magnitude.  I want to adjust my touchpad settings, but don't have access to the touchpad utility at all.  My xorg.conf file looks like this: 

[FONT=Courier New]Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection[/FONT]

Can a section just be added in?

---

