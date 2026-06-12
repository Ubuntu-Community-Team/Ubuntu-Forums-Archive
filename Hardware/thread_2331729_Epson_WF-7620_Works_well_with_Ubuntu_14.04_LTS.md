---
title: "Epson WF-7620 Works well with Ubuntu 14.04 LTS"
date: 2016-07-25
forum: Hardware
---

### Post by glenora on 2016-07-25
I hope this is appropriate for this section of the forum.

Anyone looking for a multi function printer to run with Ubuntu.
Epson WF-7620 works well.
I just finished setting it up with no real issues.

Install lsb first from a terminal.
sudo apt-get install lsb

Then you can download all the drivers in deb form from the epson US site.
Then right clicking on the drivers and selecting install using the software centre worked fine.

The final piece of the puzzle was to setup a fixed ip address for the printer. Rather that do this from the printer itself, I set my router to always reserve one for the printers mac address.

Then after installing the iscan drive (from the epson support page) you need to edit /etc/sane.d/epkowa.conf and add
net <your printers reserved ip address>

This is working for me to print and scan over my network from Ubuntu 14.04 LTS on a sony vaio laptop.
The printer is connected to my network via wifi.

Very happy that Epson are providing Linux drivers.  They also have rpm for fedora/redhat users.

---

### Post by Linuxisfast on 2016-07-25
It also works equally well with 16.04 now that Canonical restored lsb in the distro.

---

