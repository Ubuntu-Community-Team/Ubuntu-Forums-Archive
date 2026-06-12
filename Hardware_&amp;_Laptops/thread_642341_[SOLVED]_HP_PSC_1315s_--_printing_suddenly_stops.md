---
title: "[SOLVED] HP PSC 1315s -- printing suddenly stops"
date: 2007-12-16
forum: Hardware &amp; Laptops
---

### Post by perixx on 2007-12-16
Hello ....

I've got the following problem, that my printer will go on printing very smoothly but then suddenly stops (usually on the second page, but sometimes earlier), with the status light blinking and won't resume anymore. 

At first I thought, that it was a problem with the colour-cartridge almost empty, but I renewed it and problem still remains.

The output of 
```
sudo tail -f /var/log/cups/error_log
```
is:
> [16/Dec/2007:20:10:25 +0100] Closing client 13 after 300 seconds of inactivity...
D [16/Dec/2007:20:10:25 +0100] cupsdCloseClient: 13
D [16/Dec/2007:20:10:32 +0100] cupsdUpdateCUPSBrowse: Refused 150 bytes from 192.168.2.32
D [16/Dec/2007:20:10:54 +0100] [Job 68] prnt/backend/hp.c 550: ERROR: 1014 media-jam-error; will retry in 30 seconds...
D [16/Dec/2007:20:11:03 +0100] cupsdNetIFUpdate: "lo" = localhost...
D [16/Dec/2007:20:11:03 +0100] cupsdNetIFUpdate: "eth0" = 192.168.2.32...
D [16/Dec/2007:20:11:03 +0100] cupsdNetIFUpdate: "lo" = localhost...
D [16/Dec/2007:20:11:03 +0100] cupsdNetIFUpdate: "eth0" = fexxxxxxxxxxxxxxxxxxxxxxx%eth0...


Re-plugging the printer won't do anything...
Using 
```
sudo /etc/init.d/cupsys restart
```
will throw out the stuck paper sheet and begin to print again (from start) - but will most likely stop again after a few seconds.

The only indication of a problem that I could find, was in the 'hp-toolbox' > status > 'code: 1014 error "cartridge or paper-jam".

The funny thing is: after re-booting, the printing-job is being executed again from start!

perixx

---

### Post by perixx on 2007-12-20
[COLOR="SeaGreen"]**PROBLEM SOLVED!**[/COLOR]

It seems that not Ubuntu was responsible for the printouts to break up while still being in progress - obviously a [U]rather cheap 
USB-HUB[/U] caused this trouble!

Connecting the printer to the motherboard's native USB-connector has seemingly disposed of the malady....
Therefore I'm gonna consider this issue as **solved** until I experience something different :)

By the way, downloading and installing the latest HPLIP's **hp-toolbox**-manager installer works like charme and will provide (also German) language support + cartridge status display... 
only a few dependencies to be resolved and some packages to be installed, but the terminal-output and the installer serves with detailed information! 

perixx

---

