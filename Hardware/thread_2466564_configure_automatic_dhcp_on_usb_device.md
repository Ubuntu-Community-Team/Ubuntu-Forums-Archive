---
title: "configure automatic dhcp on usb device"
date: 2021-08-30
forum: Hardware
---

### Post by anisaw on 2021-08-30
HI all, new here. 
I have a remarkable tablet. I want to connect the tablet and copy files off of it. The way this is done is by enabling usb data transfer, and then visiting 10.11.99.1 in my browser. So the remarkable needs to be configured as a usb gadget every time I connect it. My issue is that whenever I connect the tablet, I have to do an ip link command, find the device id of the usb adapter, and then run sudo <device_id> dhcpcd. Unless I do this every time I plug in the tablet, I cannot connect to the tablet with my browser. I would like to just plug it in, and visit the ip. This behavior is what I got on my manjaro system, but I have recently installed ubuntu 20.04, and I cant get the same behavior. I have tried running sudo systemctl enable dhcpcd, but no luck. 

Thanks for your help!


P.S. I have Regolith (Ubuntu 20.04 with i3 window manager and gnome settings gui) installed on a thinkpad t480s.

---

