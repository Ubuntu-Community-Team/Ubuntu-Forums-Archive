---
title: "Ubuntu Install on Thinkpad X21 without USB/Floppy/CD-DVD ROM"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by gringe on 2009-06-02
Yeah its a big ask I guess, but spent ages consulting google.

I have an old IBM ThinkPad X21 laptop. I am trying to install Ubuntu onto it, but I don't have a built in CD ROM (only USB connected which fails) and it will not boot from USB.

I was hoping I could use my laptop HDD caddy to connect to my desktop PC, and install from there (a lightwieght version, or something just to get it to boot from th laptop hard drive then load the install ISO).

I did have Windows on the hard drive, but it died, so the hard drive tries to boot Windows, but fails.

Appreciate any help anyone may have,
thanks
Gringe

---

### Post by MichaelSammels on 2009-06-02
Hmm, you say it will not boot from USB? Have you tried plugging in yuor USB CD-ROM, entering the BIOS and making sure that the CD-ROM is set as the first boot device to try? Also, if you have say a USB Hard Drive, try this post:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by gringe on 2009-06-02
The problem I have is installing from a USB connected CD-ROM drive gets so far then it falls over (I am guessing its the part where it tries to install USB drivers perhaps??). The same applies if I try to install Windows on said laptop.

thanks for the link I'll take a look.

Regards
Gringe

---

### Post by Gabriel Bonilla on 2009-06-17
I had the same issue. The solution may suck a little but basicaly IBM (lenovo) has some patch for the BIOS of the x21 which runs on windows and updates the firmware. What I did was to install windows 98, I run the lenovo firmaware updates and then the laptop was able to boot from the CD.
 
You have to move the windows 98 installation files to the HD some how, I did it with the help of another computer and the external HD enclousure making it external HD usb.
 
After that you will be able to install ubunto without a problem. I have Ubuntu 9.

---

### Post by Iceman404 on 2009-07-11
do you happen to have a link to that BIOS patch? I've taken a look around lenovo's site but can't seem to find anything but the most recent BIOS revision 2.25 (which was 2003, lol)

---

