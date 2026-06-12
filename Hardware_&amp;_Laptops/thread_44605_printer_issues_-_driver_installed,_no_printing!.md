---
title: "printer issues - driver installed, no printing!"
date: 2005-06-26
forum: Hardware &amp; Laptops
---

### Post by betty on 2005-06-26
Dear All:

I have recently just migrated from Xandros 3.0, which I found a little bit sluggish.  I am learning ubuntu/gnome, and I am finding that the interface is about twice as fast.  BUT, I am having some printer issues-

I installed the driver from the installation cd of my Samsung SCX-4100 printer.  The printer is installed- everything loooks good.  Printer reports as 'ready'. But, when I try to print something, it just sits there.  *Nothing* happens.  The printer is connected via a USB port, and when I manually specify a port under the options, it is detected under USB #1.  Still, no printing.

Can anyone help me on this?

Many thanks,
betty

---

### Post by Navin_Johnson on 2005-06-27
I'm not sure if this will help or not but did you try to restart your CUPS?


$ sudo /etc/init.d/cupsys restart


I'm working on my own printing problems but this helped me get a little further.

Best,
Navin Johnson (eric)

---

### Post by David Haas on 2005-06-28
Betty--I see no PPD file for the Samsung SCX-4100 printer listed in Hoary at /usr/share/cups/model/foomatic-ppds/Samsung where the Samsung PPD files are located. Where did you install the driver? Ordinarily, when a PPD file is selected in Linux, an unzipped copy is placed in /etc/cups/ppd. Do you have yours there?  I assume that your CUPS and foomatic packages were installed by default. You could check this in Synaptic Package Manager (System>Administration>Synaptic). I know that when one doesn't have the PPD file set up or installed correctly, the printer is mute.
David

---

