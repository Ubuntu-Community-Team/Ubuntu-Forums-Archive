---
title: "How to HP C6150 with wireless network?"
date: 2006-12-30
forum: Hardware &amp; Laptops
---

### Post by bjgilger on 2006-12-30
Hi,

Santa brought a new HP Photosmart C6150 All-in-One with wireless networking (802.11g)

My previous printer was an HP 7110 OfficeJet all-in-one on a USB port. It worked fine.

Setting up the new C6150 as a networked printer at 192.168.2.2 (the assigned address shown on my Belkin wireless router) went ok except my Ubuntu box (6.10) doesn't talk to the new printer -- it won't print a test page.  ](*,) 

Any ideas?

TIA

John Gilger

---

### Post by zebulonevans on 2007-02-25
I just got this working.  I'm on Ubuntu 6.10.
Go to your printer and go through the menu and get the network settings to figure out the printers ip address.
Next open up a terminal and type
```
hp-makeuri 192.168.?.?
```
Replace the ? with the IP you got out of your printer.
Copy the CUPS URI which should be hp:/??
Now open up a web browser and go to: [http://localhost:631/admin](http://localhost:631/admin)
Select Add Printer
Give it a Name and Description
On the next page choose Device: Internet Printing Protocol (ipp)
Now past in the CUPS URI you got from hp-makeuri and hit continue.  Ignore that this format does not match any of the examples.
Choose Make: HP
Choose Model: HP PhotoSmart C6100
Wait a second at the added page and you will be taken to the configuration page.  Choose your paper type and save the settings.  Click on the printers tab and print a test page.

Congrats you have setup the wireless printer.

---

### Post by Madmoose on 2007-03-19
Hey!

This worked great! Thanks for the post!:KS

---

