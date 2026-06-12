---
title: "Ubuntu 10.10 refuses to use AVM Fritz USB at startup"
date: 2011-01-17
forum: Hardware
---

### Post by du3113 on 2011-01-17
Hello there,

I'm new to this forum and hope that I found the right place for this post.
My problem is the following:

After hours of trying and following many step-by-step tutorials I got my AVM Fritz USB WLAN Stick (v 1.1) running via ndiswrapper.
After reboot it does not work anymore. So I have to run the following script and reboot my PC to get it running again:
[FONT=Courier New]cd /home/duelle/fwlan64
sudo modprobe ndiswrapper
sudo ndiswrapper -r fwlan64
sudo ndiswrapper -i fwlan64.inf
sudo ndiswrapper -ma
dmesg | grep ndis

[FONT=Verdana]I tried to add the line "ndiswrapper" to the /etc/modules.
Since I did that, ndiswrapper is loaded and with 
[FONT=Courier New]ndiswrapper -l[/FONT]
It always tells me, that the driver is installed and the hardware is present.
[FONT=Courier New]/etc/modprobe.d/ndiswrapper.conf[/FONT]
also contains the two lines that are present after doing
[FONT=Courier New]ndiswrapper -ma[/FONT]

All these things are (afaik) correct. And it is in this state even when the stick doesn't work (after reboot).
Anything has to happen that the stick works after reinstalling and rebooting.
But after a simple reboot it refuses to do so.

I'm using Ubuntu 10.10 64bit
Kernel 2.6.35-24
ndiswrapper v1.56

Thanks for your help in advance!

Best wishes
[/FONT][/FONT]

---

