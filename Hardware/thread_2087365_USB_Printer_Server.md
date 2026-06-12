---
title: "USB Printer Server?"
date: 2012-11-23
forum: Hardware
---

### Post by farna on 2012-11-23
I have a Zonet ZPS1000 that I have just tried to get working. It is supposedly Linux compatible. The web based setup address is 192.168.5.1. I can ping the address and the server is obviously scanning my 5 port dumb hub, but Firefox can't connect. 

I'm using Mint 12 (Ubuntu 11.10 based). I'm relatively new to Linux, but can use a command line (just not familiar with the commands... mostly a user). I used Network Tools to ping the device and get 100% returns.  My computer is plugged directly into the same hub, and I'm not running a firewall. Another computer accesses the internet over that same port, so the hub is good. 

If no suggestions on getting the ZPS1000 going, does anyone know of a USB printer server that will easily work with Linux?? This is the second one I've tried, bought it because the box said Linux compatible. Zonet is now out of business, so no help there!  The printer works attached to a USB port and other computers can access it through my computer, but I want to get away from the USB cable strung over my office floor.  Right now I'm just pugging in the USB cable when I need to print...

---

### Post by ahallubuntu on 2012-11-23
Try this guide to get started:

[http://www.draconis.com/blog/2006/11/10/how-to-setup-the-zonet-zps1000-print-server-on-mac-or-windows/](http://www.draconis.com/blog/2006/11/10/how-to-setup-the-zonet-zps1000-print-server-on-mac-or-windows/)

At least use the guide to get access to the device via the web.  It claims the device's default IP is 10.0.5.1 .  Connect the device via a switch or router and set a static IP on your computer to 10.0.5.2 and then try [http://10.0.5.1](http://10.0.5.1) .

You'd probably have best luck with IPP printing as described in the guide.  

Instead of using this print server, have you tried just sharing the printer over the network using one of the computers it is connected to via USB?

---

