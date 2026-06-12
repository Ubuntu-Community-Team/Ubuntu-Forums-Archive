---
title: "Help me configure my NEC Superscript 860 Printer"
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by Josh M on 2005-04-15
I am a Linux newbie, thanks for your help in advance. 

My printer was not configured during install. I can add a printer under System --> Administration --> Printing on parallet port #1 but this does not work and I receive a messase saying that the printer isn't connected, will try again in 30 seconds...

What steps can I take to auto-detect or configure my printer?

Thanks!

---

### Post by skoal on 2005-04-16
Sweet...

I thought I was all alone out here.  I have an NEC Superscript 870 and it works fine using cups.  I don't know what Ubuntu specific stuff you need to do to get it working, but here's my setup (straight from the local web browser admin tool).

Type in "http://localhost:631/" in your web browser and enter your root password to configure your printer.  Go to Manage Printers > Add/Modify Printer.  Use this info:

1. "Location"
Local
NEC-SS870

This info is superficial and name it what you want, more than likely not *870.

2. "Device"
Parallel Port #1

3. "Make"
HP

4. "Model/Driver"
HP Laserjet IIP series - CUPS+Gimp-Print v4.2.7(en)

* If that one doesn't show up, just use the Laserjet IIP series.  That should work.

When you "Configure Printer", check that 300x300 DPI is set (under "resolution") and I needed to change "Media Size" to Letter, not A4.

I've used this setup for sometime and I'm pretty sure the cups homepage says the 860/870 use the same setup.

---

### Post by Josh M on 2005-04-16
Setting up the printer as a HP Laserjet IIP worked, thanks  :)

---

### Post by skoal on 2005-04-16
Yes, sir.  I'm glad it worked.  By the way, if you find or know of any good online NEC toner retailers, please priv me or shoot me an email.  I bought a "new" one on eBay a while back and need a new one for my 870.  I've shaken this toner cartridge up and down and back and forth so many times now it's part of my morning stretch and exercise.  I use split toner on my hands as face warpaint to fire me up for a good workout.

Thanks.

---

