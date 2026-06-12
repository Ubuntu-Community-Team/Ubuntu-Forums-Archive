---
title: "madcatz wireless ps3 game pad (debian /ubuntu)"
date: 2008-10-28
forum: Hardware
---

### Post by teaker1s on 2008-10-28
Can anyone suggest how I proceed with a wireless game pad,
it has wireless that appears to debian as wired.


So far I am at the point of seeing it in jscalibrator.
 I have a ./joystick file in my home directory, but no joy with using it in games.
does it need to be put into xorg.conf or elsewhere as both kde joystick config and in gnome it won't work.
xorg.conf so far

Section "InputDevice"
Identifier "Gamepad"
Driver "joystick"
Option "Device" "/dev/input/js0"
EndSection


dmesg
usbcore: registered new interface driver hiddev
[ 2414.244936] input: Sony PLAYSTATION(R)3 Controller as /class/input/input11
[ 2414.269137] input,hiddev96,hidraw0: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:0b.0-6
[ 2414.269170] usbcore: registered new interface driver usbhid
[ 2414.269174] usbhid: v2.6:USB HID core driver


```
jstest /dev/input/js0
```
seems to give all the output needed to fully configure it along with jscalibrator any ideas please. furthest I have got is pad locked down as per bug here and unusable 
[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg578882.html]("http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg578882.html")

---

