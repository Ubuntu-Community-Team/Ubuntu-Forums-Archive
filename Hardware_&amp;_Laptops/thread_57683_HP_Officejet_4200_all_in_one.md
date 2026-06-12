---
title: "HP Officejet 4200 all in one"
date: 2005-08-17
forum: Hardware &amp; Laptops
---

### Post by FCM on 2005-08-17
I need some guidance on what to do next. The printer function worked right from the install, however the scanner does not. 
When I try to start Xsane I get the message "no devices available'

Running lsusb gives me
Bus 001 Device 003 ID 03f0:3d11 Hewlett-Packard

sudo sane-find-scanner returns
found USB scanner (vendor 0x03f0 [Hp], product=0x3d11 [officejet 4200 series] at libusb:001:003

scanimage -L returns
No scanners were identified.

Before, I had Mandrake 10.1 installed and both functions worked fine - using KDE 3.2.3 but when I set up the printer it recommended using hpoj (this was also mentioned in a post in this forum). I used apt-get and installed hpoj. 

However, when I try to configure the printer it still recommends the hpijs driver - there is no option to use hpoj.

What am I missing? Thanks for your help.

P.S. getting this, and Totem, to work will complete the system I want to have  :grin:

---

### Post by matthew on 2005-08-17
I had a similar problem...different printer, but same manufacturer and mine is also an all-in-one so the solution might be the same. Here's a link to the thread with the solution that worked for me.

[http://www.ubuntuforums.org/showthread.php?t=49288](http://www.ubuntuforums.org/showthread.php?t=49288)

Hopefully that will help you as well.

---

### Post by FCM on 2005-08-17
Thanks for the link - now I have Xsane up and running but I am unable to set up the printer! Working my way through System -> Administration ->  Printing tells me I have the officejet but it doesn't list a driver for it. The list of printer drivers doesn't show the officejet so how do I access the hplip driver (or should it be hpijs?) - neither of them show up to be applied. Hope this makes sense  :) 

So close.....

Chuck

---

### Post by matthew on 2005-08-17
1. Go back to System -> Administration -> Printing again. 

2. Right click on the icon for your printer and select "properties" from the dialog box that comes up.

3. Select the tab that says "Driver" and look at the bottom of the box. 
You should see: Driver: <pull down box with a driver listed> <button for install driver>  Is the hpijs driver listed there? 
If it is not, close the printer properties box and find it in Synaptic and install it. 
If it is, move to #4

Edit: you asked if the driver should be hpjis or hplip and I didn't answer you. Sorry. You need hpjis.

4. In the middle of the printer properties dialog is a list of Models: I just looked in mine and approximately 3/4 of the way down I see OfficeJet 4200 listed right between Office Jet 4115 and OfficeJet 500. Select it and print away!

---

### Post by FCM on 2005-08-17
No luck Matthew. I installed the hpijs driver and followed your directions. The problem may be caused by the fact that I removed the printer before installing  hplip. Now when I try to add a new printer I can see that it knows about the oj 4200 but it won't display the driver hpijs for installation.

I'll redo everything and see what happens. Thanks for your help.

Chuck

---

### Post by Richard Perry on 2007-03-14
I would like to start a new thread, but I can't find a way on the forum.  There must be a way but it is neither obvious nor intuitive.  If somebody could kindly point the way I would be grateful.

I have an HP officejet 4215xi all in one.  On the System Settings, Computer Administration, Printing, the printer is not listed.  The only listings are for various print to files and print to fax; no printers.  When I go to Administrator Mode HP 4215xi is listed first.  I can do a successful print test from that location.

When I go to a program such as OO Writer or Kate and try to print, I get a message that it is printing to either generic or default.  It then says "print error" and quits.

How can I get this printer to work?

I am using Kubuntu with KDE.

I've tried all the previous fixes and none have worked.

Thanks in advance.

---

