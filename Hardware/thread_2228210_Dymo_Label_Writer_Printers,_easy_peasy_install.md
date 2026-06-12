---
title: "Dymo Label Writer Printers, easy peasy install"
date: 2014-06-06
forum: Hardware
---

### Post by brian-i8219utmhlx17 on 2014-06-06
First get glabel from the repositories

Then get the Dymo Drivers here:  [http://download.dymo.com/Software/Linux/dymo-cups-drivers-1.4.0.tar.gz](http://download.dymo.com/Software/Linux/dymo-cups-drivers-1.4.0.tar.gz)

Unpack the archive and cd/ to the directory the archive created

In a terminal do

./configure

then do

make

At this stage you may get a missing g++ error. If you don't then in the terminal do

sudo make install

If you do get the missing g++ then do

sudo apt-get install build-essential

Then do 

sudo make install

Plug in the USB of your Dymo Labelwriter and then add it as a printer. It will come up on the search as "DYM0008" don't about this, this is OK and choose it. Cancel the driver search if it comes up.

Click on Model and then Choose PPD files and go to /usr/share/cups/model/ and choose the correct driver for your printer. Works a treat. Easy Peasy :)

Voila! One more reason not to use Microcrap Windoze :)

---

