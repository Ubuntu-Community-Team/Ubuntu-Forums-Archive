---
title: "Scanning for Canon ImageClass MF4770n on Ubuntu 12.10"
date: 2013-06-22
forum: Hardware
---

### Post by xXbrownbearXx on 2013-06-22
Hi all,

I am very new to Ubuntu and this is my first post on Ubuntuforums.org.  I'm trying to get my Canon MF4770n to scan documents.  I was successful to install the printer drivers (Linux_UFRII_PrinterDriver_V260_uk_EN).  However, I was unsuccessful to get the sanner to work.

I am currently using:
- Ubuntu 12.10
- HP G56 Laptop
- Canon ImageClass MF4770n 
- USB cable to connect to the printer

Thanking you in advance for your assistance.
Cheers!

---

### Post by pdc on 2013-06-23
SANE is scanning for linux;

[http://www.sane-project.org/](http://www.sane-project.org/)

in supported devices, Canon

[http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)

if you search on ImageClass devices, they seem to be working: "complete" with the backend of [COLOR="#EE82EE"]pixma[/COLOR] and the man-page [COLOR="#EE82EE"]sane-pixma[/COLOR]

..............so with Sane installed; and the front-end of X-sane installed, it .............should ...................work.........

what happens when you open xsane? (If you have that installed?)

commands in the terminal would be

> [COLOR="#FF0000"]sane-find-scanner[/COLOR]

and 

> [COLOR="#FF0000"]scanimage -L[/COLOR]

and if no response, repeat the commands prefaced by sudo ie sudo sane-find-scanner

---

### Post by CobaltSS on 2013-12-01
I am also having a problem with the same printer Sane detects it but when trying to scan says Device is busy. I've tried with sudo same error. Rebooted, powercycled printer, rebuilt backends manually, same error keeps popping up. Tried from flatbed and feeder, it will also detect if something is in the feeder if you select scan from feeder but always same device is busy error. I can confirm scanning works in Windows.

Any help would be appreciated.
Thanks.

---

### Post by CobaltSS on 2013-12-02
i'm an idiot. i retested in Windows and wouldn't scan i cycled through the buttons and it only scans if scan button on printer is pressed. must've had this pressed the first time i tested with windows. tested again with ubuntu and great success with both flatbed and feeder!

---

### Post by CobaltSS on 2014-08-02
Per request here are the instructions to get the scanning working on a Canon ImageClass MF4770n (Note: I have combined various sources to create this easy to do list)


 1. Compile Sane From Source
----------------------------------

You need at least sane version 1.0.24 to support the ImageClass MF4770n.
Ubuntu 14.04 ships with 1.0.23. The latest version of sane to date is 1.0.25


Tools to compile from source
---------------------------------
sudo apt-get install libusb-dev build-essential libsane-dev


Install git-core
-----------------

sudo apt-get install git-core


Download latest sane source code
------------------------------

git clone git://git.debian.org/sane/sane-backends.git

cd sane-backends

./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var

make

sudo make install



2. Set Permissions for USB (allows you to scan without using sudo)
------------------------------------------------------------------

This was tested on Ubuntu 14.04 not sure if rules file differs on 12.04

sudo gedit /lib/udev/rules.d/50-udev-default.rules

Change..
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", ... , MODE="0664" 

To.. 
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", ... , MODE="0666" 

Reboot.

sane-find-scanner
(Scanner should be listed)

scanimage -L

If fails try.. sudo scanimage -L

If it finds your scanner then rules file differs for your version.

If either work then

Make sure printer is set to Scan > Remote Scan

scanimage --test or sudo scanimage --test

Should now perform a successful test scan.

Install xsane or simple scan from repository for a GUI interface.

Just make sure to set the printer set to Scan > Remote Scan. (This only needs to be done when scanning in Linux.) 


3. If it still fails, check to make sure Sane back-end versions match...
-----------------------------------------------------------------------------------

If permissions not set you may need to use sudo for some commands.

$ scanimage -V
Should output: scanimage (sane-backends) 1.0.25git; backend version 1.0.23

As previously stated, both versions should match and be at least version 1.0.24

If you got to this point, sane installed correctly but is still linking to 1.0.23.
To correct this we can delete or in this example move the old version.

cd /usr/lib/x86_64-linux-gnu/
sudo mkdir old
sudo mv libsane.a libsane.la libsane.so libsane.so.1 libsane.so.1.0.23 old/
sudo mv sane old/

scanimage -V
Should output: scanimage (sane-backends) 1.0.25git; backend version 1.0.25

scanimage -L
Should now successfully find your scanner.

Make sure printer is set to Scan > Remote Scan

scanimage --test

You should now have your MF4770n working successfully.

---

### Post by PhDLinux on 2014-09-22
Thank you very much for these detailed instructions. They worked for me on Ubuntu 14.04. I had to do everything, including the steps in Part 3 to match the front-end and the back-end. Your generous post has saved me hours.

---

### Post by CobaltSS on 2015-05-07
No problem glad to help. You'll be happy to know that in Ubuntu 15.04 this printer is well supported, no config necessary.

---

### Post by Jim_Witterschein on 2015-09-15
I, too, would like to add my sincere thank you to CobaltSS for his 100% accurate, very detailed instructions.  Where I had previously installed the Canon MF4770n on Linux Mint 17.1, it was problematic and didn't always work -- either printing or (and particularly with) scanning.  I followed your instructions to the letter and my Canon MF4770n now works flawlessly.  Thank you very much Sir!

---

