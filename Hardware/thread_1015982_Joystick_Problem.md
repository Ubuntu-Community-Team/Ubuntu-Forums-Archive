---
title: "Joystick Problem"
date: 2008-12-19
forum: Hardware
---

### Post by trot3911 on 2008-12-19
My joystick is a Logitech Chillstream. It seems to me that it becomes in conflict with my Microsoft Wireless Mouse and Keyboard.
They are both recognized by Ubuntu. The problem starts when I connect the Wireless Mouse and Keyboard. The Keyboard is recognized under /dev/input/js0 and the Logitech Chillstream under /dev/input/js1. So I cannot use my gamepad in many games because the games look for a Joystick under /dev/input/js0.
Is there a way to force Ubuntu to recognize the Logitech Chillstream under /dev/input/js0 and the Wireless Keyboard and Mouse under /dev/input/js1. I must also say that when the Wireless Keyboard and Mouse is not connected, the Logitech Chillstream is recognized under /dev/input/js0. so I can use it in games.
Thanks in advance for the answers.

---

### Post by achase79 on 2009-02-23
This may be a common problem for Microsoft Wireless Keyboard & Mouse users.  You may be able to create a .fdi file for HAL specifying your keyboard and mouse as a keyboard and mouse to remove it from js0.  I am not sure if that will work or not since I don't have the same keyboard.

run this (to gather information on your hardware):
```
sudo lshal > hal.txt
```
Then you can create this fdi file:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
<match key="info.product" contains="AAA">
<merge key="input.x11_driver" type="string">keyboard</merge>
</match>
<match key="info.product" contains="BBB">
<merge key="input.x11_driver" type="string">mouse</merge>
</match>
</device>
</deviceinfo>
```
with AAA being the "product name" of the keyboard and BBB being the "product name" of the mouse, both from the hal.txt you created earlier.

Then copy the fdi file to /etc/hal/fdi/policy/

---

### Post by achase79 on 2009-02-23
The only other way would be to unplug both.  Then plug in the joypad first, then the keyboard and mouse.

---

### Post by jppinto on 2009-06-08
> **achase79 said:**
> The only other way would be to unplug both.  Then plug in the joypad first, then the keyboard and mouse.

See this thread:

[http://ubuntuforums.org/showthread.php?p=7420542#post7420542](http://ubuntuforums.org/showthread.php?p=7420542#post7420542)

---

