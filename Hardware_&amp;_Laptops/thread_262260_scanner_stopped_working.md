---
title: "scanner stopped working"
date: 2006-09-21
forum: Hardware &amp; Laptops
---

### Post by Lary Grant on 2006-09-21
I installed a Brother MFC210C (which is both a printer and scanner, using a USB connection) using [http://ubuntuforums.org/showthread.php?t=105703](http://ubuntuforums.org/showthread.php?t=105703) .  It worked perfectly, but now the scanning no longer works.  When I go into xsane and click Scan, I get "Failed to start scanner - invalid argument".

How can I fix this?

---

### Post by John.Michael.Kane on 2006-09-21
What was the last thing you did pryor to the scanner failure?

Have you tried to redo the howto?

Have you tried restarting the machine with the printer on or off?

---

### Post by Lary Grant on 2006-09-21
I did try the howto again.  I have rebooted since then, but I think only with the MFC turned on.  I'll try with it off when I get back to that machine.  The last significant thing I did was install wine.

---

### Post by John.Michael.Kane on 2006-09-21
I don't feel installing wine would have affected your scan-install.

At the very least you could uninstall wine,and see if you regain your scan abilities

---

### Post by ubuntubrian on 2006-09-21
I have a similar problem involving my Epson 4990. I had been scanning fine last time and since I upgraded some packages that Update Manager listed, some Clam packages and an updated kernel (2.6.15). When I start XSane I am presented with 2 scanners, the 4990 and an Epson GT-X800 which I don't have. Previously I picked the 4990 and scanned away. Now picking it I get an invalid argument error also as well as a device busy error. The scanner also stops, meaning the scanning lamp goes out and nothing happens. rebooting the scanner and/or my computer changes nothing. However, I can scan as before if I choose the GT-X800 scanner. Maybe a corrupt file or something in the scanner settings?

---

### Post by jmwyatt on 2006-11-02
The 4990 is the US version of the GT-X800...

---

