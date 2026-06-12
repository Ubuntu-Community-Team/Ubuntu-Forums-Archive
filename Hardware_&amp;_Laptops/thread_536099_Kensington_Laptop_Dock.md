---
title: "Kensington Laptop Dock"
date: 2007-08-27
forum: Hardware &amp; Laptops
---

### Post by (-NINJ4-) on 2007-08-27
I recently installed Ubuntu Feisty on my Dell Inspiron 6400 laptop, and after installation, I decided to see if my [Kensington Laptop Dock with Video]("http://us.kensington.com/html/11196.html").  After searching the forums, I discovered how to make the audio portion of the device work, and the ethernet connection worked out of the box.  I really now only want two things out of this dock: Video and its USB ports.  Other threads about this dock have not come up with any solutions to the video problem, but I haven't yet seen anyone who is having an issue with the USB hub portion of the dock.

if I go into a terminal and type "lsusb" I get the following:
Bus 005 Device 006: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 005 Device 008: ID 1058:0702 Western Digital Technologies, Inc. 
Bus 005 Device 007: ID 0409:005a NEC Corp. 
Bus 005 Device 004: ID 0b95:7720 ASIX Electronics Corp. 
Bus 005 Device 002: ID 0409:005a NEC Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 004 Device 001: ID 0000:0000  

the WD Passport listed under Bus005, Device008 is plugged into my dock, so it can detect the ports there, they just don't show up under the computer in file browser.  Is there any way I can fix either of these two issues?

TIA

---

