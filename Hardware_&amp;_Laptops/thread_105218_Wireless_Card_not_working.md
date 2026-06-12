---
title: "Wireless Card not working"
date: 2005-12-17
forum: Hardware &amp; Laptops
---

### Post by hadji on 2005-12-17
Hi, 
I have a linksys wireless adapter. It works on the XP but I don't know how to install it. 
tried the driver which came along the card. but no use.
any suggestions?

thanx.

---

### Post by Lambert on 2005-12-17
More information is needed and we'll start with just this.

What make model of card?

Post output of this command from terminal

 lspci -v

The drivers on the cd are probalby only for a windows os. I don't know of any manufacture supplying linux drivers with their devices. If you have a device with a supported chipset there may be a driver with breezy that will load. All you will have to do there is go into system>administration>networking and try to configure your network. Try to go here first. If you see the device in the list there is a loaded driver for the device, 

If it's not a supported chipset then there is an app called ndiswrapper which basically makes a windows driver work in linux.

---

