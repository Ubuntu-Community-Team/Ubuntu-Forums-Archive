---
title: "ATI Video Driver Help.!"
date: 2010-11-13
forum: Hardware
---

### Post by jonathanbabb on 2010-11-13
Hi my laptops video card is below also using ubuntu 10.10. im been trying for days now and still nothing, i follow loads of videos tutorials still nothing follow loads of way to do it and all i get is error everywhere. i really would like some help, dont really want to back to window. thank you for you help


ATI DISPLAY DRIVER
Mobility Radeon 9000 IGP 
VERSION 8.033

---

### Post by mastablasta on 2010-11-13
you shouldn't install the driver form ATI site as it doesn't support the current ubuntu edition. you need to use opensoruce drivers.

what you could do is try to find a PPA for newer opensource driver.

---

### Post by chrisjbell on 2010-11-13
If you have a machine that has switchable graphics that is probably contributing to your problem. If you can set your display adapter to the ATI in BIOS then the driver install should work a lot better. I've been trying to find a solution for the switchable graphics thing on my HP laptop - but on HPs the BIOS doesn't let you set the display. (I don't want to hack my BIOS)

---

### Post by Decatf on 2010-11-13
The only driver available for that card is the open source driver which is already installed by default (ATI doesn't support this card anymore). More up to date version of these drivers can be obtained from the [xorg-edgers ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa"). Instructions on how to install this ppa are in the link. Are you experiencing a particular problem with the graphics as it is?

---

### Post by jonathanbabb on 2010-11-14
yes i have been having problems eg youtube videos pictures blocky and keep stoping, blus the os keeps crashing. im new to this os, whats open source?

---

### Post by jonathanbabb on 2010-11-14
if someone could help me i would really apreciated it, ive tried everythink, if someone can you can connect to me though remote connection to help thanks

---

### Post by mpnordland on 2010-11-14
have you tried using the additional drivers utility?
System>Administration>Additional Drivers
Also search for radeon in synaptic. If the xorg-radeon-driver package (or a package with a name like that) is installed then you have the opensource driver installed.
ps here is a description of opensource : [URL="http://en.wikipedia.org/wiki/Open_source"]http://en.wikipedia.org/wiki/Open_source
[/URL]

---

