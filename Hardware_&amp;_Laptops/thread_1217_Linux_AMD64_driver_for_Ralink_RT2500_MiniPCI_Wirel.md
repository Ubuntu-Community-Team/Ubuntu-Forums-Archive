---
title: "Linux AMD64 driver for Ralink RT2500 MiniPCI Wireless Card"
date: 2004-10-19
forum: Hardware &amp; Laptops
---

### Post by ulefr01 on 2004-10-19
I am looking for a Linux driver Ralink RT2500 MiniPCI Wireless Card for an AMD64 processor.
Where can i find this driver ?
How can i install this driver ?

---

### Post by david.ballester on 2005-03-10
Late, but i'm trying to locate a good wifi chipset with opensource drivers an I have seen this few minutes ago. Seems to be an opensource driver for your wifi card ( And seems to get direct support from the manufacturer! ):

[OS ralink driver project](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)

---

### Post by Ambugaton on 2005-08-08
Thats exactly the driver I'm looking for. However, I'm having some trouble installing the module.

# $make install

doesn't work.  Ubuntu says that there are too few arguments...i'm such a n00b; sorry.

---

### Post by david.ballester on 2005-08-09
Read [this](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/) 

seems, by now, that you are executing **make install** when only **make** command ( **make** standalone without *install* ) is needed

HTH

---

### Post by Ambugaton on 2005-08-09
I'm still have some issues...I still can't get the damn thing to install. I'm following all the directions on the link you posted. rt2500.ko wont build so I can't really get past step 6.

---

### Post by Ambugaton on 2005-08-10
Hey guys, nevermind about any of that. Problem solved! I reinstalled Hoary and gave the driver install another go. Went ok. I started by getting the Linux Headers and then went on to do the rest of it. I left the CD in- I have no clue if that makes any difference but its the one thing I did differently and it worked! Everyone was really helpful, thanks a ton.  :)

---

### Post by Ambugaton on 2005-08-11
OK, stupid question but :???: ...
I've got the driver working but I need it to run on startup. How would I add it to the boot script? Thanks.

---

### Post by david.ballester on 2005-08-11
Is not necessary to place any command in scripts, once driver is installed every time that a device ( rt2500 wireless card ) is detected ( pcmicia, minipci, pci...) the kernel module is loaded automatically. 
If you wanna scan automatically for wireless points every startup, you can try the GTK Wifi Project ( gnome applet to wifi scans/info )

[gtk wifi project @ ubuntu forums](http://ubuntuforums.org/forumdisplay.php?f=74) 

HTH

---

