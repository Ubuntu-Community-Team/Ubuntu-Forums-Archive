---
title: "Mode problems - no video"
date: 2012-08-04
forum: Hardware
---

### Post by gallinka on 2012-08-04
I am continuing my trouble shooting from a different thread: [http://ubuntuforums.org/showthread.php?t=2028877](http://ubuntuforums.org/showthread.php?t=2028877)

I am having problems getting video to display on a Axiomtek P2127-370.  This is an all-in-one industrialized PC.  It has an SBC8360 single board computer, 800x600 TFT LCD with an elo touchscreen (on com1).  My original problem had to do with installing Ubuntu 8.04 and getting a blank screen/over range message (on my monitor).  The SBC8360 has a VGA port that displays the same information as the LCD.  Using an external monitor on that port (also an LCD - 1280x1024 native) resulted in the same problem.  I eventually tried a second video adapter, a 3dfx Voodoo3 card, and was able to install Ubuntu.  That leads me here.  With much reading and working on the xorg.conf file I still cannot get anything to display on the "internal" LCD and cannot drive a resolution higher than 800x600 through the Voodoo3 card.  I have tried specifing a mode (as reported by the x server log) that is the native resolution of my "external" LCD on the Voodoo3 card with no success.  When I do (or otherwise get too creative with the xorg.conf file) X server loads a kind of safe mode and graphically tries to set up my video configuration.  If I exit this I can still load X normally.  My log file is quite different and may have useful information I just cannot decipher.  The SBC8360's on board video chip is a Chips and Technologies ct69000.  It has 2MB of ram and according to the "chips" driver info has a max mem clock of 135Mhz.

All of my current info is as follows.  Any help would be appreciated:

---

### Post by gallinka on 2012-08-04
Here are the log files.  The first is when X starts normally.  The second (falied) is when X does not like something I put in xorg.conf:


...looks like the files are too big.  I will attach them as .zip files:

---

### Post by gallinka on 2012-08-04
-SBC8360 single board computer:
-Celeron 850 mhz, 100 mhz FSB
-256 MB ram (1 GB ECC chip, recognized as 256 - tried ecc mem/no ecc mem in bios)
-Intel 440BX chipset (the SBC8360 has only one memory slot hence the 256mb ram)
-Chips and Tecnologies 69000 display chip (there is no seperate display adapter - SBC)
- 2mb video ram, max resolution of 1024x1280
-The SBC has several other integrated peripherals - 4 com ports, LPT, DIO, audio, LAN, etc

---

### Post by Nutria on 2012-08-04
> **gallinka said:**
> -SBC8360 single board computer:
-Celeron 850 mhz, 100 mhz FSB
-256 MB ram (1 GB ECC chip, recognized as 256 - tried ecc mem/no ecc mem in bios)
-Intel 440BX chipset (the SBC8360 has only one memory slot hence the 256mb ram)
-Chips and Tecnologies 69000 display chip (there is no seperate display adapter - SBC)
- 2mb video ram, max resolution of 1024x1280
-The SBC has several other integrated peripherals - 4 com ports, LPT, DIO, audio, LAN, etc

Pretty ancient.  This computer is on a factory floor or something?  What will you be doing with it?

Anyway, I'd try a minimalist (but not too minimal!) Debian text installer and also Damn Small Linux.

---

