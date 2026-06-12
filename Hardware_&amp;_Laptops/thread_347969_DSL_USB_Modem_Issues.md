---
title: "DSL USB Modem Issues"
date: 2007-01-28
forum: Hardware &amp; Laptops
---

### Post by emerc01 on 2007-01-28
I am running kubuntu 6.10 (edgy) on an HP Compaq nx6110 laptop. 

As I live in a country with limited availability of decent electronics, I am in possession of a Prolink Hurricane 9600 ADSL USB Modem.  (I am aware of the evilness of winmodems etc etc).    To the best of my ability, I have searched many web forums and have reviewed pages such as linmodems.org etc to attempt to figure out how to configure this modem for use.  I am unable to discover the chipset of the modem as the scripts available seem only to be linux based (i am connecting through a windows xp machine at the moment) and the one script i did find for windows just threw back information on the internal hp modem on this computer.

My questions are thus:

1. how do i find out the chipset of this modem while using xp?
2. how do i know if kubuntu is registering the fact that i have a device connected to the usb port (it doesn't seem to do a thing with it)?
3. how do i configure this modem for use with edgy?

also, again aware of the issues with linmodems, my alternative solution could be to purchase a router and connect through that. 

4.  will this be a viable solution or will i still have problems with the modem?


thanks.

---

### Post by RandomJoe on 2007-01-28
When you are booted to the Live CD, you can open a terminal and run 'lsusb' to get a listing of connected USB devices, which bus they are on, and their IDs.  It may or may not have a human-readable description out to the side.  My keyboard and trackball do, but my USB card reader only shows the ID (like 11b0:6208 ).  I was able to confirm that was it by plugging/unplugging it and seeing what lsusb showed.  A search of Google (using the two numbers separately, without the colon) pulled up a few pages that talked about the device - perhaps that'll help you.

If you run 'dmesg | less', you will get a LONG listing (thus the need for list) that shows in pretty good detail what's happening when the system boots.  Search through that for lines referring to USB - it will describe what it has found, what modules it is loading for them, perhaps if something went wrong.

You mention possibly needing to purchase a router and connect through that - does the USB modem have an Ethernet port as well?  (Mine has both.)  If so, just plug the modem straight into the computer's Ethernet port.  You might need a crossover cable instead of a regular straight-thru cable.  If you can do this, it's not only viable it's preferable - it should work better than via USB.  I haven't seen a router that lets you plug in a USB model though, only Ethernet.

---

### Post by emerc01 on 2007-01-29
> **RandomJoe said:**
> When you are booted to the Live CD, you can open a terminal and run 'lsusb' to get a listing of connected USB devices, which bus they are on, and their IDs.  It may or may not have a human-readable description out to the side.  My keyboard and trackball do, but my USB card reader only shows the ID (like 11b0:6208 ).  I was able to confirm that was it by plugging/unplugging it and seeing what lsusb showed.  A search of Google (using the two numbers separately, without the colon) pulled up a few pages that talked about the device - perhaps that'll help you.

If you run 'dmesg | less', you will get a LONG listing (thus the need for list) that shows in pretty good detail what's happening when the system boots.  Search through that for lines referring to USB - it will describe what it has found, what modules it is loading for them, perhaps if something went wrong.

You mention possibly needing to purchase a router and connect through that - does the USB modem have an Ethernet port as well?  (Mine has both.)  If so, just plug the modem straight into the computer's Ethernet port.  You might need a crossover cable instead of a regular straight-thru cable.  If you can do this, it's not only viable it's preferable - it should work better than via USB.  I haven't seen a router that lets you plug in a USB model though, only Ethernet.

Thank you so much for your help.  My modem does not have an ethernet port unfortunately, but i am sure that with a little more persistance i can make this work!

---

