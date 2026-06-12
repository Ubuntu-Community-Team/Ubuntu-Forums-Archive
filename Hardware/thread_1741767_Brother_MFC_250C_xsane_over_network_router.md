---
title: "Brother MFC 250C xsane over network router"
date: 2011-04-28
forum: Hardware
---

### Post by SnappyU on 2011-04-28
Hi,

How can I access my brother MFC-250C's scanner function over the network router?

My setup:

Notebook --- wifi --- router --- usb --- MFC-250C

My router detects the printer and displays it correctly at router's address with port 9100 (standard socket printing port no.)

I can print to it via CUPS with no problem.

Now I am thinking of accessing the scanner function using the above setup.  Is it possible?

I have xsane, sane-utils, saned etc installed on my notebook.  I suspect that I have to install these on my router and expose the scanner function via the router.  Which is possible?

My router is an Aztech HW550-3G with vanilla firmware.

Ideas?

PS: I know the following will work, but hey, this is Ubuntu right? ;)

Notebook --- wifi --- router --- share out scanner
+---usb---scanner

---

### Post by SheamusPatt on 2011-08-16
There is information on the Brother web site here [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html) . You likely don't need to install the Brother packages, as recent Ubuntu releases include them. You'll need to run brsaneconfig/2/3 though, as described here.

That assumes you can reach the scanner functionality over the LAN, though. I see now that the 250C is a USB device, though, so it all depends on what your router can expose over its connection. If the printer just shows up as a Samba (Windows network) printer, I suspect you won't be successful as there's no equivalent scanner network protocol (network scanners all use proprietary protocols, I believe, and the router isn't likely to emulate them).

---

