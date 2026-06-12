---
title: "HP DeskJet 3653 won't print..."
date: 2007-09-16
forum: Hardware &amp; Laptops
---

### Post by IAmMe1 on 2007-09-16
I know this is a somewhat common problem, but I can't find a good solution that works for me... My HP DeskJet 3653 won't print. First of all, I have the printer connected to a USB port in the back of my box, but when I try to add a printer, the printer doesn't show up under detected printers. I manually select a location, then select the hpijs driver. There seem to be no other problems, until I try to print... It says that the printer has a job, but it's not doing anything. Any ideas on how to solve this?

Thanks.

---

### Post by handuma on 2008-02-13
I have experienced similar problems with hp Deskjet 3653 printer using Ubuntu versions  Breezy (5.10) and Gusty(7.10). I replaced  hp Deskjet 3653 with hp Deskjet 6112 and it was automatically detected by both versions. Maybe editing files manually could help?

 I found a work around for the hp Deskjet 3653 printer on Ubuntu forums, [https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp)  (see last line below), but it did not work for me.


Make:  HP
Model: DeskJet 3650
Driver: hpijs
Supported: No
Works: Yes
Version: v5.04 (Hoary) & v5.10 (Breezy)
Not detected. Have to choose it from the list in Gnome printer install.

---

### Post by Mohammed Nisaruddin on 2008-02-13
In my laptop having operation system 98 so ,i want to upgrade this for xp so how can i do this,i am waiting for u r reply.

---

### Post by RequinB4 on 2008-05-18
Here's a nice GUI tutorial for hp deskjet 3653 on any ubuntu 7.10 or later:

After using the default "printing" program (system - admin) to tell CUPS the specifications you want for your printer and the driver (the 3650 hplip one), you then need to install the secondary "Printing" application from applications - add/remove, then run the second "Printing" in system - administration, then rightclick the deskjet_3600 and click properties.  Click the Connection tab, click "Local or detected printer", "Use a detected printer", and "hp deskjet 3600"

Now print a test page.  It should work well.

P.S. - If you only have a black cartriage inside, the print will be very light.  Solve this by going to system - admin - printing (first one) and under "printer options" change printout mode to "normal greyscale"  Hit apply.  You will have to change this back if you want to print in color.

---

