---
title: "ieee1394 freeze the system"
date: 2004-12-19
forum: Hardware &amp; Laptops
---

### Post by prichards on 2004-12-19
I have a problem with a dv camera.
The ieee1394 is detected by hotplug, and the modules are loaded. the device isn't created, but i have solve it by doining myself.

The problem is that when i connect the camera, the system freeze, i don't know if there  is a whole system freeze or just X, (i also tried without X, and i can get any response from the keyboard, but the cursor still blinks), both mouse and keyboard are usb.

As soon as i unplug the cable or turn off the camera, the system get back to normal. there isn't any extrange on the log files, any ideas?

there is a motherboard with an nforce2 chipset (abit nf7)

Thanx in advace

BTW, I'm using the latest hoary

---

### Post by lompolo on 2005-09-20
[QUOTE=prichards]I have a problem with a dv camera.
The ieee1394 is detected by hotplug, and the modules are loaded. the device isn't created, but i have solve it by doining myself.

The problem is that when i connect the camera, the system freeze, i don't know if there  is a whole system freeze or just X, (i also tried without X, and i can get any response from the keyboard, but the cursor still blinks), both mouse and keyboard are usb.

As soon as i unplug the cable or turn off the camera, the system get back to normal. there isn't any extrange on the log files, any ideas?

there is a motherboard with an nforce2 chipset (abit nf7)

Thanx in advace

BTW, I'm using the latest hoary[/QUOTE]
 try dmesg in terminal. 
I get Error parsing configrom for node 0-00:1023
ieee1394: Error parsing configrom for node 0-01:1023
ieee1394: The root node is not cycle master capable; selecting a new root node and resetting..

I think problem is with abit motherboard. I have abit as8. I tried with my friend computer and it was not abit motherboard and it was no such errors.

---

