---
title: "Lexmark Pro905 driver errors"
date: 2011-09-29
forum: Hardware
---

### Post by mscout2004 on 2011-09-29
Lexmark Pro905 got drivers from lexmark web site did the sudo command to run in terminal now getting error:

Lua error detected: While parsing install.lua: config/run.lua:1476: attempt to index global 'ownhership' (a nil value


HELP PLZ need my printer. Using Ubunutu 11.10 x64

---

### Post by dino99 on 2011-09-29
found that:
[http://ubuntuforums.org/showthread.php?t=1419642&highlight=lexmark+root](http://ubuntuforums.org/showthread.php?t=1419642&highlight=lexmark+root)

and you can ask their support here:
[http://support.lexmark.com/index?locale=EN&page=product&userlocale=EN_US&productCode=LEXMARK_PLATINUM_PRO905](http://support.lexmark.com/index?locale=EN&page=product&userlocale=EN_US&productCode=LEXMARK_PLATINUM_PRO905)

just seen you run 64 bits, comments found on Phoronix:

What makes it more difficult to install the 32-bit driver on 64-bit Linux is that Lexmark wraps their package (with Ubuntu, the Debian package) within a Loki/Mojo installer. When the installer detects you are on 64-bit Linux, the installation fails. However, this is an unofficial workaround for this as reported by one of the Lexmark engineers.

    Prerequisite packages: ia32-libs, openjdk-6-jre

    1. Get the latest driver
    2. Untar driver
    3. run in terminal "./lexmark-inkjet-09-driver-1.5.i386.deb.sh --noexec --target lexmark"
    4. a "lexmark" (from --target) directory was created, "cd lexmark"
    5. run in terminal "tar xvf instarchive_all --lzma"
    6. run in terminal "dpkg -i --force-all lexmark-inkjet-09-driver-1.5-1.i386.deb"

Those are the steps to extract the Debian package manually and then force its installation on 64-bit Ubuntu. These steps worked just fine for us with Ubuntu 9.10, but it is rather unfortunate that in 2010 Lexmark still does not have any x86_64 drivers available.

of course adapt to the updated  driver

---

### Post by mscout2004 on 2011-09-29
Already saw other post didnt help with this error. already was using the sudo command in terminal. have talked with tech support and they were no help

---

### Post by dino99 on 2011-09-29
have added comment above

---

### Post by mscout2004 on 2011-09-30
finally got the drivers installed but still cant print to it or even see it from the ubuntu session. can get to the back end from a browser and can print to it from another ubuntu pc on my network but this one will not see it. cant find a GUI to make it see it either. in 11.04 there was a GUI for the printers but I cant find it  since i did the upgrade to 11.10

---

### Post by greyghost60 on 2011-10-18
My Pro905 drivers work! after upgrading to 11.10 I deleted all the Lexmark  items using Synaptic downloaded the driver from the US site and followed the instructions

Running  ./lexmark-inkjet-legacy-wJRE-1.0-1.amd64.deb.sh gave me a graphical package and installed the printer, or so it seemed 

The only trouble is that it will only work in wireless mode. It's fine and scans and prints perfectly but when connected via a usb port it gives a 'can't connect to printer error' 

lsusb gives 
 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 002: ID 046d:09a4 Logitech, Inc. QuickCam E 3500

Bus 001 Device 003: ID 0d49:7410 Maxtor Mobile Hard Disk Drive (1TB)

Bus 001 Device 004: ID 043d:0185 Lexmark International, Inc. 

Bus 001 Device 006: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer

Bus 004 Device 002: ID 056a:0018 Wacom Co., Ltd Bamboo Fun 6x8


and all the other usb connections work.

Any thoughts would be welcome but the driver does work :confused:

---

### Post by mscout2004 on 2011-10-18
I did get the driver to work they had to correct a typo they had in the driver.

GreyGhost60 with the USB problem are you using a usb hub of any kind when you are plugging in the printer? The Lexmark printers don't like being on a hub or the front ports of a PC. They really don't even like expansion cards either. They need to be solo in one of the main ports on the motherboard.

---

### Post by mörgæs on 2011-10-18
Moved to Hardware and Laptops.

---

