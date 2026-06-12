---
title: "Razer products - 9.10 + 10.04"
date: 2010-09-19
forum: Hardware
---

### Post by Garandir on 2010-09-19
I really would prefer to use Ubuntu over Windows.
One issue: No support for Razer products. I have already tried the RazerCopperHeadMouse tool, it did not work.
What basically happens to me is this: Boot up fine, log in fine. Roughly 5 - 10 minutes into usage, keyboard freezes up. If I unplug it and plug it back in, it lights up for a second and goes off. Keyboard is a Lycosa. The mouse will do the same thing about a minute later, it's a Diamondback 3G. I've been on Razer support with no help at all. They work perfectly fine on Windows.

---

### Post by Garandir on 2010-09-20
Bump before I go to school, hopefully I'll get a reply when I come back.

---

### Post by Garandir on 2010-09-20
Does anyone else even have this problem?

---

### Post by Garandir on 2010-09-21
Bump #3...

---

### Post by realzippy on 2010-09-21
Remember having problems with mouse plugged into a lycosa's USB slot.
Plug the mouse "directly" to the computer....any difference?

---

### Post by Garandir on 2010-09-22
> **realzippy said:**
> Remember having problems with mouse plugged into a lycosa's USB slot.
Plug the mouse "directly" to the computer....any difference?
It is/has been plugged directly into the computer. I have also tried virtually every combination of ports. Like I said, they work fine on Windows 7.

---

### Post by Garandir on 2010-09-23
Bump #4.

---

### Post by Garandir on 2010-09-24
Bump #5.

---

### Post by Garandir on 2010-09-24
Bump #6, could really use some help with this.

---

### Post by Garandir on 2010-09-25
Come on, really? 252 views, 9 replies when I post this, only one of the replies isn't mine.

---

### Post by realzippy on 2010-09-26
As mentioned,I used to have a Lycosa;no problem when not using the
built-in USB.Had a razer Biamondback,a razer Salmosa,no problems,but
this was in the days of 8.10...
Suggest to test different keyboard/mouse to see if problem persists,
it might be a YourMainboard/USB/kernel issue in general.Remember certain USB mouse problems in the forum;search for a clue/solution here and not specified to razer hardware.
BTW,at least for razer mice there is a linux driver that seems to work;helped a guy here to compile it days ago:
[http://ubuntuforums.org/showthread.php?t=1578998](http://ubuntuforums.org/showthread.php?t=1578998)

You could run an old Ubuntu LiveCd (e.g. 8.10);if it works,it is very likely a Kernel issue..
Another idea :
Check your xorg.conf file,which should only exist when using ATI or NVIDIA graphics driver.If there is a "mouse" and "keyboard" section,
you could try to disable or modify them;input devices are managed by HAL/KMS
in newer Linux OSs.

---

### Post by sloggerkhan on 2010-09-26
I have a razer copperhead mouse, no problems. Never used the razer config thing with it on 'buntu. Set it a button/profile setup I liked when I got it and still had a windows install about 5.5 years ago. Still use, still no problems. Gets detected as a mouse + usb HID.

Never tried one of their keyboards.

---

### Post by realzippy on 2010-09-26
maybe you get a clue running:
```
lsusb
```
when mouse/keyboard are working fine,comparing to
```
lsusb
```
when not working.
(use a 2nd Non-USB keyboard to type then)

---

### Post by Garandir on 2010-09-26
> **realzippy said:**
> maybe you get a clue running:
```
lsusb
```when mouse/keyboard are working fine,comparing to
```
lsusb
```when not working.
(use a 2nd Non-USB keyboard to type then)
Unfortunately, I don't have one of the older keyboards.

I will, however, try an 8.10 ISO, a kernel problem never occurred to me.

---

