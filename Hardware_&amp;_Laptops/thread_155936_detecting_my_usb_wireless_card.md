---
title: "detecting my usb wireless card"
date: 2006-04-06
forum: Hardware &amp; Laptops
---

### Post by mrios on 2006-04-06
I followed the directions from this forum post: [http://ubuntuforums.org/showthread.php?t=106846](http://ubuntuforums.org/showthread.php?t=106846)

I've done everything they said, and now I have a driver compiled and located in the kernel. lsmod shows that the module is loaded. 

However, when I try to start up the network device, it tells me that there is no such device.

[INDENT]mrios@nullspace:~$ sudo ifconfig rausb0 up
rausb0: ERROR while getting interface flags: No such device
mrios@nullspace:~$
[/INDENT]

I have no clue what to look for. I found something interesting in my dmesg which may help:

[INDENT][   47.623933] rtusb: probe of 1-1:1.0 failed with error -12[/INDENT]

Is there any sort of mapping command that I need to do?

Additional information: I am running on a ppc platform. I don't know that that should matter, since I compiled the driver myself.

Thanks in advance,

---

### Post by Darkriser on 2006-04-06
that thread is great. but there are som details missing. important details;) . please, follow this link to complete the installation process. this worked for me absolutely great:rolleyes: 


[http://doc.gwos.org/index.php/Rt2x00drivers](http://doc.gwos.org/index.php/Rt2x00drivers)

---

### Post by mrios on 2006-04-06
I read that and tried it... still the same problem. I don't have my computer with me right now, but later on today I will print out all of my config files and the location of the rt2570.ko file in my kernel files.

But in the meantime, does anyone have an idea why the device is not acknowledged? 

To recap:
1. The kernel driver was natively compiled.
2. The driver was placed in the .../drivers/net/wireless/ folder
3. The config file /etc/modutils/rt2570 was set to have the single line "alias rausb0 rt2570"
4. The file /etc/modprobe.conf was removed.
5. The /etc/network/interfaces file has these lines added:
[INDENT]iface rausb0 inet dhcp
wireless-essid "something"
wireless-mode Managed
auto rausb0
[/INDENT]
6. The driver appears in lsmod and when I type "modprobe rt2570" after reloading the modules, I get no response (presumably this indicates success.)
7. My dmesg contains a line that says the USB device failed to load. (This is when I start up the computer with the wireless device plugged in.)

I am clueless about what I may have missed or what I did out of order. 
Any ideas?

---

