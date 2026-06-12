---
title: "Compaq F755"
date: 2008-03-15
forum: Hardware &amp; Laptops
---

### Post by gunbait101 on 2008-03-15
Alright guys, I'm new to Ubuntu (Linux in general) I was wondering if someone could guide me through the driver installation (Ubuntu is installed fine) with my Compaq Presario F755US Notebook, thank you in advance, I'll give you a list of all my stuff (I'll do my own research and help out getting drivers, the biggest one is the Wireless card, and Video drivers).


Wireless Card : Atheros AR5006X
Video/Chipset : GeForce 7000M / nForce 610M

Actually come to think of it, that is all I need for Ubuntu, I will continue doing research, but I thank you, if you help out.

Nick

---

### Post by NightwishFan on 2008-03-15
Wireless can be tough but the restricted drivers for graphics are 1 click away on supported cards. The kernel takes care of the rest.

---

### Post by gunbait101 on 2008-03-15
The restricted video drivers do not help. I really wish I could just get this stuff to work right!!! I've had so many problems with XP, and in hopes of getting Ubuntu to work, that was just a failed attempt....

the wireless card I'm yet to get working along with the video drivers...

---

### Post by NightwishFan on 2008-03-15
Did you use the restricted drivers manager or try the ones from nvidia?

---

### Post by gunbait101 on 2008-03-16
Both, it was a pain in the butt to find the drivers for Windows XP let alone Ubuntu.

---

### Post by NightwishFan on 2008-03-16
No for Ubuntu _most_ drivers are included or are in the repos. :)

Just go to the Restricted Drivers under the system menu and install one for your card. (If available)

---

### Post by teknotuck on 2008-03-22
I am trying to setup the exact same laptop. HP has done a great job of making something Ubuntu has issues with. The best video i can get trying every driver out there is 800x600 using the vesa driver.

Here is the relevent section of my xorg.conf for anyone having issues.

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:0:18:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection  
                Modes           "800x600"
        EndSubSection
EndSection

I have given up on the wifi because i had a zydas wifi dongle sitting around here and i got that working fairly painlessly. 

To anyone looking to buy this model of laptop, forget it, its a craptop.
Sure its cheap but at least at this point in time the nvidia drivers, including those from the restricted drivers repository, will only only give you 640x480. the ones off of nvidia's site are even worse and you will be stuck with only a command prompt.

This thing is worse than a Dell. If anyone is able to get something better than 800x600 please post it or if someone comes up with a solution for the builtin atheros wifi chip.

---

