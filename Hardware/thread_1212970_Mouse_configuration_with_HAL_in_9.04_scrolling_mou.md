---
title: "Mouse configuration with HAL in 9.04 scrolling mousewheel"
date: 2009-07-14
forum: Hardware
---

### Post by PuckstopperGA on 2009-07-14
Hi,

I'm having issues with my mouse in 9.04. When I boot, the mouse wheel scrolls horizontally when I'm trying to make it scroll vertically, and it scrolls vertically when I try to scroll horizontally. When I run xinput and swap the button assignments, it fixes it. But I have to run this command at every bootup or else it won't work correctly. One note, in xinput I have to use the device ID and not the name as my USB dongle and mouse (bluetooth) are called the same thing.. I've tried creating a mouse-wheel.fdi policy file, swapped the buttons, and assigned the X & Z axes (although I'm not sure I have that right), but whatever changes I make to the fdi file seem to be ignored by ubuntu. I've tried naming the device in the fdi file and using its ID, but neither seem to work. Any tips out there?

Here's my mouse-wheel.fdi file:

[INDENT]<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" string="2">
      <merge key="input.x11_options.Buttons" type="string">7</merge>
      <merge key="input.x11_options.ButtonMapping" type="string">1 2 3 6 7 4 5 8 9</merge>
      <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
      <merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
      <merge key="input.x11_options.EmulateWheelTimeout" type="string">300</merge>
<merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
      <merge key="input.x11_options.ZAxisMapping" type="string">4 5</merge>
      <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
    </match>
  </device>
</deviceinfo>[/INDENT]

---

### Post by PuckstopperGA on 2009-07-14
BTW this is the command I'm using at startup to make it work right:

```
xinput set-button-map 6 1 2 3 6 7 4 5 8 9
```

---

### Post by PuckstopperGA on 2009-07-15
Bump..

---

### Post by PuckstopperGA on 2009-07-17
Bump... Doesn't someone know about HAL configuration? Can't even find that many how-to's...

---

### Post by PuckstopperGA on 2009-07-20
bump...

---

### Post by limit223 on 2009-07-20
I had a very good tutorial to configure options in /etc/hal/fdi/policy/*my*.fdi for my Synaptics Touchpad here:
[http://wiki.archlinux.org/index.php/Touchpad_Synaptics](http://wiki.archlinux.org/index.php/Touchpad_Synaptics)

 I guess is very imp to find how to define <match key="" contains="">
with:
cat /proc/bus/input/devices

then
<merge key="input.x11_driver" type="string">your driver</merge>

and then your merge keys options.

---

