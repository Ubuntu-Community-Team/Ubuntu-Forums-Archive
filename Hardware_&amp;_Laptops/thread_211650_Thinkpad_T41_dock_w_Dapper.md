---
title: "Thinkpad T41 dock w/ Dapper"
date: 2006-07-08
forum: Hardware &amp; Laptops
---

### Post by devnulljp on 2006-07-08
I have a THinkpad T41 with a mini dock--it worked well with Ubuntu 5.10 but after upgrading to dapper it's essentially just a big power supply...the usb ports are all dead to the OS. (they still work in windows though).

What's interesting is the buses seem to be seen, just not working.

$ lsusb
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 011: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 010: ID 067b:2507 Prolific Technology, Inc.
Bus 002 Device 001: ID 0000:0000

Both the mouse and the ext HDD (Prolific) are plugged into the two ports on the body of the thinkpad (listed as bus002), so there are other buses seen.

No changes sees in tail -f /var/log/messages on plugging anything into the ports on the dock...

Only thing I can think of is I installed with the pc off the dock...am I missing a kernel module? Any ideas? Anyone else?

---

### Post by K0LO on 2006-07-08
This site may be of some help:

[http://www.thinkwiki.org/wiki/Category:T41](http://www.thinkwiki.org/wiki/Category:T41)

See "Problem with USB2.0"

Mark

---

### Post by devnulljp on 2006-07-09
Thanks for the info - interesting and useful looking site. I have run into the probloem with usb2 and found that removing ehci_hcd helps with getting drives recognised. Unfortunately, this is a separate issue -- I have to disable ehci_hcd to get drives working on the laptop's usb ports, but it makes no difference to the dock in Dapper unlike 5.10

---

