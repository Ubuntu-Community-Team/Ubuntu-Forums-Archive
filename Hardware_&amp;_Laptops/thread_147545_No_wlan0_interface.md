---
title: "No wlan0 interface"
date: 2006-03-20
forum: Hardware &amp; Laptops
---

### Post by FuriousLettuce on 2006-03-20
I recently re-installed ubuntu but am having issues getting my wireless USB pen to work. I know that it works as I have used it happily without any problems for weeks before. 

I have added the line 
```
iface wlan0 inet dhcp
```
to /etc/network/interfaces, but the gnome network manager cannot see it. 
In accordance to this, ifconfig -a lists no wlan0 interface and iwconfig reports no interfaces with wireless extensions. 

Ndiswrapper reports that the driver is installed correctly and that the hardware is present, but there is no ndiswrapper process running. I have modprobe'd ndiswrapper, but it appears to have made no difference.

Can anybody help me please?

PS: As an aside, something is wrong with the default ubuntu setup for my eth0:

when network manager is not running, ubuntu seems to find it impossible to use any network interfaces properly. I am able to ping addresses, but whenever I use the 'host' command, I receive 'Warning: message parser reports malformed message packet'. The only way I have found to get out of this is to first download links2 onto a different computer, including all its dependencies, and then install it. From there, firefox / synaptic can then visit any website that links has resolved. For example, to access updates, I must first visit 'http:gb.archive.ubuntu.com/ubuntu/', which will then allow Synaptic to stat all the package lists and download new ones, the first of which was network manager. Once network manager is installed and running, there are no problems whatsoever. This happened both before and after the clean install.

My ethernet interface is built into the motherboard - an nforce4 g/bit port.

---

### Post by dralaroc on 2006-03-20
Try this...unplug and reboot.  When logged in reinsert the usb adapter and see what ya get.

---

### Post by FuriousLettuce on 2006-03-20
Thanks :)

I'd forgotten to add it to /etc/modules!

---

