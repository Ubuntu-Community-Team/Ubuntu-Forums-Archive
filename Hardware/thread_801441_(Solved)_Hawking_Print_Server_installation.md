---
title: "(Solved) Hawking Print Server installation"
date: 2008-05-20
forum: Hardware
---

### Post by vancouverite on 2008-05-20
Hi all,
This is just an FYI into the archives of solved problems.  I installed a Hawking Technologies HPS12U Print server on my network and found it rather difficult to setup given the lack of any documentation on their website.  It is, however, quite simple.  The correct procedure is:

1) Determine from your router what the IP of the device is.
2) Point firefox to the device and setup a static IP following the manufacture guide (this is the same as in Windows, and is pretty self explanatory).
3) Open "System -> Admin -> Printing" from the menus.
4) Add a new printer and select LDP as the host type.
5) For host enter "<device IP>/lpt#".  The lpt# is either lpt1 (parallel port), lpt2 (usb 1), or lpt3 (usb 2).
6) Click forward and select the driver for the printer that you have attached to the port.
7) Proceed with naming, etc and you are done.  A test page should print without a problem.

Cheers,
Vancouverite

---

### Post by chudux on 2008-12-02
Thank you!

---

### Post by jenkinsr99 on 2008-12-03
Most excellent advice from Vancouverite, I thought my Hawking print server was a lost cause, thanks!

---

### Post by joejoe148 on 2008-12-21
I applied your solution to a buffalo print server (lpv2-usb-tx1) and used the IP address of the server followed by lpt1 (there is only one printer port on this server) and it allowed me to set up and print.  Thanks for the post. 

but,

there is a significant difference in print speed between direct connection and server connection.  Is that normal?

---

### Post by avinegar on 2010-06-29
Thank you so much. The installation went like a charm!

---

