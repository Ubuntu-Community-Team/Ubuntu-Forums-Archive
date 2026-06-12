---
title: "Wireless Linux Restricted Drivers for my T61P laptop"
date: 2008-07-22
forum: Hardware
---

### Post by malarie on 2008-07-22
Good evening Ladies and GentleMEN!! (We're tonight's entertainment)

Okay,, So here is my problem, i just bought this nice Thinkpad T61P, and I installed Ubuntu 8.04 o it.  The Wired network works fine, but for some reason it My wireless card cannot be activated.  I do not have the restrcited drivers for it..   I have the restricted driver for my nvidia 570M, it was automatically detected and installed, but for the wireless card its another story...

lspci -v detects it, but i cant activate it...

Anybody have a small clue??


03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
	Subsystem: Intel Corporation Lenovo ThinkPad T51
	Flags: bus master, fast devsel, latency 0, IRQ 217
	Memory at df2fe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: **<access denied>**


Merci

---

### Post by nickdbliss on 2008-07-22
u need to install drivers for it. Give more info. Try posting results of lspci,iwlist scan and ifconfig..

---

### Post by prshah on 2008-07-22
> **malarie said:**
> 03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)


The 4965 is a well-supported, but slightly iffy, chipset.

Why not try my [step-by-step guide to install and setup wireless]("http://ubuntuforums.org/showpost.php?p=4723545&postcount=1")? It also shows expected outputs, so you can see where something is going wrong. Also, it shows how to use ndiswrapper, but if your wireless card is detected fine (see output of command "iwconfig") then you can skip the part on setting up ndiswrapper. (jump to step 9).

If you run into problems, post back here with the commands and the outputs that you received.

---

