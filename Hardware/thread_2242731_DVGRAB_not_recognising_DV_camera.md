---
title: "DVGRAB not recognising DV camera"
date: 2014-09-03
forum: Hardware
---

### Post by ian.fenelon on 2014-09-03
Hi,

I have a Panasonic DV camera connected to my "old" Dell Inspiron 6400 laptop (which is very happily running Ubuntu 14.04) via a firewire cable.

lspci tells me that I have -

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller


lsmod tells me I appear to be using the firewire "new stack" - ?

firewire_core          61867  1 firewire_ohci
crc_itu_t              12627  1 firewire_core

When I run this -

ian@ian-MM061:~$ tail -f /var/log/kern.log

I see messages like this (when the camera is connected) - 

Sep  3 22:02:37 ian-MM061 kernel: [ 1786.148098] firewire_core 0000:03:01.0: rediscovered device fw0

When I run the dvgrab command, I get - 

ian@ian-MM061:~$ dvgrab -i
Error: no camera exists


Is this because I need to run the "old" stack? The firewire card is "old"?
If so, how do I do this?

Or is there something else I need to do to get this to work?

Hope you can help!

---

