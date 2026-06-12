---
title: "USB ports on Thinkpad Dock 2 - with X30 laptop"
date: 2007-04-13
forum: Hardware &amp; Laptops
---

### Post by murius on 2007-04-13
Hi,

I recently installed Edgy on an IBM Thinkpad X30. USB ports on laptop are fine but the ones in the Docking station do not work, they do not even provide power (they do work when booting under Windows XP). Everything else on the Docking station works (DVD, Sound, Networking, PS2 port, etc)

My docking station is a Thinkpad Dock2:
[http://www.thinkwiki.org/wiki/ThinkPad_Dock_II#IBM_ThinkPad_Dock_II](http://www.thinkwiki.org/wiki/ThinkPad_Dock_II#IBM_ThinkPad_Dock_II)

There are 2 USB ports on the docking station and 2 on the laptop.
When I type the command 'lsusb' I get the following output:
~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
(This is with USB devices connected on docking station ports)

If I plug in a mouse on the laptop USB port then 'lusb' gives the following:
~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 008: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

Any ideas how to get the USB on the docking station working? Thanks in advance everybody.


- Murat.

---

