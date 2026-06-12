---
title: "HP Laserjet alignment issue"
date: 2013-08-11
forum: Hardware
---

### Post by crashed111 on 2013-08-11
Hi all

I currently have a HP Laserjet 2600n hooked up with Jetdirect to my Ubuntu machines. 

Recently I have noticed that the alignment of the black and colour has been out which has introduced "ghosting" on some of my print outs. I recently reset the NVRAM 4 times which fixed this issue (I believe when you do this the printer does a full recalibration). However about 2 days later the issue come straight back and I was able to fix it by resetting the NVRAM. 

Does anyone know what's causing this? Is it the printer or should I buy a new set of toner. I don't want to buy a new set of toner if it is an issue with the printer itself

Thanks in advance.

---

### Post by bsamim on 2013-08-11
What driver are you using?

---

### Post by tgalati4 on 2013-08-11
There might be a button battery that has gone bad that keeps the NVRAM settings alive.  If you have a power dropout, then it's possible you will lose your calibration settings.  You can usually see the settings by printing out a settings page from the front panel.  Run an alignment cycle, print out the settings page and note the values.  Unplug the printer and reprint the page and see if the settings go back to 0.  If the settings are not being saved while the printer is unplugged, then take the printer apart and locate and test the button battery.

If the battery checks out OK, then it's possible that your printer's motherboard has developed a fault--look for leaky or bulging capacitors.

---

### Post by crashed111 on 2013-08-11
[COLOR=#000000]tgalati4 - Thanks for the advice, I will test it tomorrow. Hopefully it is the battery otherwise looks like I will be on the eBay market for a new printer!

[/COLOR][COLOR=#000000]bsamim - I am using the stock driver which is automatically detected by Ubuntu. I see the same issues when printing a demo page from within the printer menu itself so I believe this is not a driver issue [/COLOR]

---

