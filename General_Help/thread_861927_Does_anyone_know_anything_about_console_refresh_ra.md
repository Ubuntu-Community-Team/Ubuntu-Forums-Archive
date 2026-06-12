---
title: "Does anyone know anything about console refresh rate?"
date: 2008-07-17
forum: General Help
---

### Post by samrat1985 on 2008-07-17
[COLOR="Black"][FONT="Courier New"]I am using "Ubuntu 7.04, Geforce 6200 CRT" monitor box. Xserver runs
at 1024x768 @ 85 MHz. I use the vga=786 kernel parameter & use fbset to
see console refresh rate, it use 640x480 @ 72 MHz & my eyes have trouble 
with all that flickering when using applications like elink or links2 -g 
at the console.
	
	I have read in kernel docs (vesafb.txt) that vesa cannot change 
mode dynamically after bootup & forget about refresh rate if 
you use vesafb! On a vanilla Ubuntu install, console RR (refresh rate) 
was 60 MHz. This box is a dual boot. WinXP RR was cranked up at 85 MHz, 
then I installed Ubuntu & Console RR was detected as 72 MHz.
	
	So now what do I have to do to have a "console 640x480 @ 85 MHz??"
This is the second time I am posting this as the answer I got before didn't 
solved it. 

Ps: For those who don't want to read that much..
* CONSOLE REFRESH RATE; 
* BOX CRT, UBUNTU 7.04, GEFORCE 6200
* USING VESAFB KERNEL PARAMETER "vga=786" @ BOOT TIME 
* HAVING PROBLEMS WITH FLICKERING AT CONSOLE APPS LIKE ELINKS
* XSERVER RUNNING AT 1024x768 @ 85 MHZ
* WANT 640X480 @ 85 MHz CONSOLE; HELP ME :( PLEASE

ANSWER I GOT BEFORE: 
Add modeline using gtf to xorg.conf. This doesn't work.
I wonder if it has to do something with vga parameter I give at boot time
or do I have to reconfigure something? [FONT="Courier New"][/FONT][/FONT][/COLOR]

---

### Post by samrat1985 on 2009-11-06
I switched to an LCD & my eyes thank me!

---

