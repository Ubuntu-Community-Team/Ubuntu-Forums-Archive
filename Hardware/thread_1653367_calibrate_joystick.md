---
title: "calibrate joystick"
date: 2010-12-26
forum: Hardware
---

### Post by th1bill on 2010-12-26
Using "lsusb" I have the proper name and my research has led me to use jscal to get my Joystick to work.  As you can see there is a problem with my syntax, can anyone help?

> willis@home:~$ jscal --calibrate Saitek PLC Cyborg Graphite Stick
jscal: missing devicename
willis@home:~$ jscal Saitek PLC Cyborg Graphite Stick  --calibrate
jscal: missing devicename
willis@home:~$ 

---

### Post by grandpaken on 2010-12-28
> **th1bill said:**
> Using "lsusb" I have the proper name and my research has led me to use jscal to get my Joystick to work.  As you can see there is a problem with my syntax, can anyone help?

 Don't get the idea I'm an expert...but I figured out it's
jscal- -c /dev/input/js0

  It only worked when I input the full path to the joystick device -c js0 doesn't work.

---

