---
title: "Ubuntu 18.10 Touchpad on Geo Book3 laptop"
date: 2018-12-20
forum: Hardware
---

### Post by diddy1234 on 2018-12-20
Hi there

I recently  purchased a cheap laptop (Geo Book3) and I intended to get rid of windows 10 and replace it with Linux.
I have tried searching the web but the laptop  is so new, no one is using this laptop with linux.

After trying several variants of Linux, Ubuntu 18.10 seems to work the best  (I suspect because the laptop has been on sale less than 6 months).

There are two issues that I have :-

1. The touchpad  only  works  in Ubuntu 18.10 and not at all in 18.04.
But its the movement  that is the problem.
In windows the whole trackpad allows the mouse movement over the whole desktop  but in ubuntu I have to swipe several times to get  the mouse to move  across the whole desktop. No acceleration ?
Also the touch to select has to be turned off as its too sensitive. if i touch the touchpad to move the mouse,  it selects as well

2. I cannot  install to the onboard system 32GB  eMMC. Ubuntu does not see this  device, How can I get it to see this ?

Issue  number 2 can be worked  around  with  a  mountable hard drive or even to a ssd card.

Should  I stick with windows for now and wait until an updated version of linux appears ? 

The specs of the laptop are :-
Processor	- Intel® Celeron® N4000 Processor- Dual-core - 1.10 GHz / 2.60 GHz
RAM	4 GB LPDDR4
Storage	32 GB eMMC
Touchscreen	No
Screen size	13.3"
Screen type	IPS LCD
Resolution	Full HD 1920 x 1080p
WiFi	- AC WiFi - 1x1 - Up to 433 Mbps
Bluetooth	Bluetooth 4.2
USB	USB 3.0 x 2
 HDMI x 1

Windows shows the touchpad is a I2c compliant HID device using a standard windows driver
Windows also shows the storage as Common Biwin device


Any answers would be greatly appreciated.

---

### Post by diddy1234 on 2018-12-28
For anyone  who wants to use Linux on one of these laptops, it can be done but dual booting with windows doesnt work too well.

the best option (gamble on my part) was replacing windows 10 with Ubuntu 18.10 (mouse support works in this version).
in the bios (accessed by the delete key during turning on) I had to turn off trusted computing in order to see the built in 32GB storage and in the southbridge bios settings set Linux instead of windows. then Linux installs.
I did have to play with the touchpad settings (turning off touch to select) as the mouse is too sensitive.
However,  In ubuntu I installed Cinnamon desktop  and there are extra settings for touchpad sensitivity and acceleration.once these were set, the laptop became very useful.
also the ability to set a max audio output in the amplified region allowed the sound card and built in speakers to be alot louder (this laptop has small downward firing speakers). the extra volume improves this quite a bit.

so the laptop is a terrible windows laptop but a very good  linux laptop

---

### Post by istephen2 on 2019-03-15
Could you give me a quick guide on how to get Ubuntu working on this laptop?I can't seem to figure it out :(

---

### Post by diddy1234 on 2019-03-18
I found the Ubuntu version 18.04 lts didnt work as it didnt have touchpad drivers (or not configured) so I tried 18.10 and the drivers worked out of the box.

I did have to configure the touchpad though.
I turned off the touch to select feature and then changed the sensitivity and acceleration and now it works fine

---

### Post by istephen2 on 2019-03-18
I can get the mouse to move but only if I keep the touch pad clicked in. Any ideas?

---

### Post by diddy1234 on 2019-04-15
Sounds like a configuration issue. could you plug in a USB? mouse and see what you get ?
if this works fine, then there is some setting for the trackpad you would need to look into

hope it helps

---

### Post by urowietu on 2019-07-05
Hi I am into python

So I tried to install Ubuntu 19.04 into my new GeoBook1 and it always hanged on a black screen after usb boot. Changed all the boot priority stuff etc. I think the community has just not written drivers yet. 

I just accepted it and started to use the windows subsystem for Linux out of MSDOS to learn to do bash scripts and installed my jupyter-notebook through bash terminal. Tomorrow I’m going to a charity shop to buy an old dell with a dvd reader and I am going to dvd-install Ubuntu 19.04 from a dvd off Linux magazine. Live and learn. Someday my geobook will become obsolete enough to have drivers for Ubuntu. It’s all good.

---

### Post by hoohaw on 2019-10-25
FYI, touchpad now works well with the latest 5.0.0.31 kernel on 18.04.3

---

### Post by uRock on 2019-10-25
This thread is old and 18.10 is obsolete.

Thread Closed

---

