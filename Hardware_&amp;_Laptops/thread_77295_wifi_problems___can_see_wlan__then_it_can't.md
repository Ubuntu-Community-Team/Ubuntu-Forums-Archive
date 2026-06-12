---
title: "wifi problems :  can see wlan  then it can't"
date: 2005-10-16
forum: Hardware &amp; Laptops
---

### Post by dotdot on 2005-10-16
hi folks,
I've just installed 5.10 after having some problems on 5.04 ....
env = sony vaio pcg-x29.
I have a dlink G604 router.
and DWL G122 usb wifi link.

I have installed ndiswrapper - and gone through the process covered in...
[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

on typing iwconfig - i get nothing for ages then all of a sudden the light comes on (on the usb link). .... then dies.

in  that short time i got iwconfig to tell me i had wlan with essid etc looking good.

looking through dmesg .. i see...

wlan : ndiswrapper ethernet device .. using driver netrtusb, config file ...
then a couple of lines later...
ndiswrapper (usb_submit_nt_urb:6212): usb_reset_pipe()= -71.
ndiswrapper (usb_reset_port:633) : usb_reset_device()= -19
usb 1-1 : usb disconnect,address 27
ndiswrapper:device wlan0 removed.

..any ideas people ?

..

---

