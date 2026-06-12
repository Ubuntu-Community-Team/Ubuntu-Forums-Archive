---
title: "Screen Issue"
date: 2005-12-07
forum: Installation &amp; Upgrades
---

### Post by DarthOverlord on 2005-12-07
Hello everyone.  I am trying to install Ubuntu 5.10 on the 2nd drive on this machine:

Opteron 165 (CCBWE 0534SPMW) @ 2.5Mhz (280x9)
Thermalright XP-90 with Panaflo 92mm fan
DFI Lanparty NF4 Ultra 704-2BTA
eVGA GEForce 7800GT
OCZ (1GB x 2) OCZ4002048ELDCPE-K
Windows XP MCE 2005
OCZ Powerstream 520 Watt SLI
WD SATA 160
Samsung SATA 120
Lian-Li PC-65B
Dell FPW 2005 Widescreen
Logitech z5500

I tried both the 32 and 64 bit versions and hit the same problem.  When I get to the log in screen, I type in my user name and password.  Then the screen gets a multicolored distorted image where the log in box was and the machine is frozen.

I installed off the discs that came in the mail and ran everything standard.  Please help. Thanks.

---

### Post by bananana on 2005-12-07
Is it possible that it's not your machine, but X-window that is frozen? Try CTRL+ALT+Backspace to see if X quits (you should be returned to the login screen). Also, CTRL+ALT+F1 (similarly for F2-F6) should bring up a text console. If these things work, then your problem is with your X configuration. Most likely the display driver or monitor settings.

---

