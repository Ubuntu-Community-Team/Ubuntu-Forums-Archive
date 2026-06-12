---
title: "Canon i80 using Feisty CUPS i850 driver has color stretch"
date: 2008-10-07
forum: Hardware
---

### Post by daveola on 2008-10-07
I'm on Feisty.

I've got a Canon i80 which CUPS easily finds.  It recommends the i850 driver - I don't see an i80 driver in the list.  The printer prints fine on my OSX box.

When I print on Ubuntu, however, the black and yellow are fine, but the magenta and cyan are stretched out to the right.  I've put up a photo of the Ubuntu test page print at:

[http://davepics.com/tmp/Canon-i80.CUPS.stretched.jpg](http://davepics.com/tmp/Canon-i80.CUPS.stretched.jpg)

It's easiest to see the problem if you just look at the Ubuntu logo.  The yellow is in the right place, but magenta and cyan stretch off as if the paper width was much larger.

Am I using the wrong driver?  Is there any way with the Gutenprint CUPS expert driver that I can set some sort of scaling parameters for the cyan/magenta colors?  Can this only be solved by throwing money at the trueprint (for sale) drivers?

---

### Post by daveola on 2008-10-15
Bump?

---

### Post by gnwiii on 2009-06-21
After upgrading from 8.10 to 9.04, I'm getting the same color stretch 
problem on a PIXMA MP510 as the OP reported.  One difference is that 
my test page printouts show the ghostscript Revision, which was 863 on the
test page that worked, but 864 on the pages that fail.  The OP's image
is cut off at the bottom, where the version numbers are displayed.

For the record, there is information about Canon's GPL drivers in:

MontrealSummit-2007-Canon_Printer_Drivers_for_Linux_070926-2.pdf

available for downloading.

---

