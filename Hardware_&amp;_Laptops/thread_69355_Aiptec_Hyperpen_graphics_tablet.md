---
title: "Aiptec Hyperpen graphics tablet"
date: 2005-09-26
forum: Hardware &amp; Laptops
---

### Post by JulesH on 2005-09-26
Hi,

Has anyone come across a Linux (Ubuntu) driver for an Aiptec Hyperpen 6000 graphics tablet? I have the serial port version, NOT the USB version.

If not, is there any way to experiment with getting it working?

Regards,
Jules

---

### Post by Bakerconspiracy on 2007-03-18
I have one of these tablets also, and I would like to get it working aswell. There seems to be no hope in the future though because aiptec didn't hit it big like wacom.

---

### Post by FuzzyUnicorn on 2007-04-07
I have the serial (not USB) version of this tablet too. The driver is in the repos. It's called xserver-xorg-input-hyperpen. After installing it, you will have to edit your xorg.conf. Add a section that says:
```
Section "InputDevice"
    Identifier "pen"
    Driver     "hyperpen"
    Option     "Device"         "/dev/ttyS0"
    Option "Mode" "absolute"
    Option "Cursor" "Stylus"
    Option "SendCoreEvents"
    Option "XSize" "600"
    Option "YSize" "450"
    Option "AlwaysCore"
    Option "BaudRate" "19200"
    Option "PMin" "62" 
    Option "PMax" "511"
 EndSection
```
Then in your "ServerLayout" section add:
```
InputDevice	"pen" "SendCoreEvents"
```
When you restart X, your pen should work.  A quick/dirty way to restart X is to hit <ctrl><alt><backspace>

---

### Post by SpikeyB on 2007-04-22
FuzzyUnicorn

I don't know if you are a girl or a boy but I don't care, I love you.

My hyperpen was the only bit of hardware I couldn't get to work and now it does.

Thank you very much.

---

### Post by space_man619 on 2007-12-15
Thanks FuzzyUnicorn!
My tablet works great now!
Is there a way to configure things e.g. buttons on the pen?

---

