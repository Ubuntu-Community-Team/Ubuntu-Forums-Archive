---
title: "USB UPS install in 7.10"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by atthecoast on 2007-10-21
I have a Trip-Lite Omni1000 UPS and would like to get this working under Ubuntu 7.10.

Just before a fresh install of 7.10 I was running 7.04 and installed packages "nut" and "nut-usb". I do not recall doing any configuration of nut at all. I plugged the UPS USB cable in the computer just before my install of 7.10 and was pleased to see an icon for the UPS show up in the top tool bar on a reboot.

I expected that the 7.10 release would display this as well once I installed nut and nut-ups packages. However this is not happening.  My /var/log/messages file shows "USB HID v1.10 Device [Tripp Lite .... on usb-...." so the OS still sees the device.

I tried creating various files under /etc/nut to manually configure the UPS. So far I cannot find a driver file under /lib/nut that will work. I have tried newhidups and tripplite_usb as well as others. I get a failure message if I execute "upsdrvctl start", indicating that it cannot find a UPS to match the driver specified.

From a nut hardware compatibility web page I think I may want a driver "usbhid-ups" however this does not appear in the /lib/nut directory (nor anywhere else on the system) and I can't figure out where I might find this.

I am also rather confused as to why this UPS was found and all information about it displayed just fine when I was running Ubuntu 7.04. I really don't think I had to do anything at all to have that release find the UPS.  Perhaps there was some other package installed of which I don't know about now.

Any ideas on getting this working would be appreciated. I've been doing a lot of searching on the web with no success so far.

---

