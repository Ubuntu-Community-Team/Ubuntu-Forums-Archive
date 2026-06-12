---
title: "USB optical mouse not working"
date: 2005-12-11
forum: Hardware &amp; Laptops
---

### Post by tinkerbell on 2005-12-11
Hi,

I just installed Kubuntu 5.10 a few days ago on my desktop & Toshiba Satellite A45 laptop 3 days ago. Most things are working fine except for a weird problem that started just today on the laptop -- my USB optical mouse is not working, though the laptop touchpad works just fine. In fact, the red light at the bottom is flashing steadily like a turn signal, instead of being on all the time as it ought to be. The mouse is completely dead -- no movement detected, nothing. I checked the USB port by plugging in my flash drive; no problem. I checked the mouse on a friend's laptop; again, no problem. Tried it on all 4 of my USB ports, no luck.

Tried dmesg; the output I get is:

[4299091.418000] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[4299103.046000] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[4299132.169000] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[4299176.392000] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[4299178.552000] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?

When I try cat /dev/input/mice, there's no response whatsoever from the USB mouse, while the touchpad again works fine. This is all the more odd because the problem only started today -- as of yesterday, the mouse was working just fine, & I could use both mouse & touchpad together as I used to on Mandrake. 

Any clues as to what might be causing this would be greatly appreciated. Thanks in advance!

---

### Post by tinkerbell on 2005-12-12
I think I've figured out a workaround -- as long as the mouse is plugged in before I boot, it works fine. I can't plug it in during or after bootup & have it work. Any ideas why?

---

### Post by Sef on 2006-01-06
Sounds like there is a problem with the hotplug system.  If it doesn't work, then the devices will have to be plugged in when the computer boots up.

---

### Post by ikram ullah on 2006-01-06
I am a lecturer of  University.I am Pakistan therefore a need your support and i am living in Peshawar.
                      My address is "pakistan/N.W.F.P/Hayat abad Peshawar/ph3/
                                      seck-2/st16/ho456

---

