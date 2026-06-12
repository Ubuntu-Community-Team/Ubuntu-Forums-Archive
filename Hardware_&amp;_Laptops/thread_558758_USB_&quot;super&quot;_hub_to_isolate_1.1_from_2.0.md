---
title: "USB &quot;super&quot; hub to isolate 1.1 from 2.0?"
date: 2007-09-24
forum: Hardware &amp; Laptops
---

### Post by miamicanes on 2007-09-24
Is there such a thing as a USB hub that segregates USB1.1 devices from the 2.0 ones and makes them appear to be USB2.0 devices to the root hub itself (buffering their slow 1.1 output, then relaying it onward at 2.0 speeds, buffering their fast 2.0 input and relaying it onward to the slow device at 1.1 speeds)?

The reason I ask is because I'm trying to move as many peripherals as I can to USB to reduce the number of cables I have to connect and unplug whenever I move my laptop. The problem is, Dell put both of the laptop's USB ports on the same root hub, and one of the things I MUST connect is a USB1.1 mouse/keyboard adapter that CAN NOT be replaced -- it's one of the very, very few known to work reliably with Lexmark Model M13 keyboards (the ones with buckling-spring keys and built-in Trackpoint mouse; they draw more power than most cheap PS2->USB converters can supply). So what I'm hoping is that someone makes a USB hub that can logically isolate it from the rest of the devices connected to the port (all 2.0) so it won't drag down their performance.

update -- apparently, what I'm referring to is a USB 2.0 hub with "transaction translator" -- something that's part of the spec, but most 2.0 hubs don't actually implement because it increases the cost & most people don't know the difference anyway; even worse, quite a few apparently LIE about it when queried by the root hub, or don't implement it properly... so I guess a revised question would be, "Does anybody know of any specific USB 2.0 hubs with fully-implemented transaction translator?"

---

