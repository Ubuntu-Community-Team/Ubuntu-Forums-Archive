---
title: "SOME USB Ports Acting Strangely?"
date: 2008-09-29
forum: Hardware
---

### Post by SleepingProphet on 2008-09-29
This is kindof a strange issue, and I've been Googling for hours unsuccessfully.

I recently built a new HTPC using a Shuttle barebones as a start point. I am dual-booting between Windows Vista and Ubuntu Hardy x64. The Shuttle box I've got has a total of 6 USB ports built in, with the rest only available as headers on the motherboard.

This is the Shuttle I'm using:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856101034](http://www.newegg.com/Product/Product.aspx?Item=N82E16856101034)

The South Bridge (which runs the USB) is the relatively recent ICH9DH, so its not like this is some sort of old janky "Oh man USB 2.0 is still new" sort of chipset. Under Windows I have tested ALL the USB ports and they all behave as expected.

Under Ubuntu, 4 of the ports work as normal.
2 ports are basically unusable. When plugging a USB mouse into one of these "unusable" ports, the mouse DOES get electrical power and lights up, but its not showing up if I do an lsusb command in terminal. I'm a tech support guy for Windows stuff by trade, but I'm very new at linux and so if there's some "obvious" command to run, sorry if I missed it. When running lsusb with nothing plugged into the "messed up" ports the results return immediately. With anything plugged in, there's a pause of a few seconds before the list comes up.

Does this help? Anyone know why this might happen and/or how to fix it?

Most of the info I was finding via Google indicated this was some sort of issue with IRQs and / or EHCI, and most of the time the advice given was "update your kernel". 
My kernel is reported as 2.6.24-19-generic by running uname -r, and I do see there's a slightly newer stable kernel out there, so I may try to update that if I can figure out how.

I'd really like to get this USB stuff resolved so I can finalize the way I do the wiring and fully dress cables and stuff.

---

### Post by SleepingProphet on 2008-10-01
nobody? :(

---

