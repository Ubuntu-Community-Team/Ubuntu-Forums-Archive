---
title: "Canon ix4000: turboprint installation"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by eeried on 2007-05-03
Hello,

I need to install the turboprint driver for Canon ix4000 for someone in our LUG.

I've read the the on-line manual on the Turboprint website an dI've found the following  on this forum:
> There's a .deb package you can download and double click to run with the GDebi GUI installer.

After it's installed, you should be able to go to "System | Administration | Printing" double click "New Printer", choose "Local Printer", check "Use a detected printer" (hopefully), then click "Forward." On the next screen change "Manufacturer" to "CANON TurboPrint" (third line on the right for me). Choose the "Canon_PIXMA_iP1700 TruboPrint" driver from the list and finish the Wizard like normal.

As I tried to install the driver while using Dapper Live-Cd and it didn't work (no printing),  I'd like to make sure how to install it.

So you download a DEB package and you install it: you get two icons on the desktop. Then do you follow the Turboprint manual or do you go to System etc. as above.

The Turboprint manual is probably a bit ancient:
> # You must be logged in as "root" for the installation process. If you are not logged in as "root", you can temporarily switch to root by entering in the shell window:

    xhost +
    su root
    export DISPLAY=:0

The commands "xhost +" (give other users access to the X display) and "export DISPLAY=:0" (set the X display environment variable) make sure that programs can open windows on the X display after switching to root. After entering "su root" (switch to root login) please enter the password for root.
...

If you installed TurboPrint as an RPM package, please start the printer setup tool "xtpsetup" to choose a printer driver. Continue with reading registering TurboPrint.


I suppose we should follow the RPM instructions, but if you click on the setup icon then you aren't root, does it matter?

Your help will very very much appreciated,

---

