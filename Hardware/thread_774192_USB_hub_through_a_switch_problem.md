---
title: "USB hub through a switch problem"
date: 2008-04-29
forum: Hardware
---

### Post by Shades404 on 2008-04-29
Hi, I am having some problems connecting a usb hub to my laptop through a usb switch. My system setup is that I want to share a number of usb peripheral (mouse, keyboard and webcam for example) between two computers. (thankfully my monitor has dvi and avi inputs so can take both inputs and switch itself)

To solve this I have an old Belkin peripheral switch to switch one device between up to four machines. Into this I plugged a hub, this works fine on my desktop which is a windows xp machine, but doesn't register at all on my Ubuntu laptop.

The switch never shows up in lsusb and so I am assuming it's just a switched connection. My mouse or keyboard show up as normal when connected through it, however the hub I have only shows up when connected directly to the laptop and not via the switch

Connected directly it shows up as:
> Bus 007 Device 009: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub

The only other thing I can think of is that under windows xp it warns me that the hub is 2.0 and the switch is not and so won't run at usb 2 speeds. I'm not sure if this is relevant to the problem or not.

I've tried other hubs as well, and this one can be powered if needed, nothing seems to work. If anyone can offer a suggestion or pointer or even a solution that would be great :)

---

### Post by sjoseph on 2008-05-23
I am having similar probs. I have a Belkin USB Peripheral Switch and while I can get it working on XP, the driver can't load in Gutsy (I can load it w Crossover but that doesn't really do anything). I am trying to run a printer w 2 computers. Any thoughts.

---

### Post by bLaCkMeTaLL on 2008-10-29
Hello, I have a similar problem too...

I Have:
[LIST]
[*]multiport lcd display (dvi, vga)
[*]a windows pc connected through dvi
[*]an ubuntu laptop connected to vga
[*]an usb keyboard I wish to share between the two computers
[*][a belkin 2x1 usb switch]("http://catalog.belkin.com/IWCatProductPage.process?Product_Id=134172")
[/LIST]

The switch under windows doesn't present any problem (I use this pc for gaming), but under ubuntu isn't even recognized.

Can anybody help?

---

