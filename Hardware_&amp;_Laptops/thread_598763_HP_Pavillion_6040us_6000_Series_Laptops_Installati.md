---
title: "HP Pavillion 6040us 6000 Series Laptops Installation Instructions for Ububtu 7.10"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by thinkjones on 2007-10-31
This will be fairly short as the 7.10 installation went like a breeze on my laptop.

**Step 1 - Boot from CD**
After burning the CD boot from it.
At the installation screen select F6 and type "noapic", without inverted commas at the end of the command line.  This will boot up ubuntu ready for installation.

**Step 2 - Install**
When booting from the CD there is a desktop icon "click install"
Set up partitions
Install
Process takes about 10 minutes.

**Step 3 - Install Drivers Specific to the HP Pavillion system**
Here I got into a slight confusion partially due to my newness to ubuntu, but you will notice when you first install that you do not have wireless nor is the high resolution available because both the nvdia and broadcom drivers have not been installed yet.

Don't go searching on the internet for fixes for this, Ubuntu already has the solution built in.

First plug your laptop into the internet using an ethernet cable.

Then go to "Restricted Drivers Management" and enable the broadcom and nvidia drivers.

You will probably have to reinstall but after that the wireless options should be working and you can change your screen resolution to what you had in windows.

Then you can have fun enabling in the advanced graphics functions in the desktop panel. omg wow this desktop blows vista to shreds.

**Summary**
Easiest Linux to install yet.  If I were MS I would be scared.

---

