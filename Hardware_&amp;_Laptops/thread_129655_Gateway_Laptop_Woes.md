---
title: "Gateway Laptop Woes"
date: 2006-02-14
forum: Hardware &amp; Laptops
---

### Post by PhoneGuy on 2006-02-14
Hi folks.

I've got a Gateway 400VTX, and I can't seem to get the xorg to run.

I get:

"Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?"

Doesn't let me choose yes, or no.

When I try to manually run startx, I get:

EE: I810(0): No Video BIOS modes for chosen depth.
EE: Screen(s) found, but none have a usuable configuration.
Fatal Server Error:  No Screens found.

Any ideas?

Framebuffer works during install...so...I'm scratching my head as to why xorg won't work.

PhoneGuy

---

### Post by jml on 2006-02-14
Graphics problems with Linux on laptops are not uncommon.  The reason the framebuffer mode worked is because it does not use x.org for its display.  Were you able to do the install without problems.  Was the installation menu screens drawn OK?  If they were, then it mught be helpful to install 5.10 again with the command "Linux vga=771"  Without the quotation marks.  I needed to do that in order to get X running properly on my laptops.  (a pair of IBM Thinkpads)  Hope that this is of help.

Joe

---

### Post by PhoneGuy on 2006-02-15
Actually, running vga=771 does not work for me.

I can get slax-killbill to run...and have been able to use Knoppix....so, I'm scratching my head to figure out why it's not working.

PhoneGuy

---

