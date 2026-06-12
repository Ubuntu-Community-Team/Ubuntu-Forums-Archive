---
title: "HP Laptop too hot"
date: 2011-07-16
forum: Hardware
---

### Post by najdorfchess on 2011-07-16
Hi all. My friend uses Ubuntu 10.10 64-bit OS (wubi install) in her HP laptop and has been experiencing too much heat on the laptop body and on the touchpad. I think the problem could be due to CPU overclocking and/or cooling fan management. Could anyone temme how to sort this problem? Details below

Laptop config
=============

Model - HP G42-458TU
RAM - 4GB 
OS - Ubuntu 10.10 64-bit installed within Windows 7 via Wubi
Processor - core i3 m370 2.4Ghz

Solutions tried
===============

Installed gkrellm but this doesnt seem to work during start up. Have no idea if we need to config it. 
Unable to install i8kutils since they are only for Dell laptops. 
lm-sensors are already installed.

---

### Post by limescout on 2011-07-16
For starters, set the CPU clock back to the factory setting.  Also, make sure the vents for the fans are not covered by anything and have lots of space.  If you're interested, they make laptop cooling pads to provide cool air to particularly hot PCs.

---

### Post by najdorfchess on 2011-07-17
> **limescout said:**
> For starters, set the CPU clock back to the factory setting. 

How could I do that?

---

### Post by najdorfchess on 2011-07-17
^Bounce

---

### Post by najdorfchess on 2011-07-19
Someone kindly help.

---

### Post by aria1121 on 2011-07-19
Meanwhile, I am waiting to get help from someone ;)

When you turn it on (trigger the power button) you have to enter the BIOS. Check it's manual how to. Normally you have to quickly after it started press [F1], [F2], [F10], [F11], [F12], [Del], [Space] or something like that. I don't know how your BIOS works, but you have to navigate to your CPU settings. Set the CLOCK SPEED, CYCLE SPEED or something like that down to like 1.8 GHz. Now go to Exit and save changes before exiting (usually with [F10] or [F12] (Never [Ctrl]+[Alt]+[Del] in BIOS unless it freezes for what for reason!) Now boot again.

Also, I have a 1.4 GHz which never ran Kubuntu without overheating.

Did this help?

---

### Post by najdorfchess on 2011-07-20
Thanks for ur reply. Will this not affect the performance?

---

