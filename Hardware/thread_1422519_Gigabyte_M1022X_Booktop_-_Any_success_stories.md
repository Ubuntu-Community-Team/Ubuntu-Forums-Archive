---
title: "Gigabyte M1022X Booktop - Any success stories?"
date: 2010-03-05
forum: Hardware
---

### Post by jacovt on 2010-03-05
Hi guys,

Bought a Gigabyte M1022X Booktop netbook today. Had some trouble installing UNR on it.

Turns out the touchpad is not working at all. This is a multitouch touchpad. Funny enough, the USB mouse I plugged in does not seem to work either. *shrug*

I have yet to try install the latest 10.04 Alpha versions to see if any progress have been made, will get round to that later tonight.

Meanwhile, has anyone here had any success installing Ubuntu on this model?

Also, what is the best way report the hardware specs as to get them supported?

For those interested, here is the hardware breakdown:

Model: Gigabyte M1022 series (M1022X)
CPU: Intel Atom N280 1.66GHz (512Kb, 667MHz)
Chipset: Mobile Intel 945GSE Express
RAM: 2GB DDR2
HDD: SATA 250GB
Communiations: 802.11b/g/n, 10/100 Ethernet, Bluetooth: 2.1 + EDR
LCD: 10.1" TFT-LCD with LED backlight
Input: Touchpad, Keyboard
IO Ports: 3xUSB, Mic-in, Earphone-out, D-SUB, 1xRJ45, 4-in-1 Card reader, 1xExpress card
Docking: Yes


---Jaco

---

### Post by timjohn7 on 2010-03-24
I have bought the same netbook, and eagerly await a response so I can decide how to approach this issue.
Jaco, where are you located and how much RAM did you get in your Booktop?

---

### Post by timjohn7 on 2010-03-25
Jaco, Have you looked at jolicloud ([www.jolicloud.com)?](www.jolicloud.com)?)

They state that the 1022X is compatible and I may give it a try in the near future.  My machine was delivered with only 1Gb RAM although the box stated 2Gb so I may have to return it, so I don't want to make too many changes yet.

---

### Post by timjohn7 on 2010-03-30
Just an update to confirm that I have exactly the same problem as posted by jacovt.

Touchpad not functioning at all in Karmic NBR or full version.

I have reported this to [www.elan.com.tw](www.elan.com.tw) (manufacturers of the touchpad), but am not holding my breath waiting for a reply.  They have patented the touchpad and I'm pessimistic that they will provide code for Linux support.

---

### Post by morered on 2010-04-15
This fixed the touchpad on a Gigabyte M1022C:

[http://ubuntuforums.org/showthread.php?t=1275975](http://ubuntuforums.org/showthread.php?t=1275975)


Internal mic not working, any ideas?

---

### Post by timjohn7 on 2010-04-21
I'm currently running Lucid Beta 2 NBR  Live CD and the Elan Touchpad works!  Including multitouch!
Wireless and sound are fine, but the webcam is not detected.

This looks VERY good!

Addendum to this post...

After full install of Lucid Lynx Beta2 NBR, EVERYTHING JUST WORKS!  That includes webcam (in Cheese; I haven't set up Skype yet).  I'm currently dual booting Windows 7 and NBR 10.04, and will probably stay that way for some time, but what a great discovery to find the Touchpad working!

I consider this to be a 99% success story!

---

### Post by bar-end on 2010-06-22
I've   used  power   ISO   to   make   an   image   of  Ubunt   Jaunty   and   then   mounted   the  image.   I've   installed   it   inside   windows,  rebooted   and   everything   went   fine.   

Also  got   the  touchpad   problem   but   the   external    mouse works   perfectly.

---

### Post by BenjaminChile on 2010-06-27
Hey there, I think you should try with new Ubuntu 10.04 LTs Lucid Lynx, download this ISO image and try it out a boot with a USB stick (as I did last week here in Chile). Or use an external CD/DVD writer/reader disk connected to a usb switch in you netbook. It works out fine with this Ubuntu version. You can also continue using windows xp and add the WUBI virtual directory file for Ubuntu  as a second choice, for sure.

---

