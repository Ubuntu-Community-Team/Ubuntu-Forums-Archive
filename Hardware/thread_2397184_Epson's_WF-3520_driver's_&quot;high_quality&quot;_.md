---
title: "Epson's WF-3520 driver's &quot;high quality&quot; print setting does nothing?"
date: 2018-07-26
forum: Hardware
---

### Post by mikeymikec on 2018-07-26
I'm running Lubuntu 18.04 LTS x64 with whatever the latest driver from the Epson website for this printer, and the printer is networked.

I don't have any problems with normal printing, but when testing things out I tried the high "print quality" setting, did a test print (all of this with system-config-printer) and the result was identical to a standard quality printout and took exactly the same length of time to print.

---

### Post by mikeymikec on 2018-10-18
I had another crack at this problem today and fixed it.  I started by trying it on a test Lubuntu VM I had set up (same version as my primary OS), and followed these instructions:
[https://askubuntu.com/questions/771427/how-to-install-epson-printer-drivers-on-ubuntu-16-04](https://askubuntu.com/questions/771427/how-to-install-epson-printer-drivers-on-ubuntu-16-04)
I downloaded what Epson regard to be their full feature print driver (amd64 deb file) from the Epson website.

When I ran through the instructions on the VM, the proper driver was automatically picked when going into system tools > printers > add.  However on my main OS, printer > add still picked up the driverless version (this can be checked by opening the printer properties and reading the 'make and model' text box).  I then clicked on 'change' next to it, select driver from database, Epson (recommended), I think it then picked my Epson model number itself (if not pick it), then it listed two drivers on the right hand side, the driverless one and the one I installed from the .deb file.  I picked the non-driverless one, clicked OK, then I had the proper driver ready to go and high quality printing now works.

---

