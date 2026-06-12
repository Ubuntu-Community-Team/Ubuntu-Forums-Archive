---
title: "Epson Stylus RX595"
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by gengle77 on 2008-02-02
I'm trying to install this printer on Gusty Gibbon 7.10. The drivers are there and its printing fine. The problem is getting it to scan. I've tried everything from the forums to get Image Scan to work but to no avail. The kicker is I had it working fine with Image Scan but just recently upgraded my computer and cant find the original steps that worked for me. Any help would be great. Thank you.

---

### Post by cotcot on 2008-02-02
Check if you have the epkowa driver :

The file /etc/sane.d/dll.d/dll.conf must be modified by deleting “epson” and adding “epkowa”. Otherwise sane will be confused because of seeing 2 drivers at once.
Code:

> sudo gedit /etc/sane.d/dll.conf

---

### Post by gengle77 on 2008-02-04
I have downloaded the driver from Avasys, but I need to know the exact steps from there. When trying the advice from the forums it seems to never work. I know theres something out there that works cause I had it working  before. Im going to do a fresh install of Ubuntu 7.10 Tuesday night and try again. I tried so many things in Terminal, and changing files I would feel more confident with a fresh install, and I have a new video card coming and have to add a promise card. Thanks

---

### Post by gengle77 on 2008-02-09
Okay I got to work. There were two in the /etc/sane.d/dll.conf. There was epson, and epson2 I deleted both. Made sure there was epkowa which there was tried it and it worked.Thanks for the help.

---

### Post by stormlongfella on 2008-07-01
Ok...This is what I did to get the scanner portion of my RX595 to work on ubuntu 8.04.  The Printer worked from the start so I did no changes to it. After 3 days of searching and googling this is what I came up with.

Steps:
   *$  sane-find-scanner*

write down the product and device id 

   *$  sudo gedit /etc/sane.d/epson.conf*

add product and device id to the usb section in /etc/sane.d/epson.conf file. also uncomment(delete #) "usb /dev/usb/scanner0" found at the bottom of the file.

   *$  sudo gedit /etc/sane.d/dll.conf*

Next make sure /etc/sane.d/dll.conf lists epson and epson2 is deleted or make sure it has a # in front of it.

Restart the computer,and your scanner should work now.

Now I would like to get the CD printing portion working...If anyone has some suggestions please let me know.

---

