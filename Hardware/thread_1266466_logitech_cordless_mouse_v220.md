---
title: "logitech cordless mouse v220"
date: 2009-09-14
forum: Hardware
---

### Post by beegie on 2009-09-14
**Re: Logitech Cordless Mini Optical Mouse doesn't work at all**             
                                                                evilteddy,

EDIT: Make sure you have the evdev driver.
     Code:
     sudo apt-get install xserver-xorg-input-evdev 
Make a backup of you xorg.conf and get the device info
     Code:
     cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
cat /proc/bus/input/devices 
Then use the following block of code in xorg.conf, but fill in the Dev Name and Dev Phys with the info you got from the cat command:
     Code:
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
Then put the following line in the ServerLayout section:
     Code:
     InputDevice "Logitech V220" 
Save and reboot.

this was posted by [Temüjin]("http://ubuntuforums.org/member.php?u=327594") and i have this problem but i dont know what he means by "Then put the following line in the ServerLayout section:" i followed all the instruction, but this one and whe i attempt to save it says permission denied

---

### Post by beegie on 2009-09-14
bump

---

### Post by peculiar penguin on 2009-09-25
I'm running Jaunty and this mouse worked out of the box for me (except for the tilt wheel buttons, see below on how to set up those), so I'm not sure what's wrong if it doesn't work at all for you.

Also unless you're using an older version, modifying xorg.conf won't work any more. I think the X.org server ignores that file and talks to HAL these days.



=====

Enabling the tilt wheel buttons of a "Logitech V220 Cordless Optical Mouse for Notebooks" on Ubuntu 9.04 (Jaunty Jackalope):

Open a terminal and do a
```
cat /proc/bus/input/devices
```Go through the output and find the device that corresponds to the mouse - the "Name" entry should say "Logitech USB Receiver" (if it doesn't you'll have to change the name in the XML snippet below).

Open a text editor with privileges
```
gksu gedit
```Copy and paste the following text:
```

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input">
      <match key="info.product" string="Logitech USB Receiver">
        <merge key="input.x11_driver" type="string">evdev</merge>
        <merge key="input.x11_options.Buttons" type="string">7</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```Save this as an .fdi file in the /etc/hal/fdi/policy directory (e.g. /etc/hal/fdi/policy/logitech_v220.fdi).

Reboot and the buttons should start working (System > Administration > Log File Viewer works as a first test, it should have both vertical and horizontal scroll bars if you make the window small enough).


In Firefox (firefox-3.5 aka Shiretoko) I really wanted to use the tilt buttons as back/forward buttons, not for horizontal scrolling. This can be done in about:config by changing the value of "mousewheel.horizscroll.withnokey.action" from 0 to 2. This resulted in left tilt = forward, right tilt = back. To invert this behaviour, set "mousewheel.horizscroll.withnokey.numlines" to -1 and "mousewheel.horizscroll.withnokey.sysnumlines" to false.

---

### Post by go2dell on 2009-10-16
Just wanted to report that in Kubuntu 9.04, this mouse works out of the box for me, including side scrolling with the tilt wheel.  KDE rocks!

Thanks to *peculiar penguin* for giving the steps to switch the tilt to forward/back in Firefox.  Everything is now perfect.

One note:  if the mouse doesn't work for you the first time, check your dmesg and try unplugging and replugging the USB receiver.  The first time I plugged it in, it wasn't completely recognized (just USB low speed device).  The second time, it was seen as a Logitech USB Receiver.

---

