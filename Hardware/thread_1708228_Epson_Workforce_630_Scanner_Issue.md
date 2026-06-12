---
title: "Epson Workforce 630 Scanner Issue"
date: 2011-03-16
forum: Hardware
---

### Post by Irishwunda on 2011-03-16
Good morning Ubuntu Forums! Long time Ubuntu user, first time poster.

So I got a new Epson Workforce 630 printer for my home office, which I primarily use with my Ubuntu 10.10 laptop. I have installed the required printer driver packages and it works perfectly. However I have a bit of an issue with the scanner...

Basically, as long as I have a single text or photo page on the scanner glass I can use 'Image Scan!', XSane or 'Simple Scan' to capture that one page. However as soon as I attempt to use the Auto Document Feeder I get an I/O error from all three programs and the page gets half fed through the rollers. I scan multiple documents at a time that need to go to a single PDF so this, obviously, is not acceptable!

These are the packages I have installed:
epson-inkjet-printer-workforce-635-nx625-series_1.0.0-1lsb3.2_i386.deb
and for the scanner:
iscan-data_1.6.0-0_all.deb
iscan_2.26.1-3.ltdl7_i386.deb
iscan-network-nt_1.1.0-2_i386.deb

all of which were suggested by Sisco311 in another thread involving this printer. Still I am having an issue with this.

Can any of you wonderful people help me out here? Thanks in advance!

---

### Post by Irishwunda on 2011-03-16
Okay so scratch that... I found an older thread that pointed me to the epkowa.conf file in the sane.d directory and I've got it configured so that I can scan from the ADF without fail from the laptop itself.

However I still cannot get the printer to recognize the laptop as a valid "Scan to PC" option via the wireless network (It only shows 'USB Connection' as an option). Normally this would be alleviated by the included Epson software package, but as we all know it is not Linux compliant.

Any suggestions on getting the laptop recognized via the wireless network so that I can scan to it directly from the printer's control panel?

Thanks.

---

### Post by Njlarson88 on 2011-05-13
What did you change in that config file?

---

### Post by Irishwunda on 2011-05-13
Check your pm.

Also, I've semi solved this issue by just using a memory card in the Workforce 630, scanning to that, and just accessing it via the wireless network.

So in a roundabout way... Solved.

---

### Post by jemcmahon on 2011-07-12
I'm experiencing the problem of ADF scanning resulting in a half fed page and an IO error.  What exactly did you add/change in epkowa.conf?  Thanks.

---

