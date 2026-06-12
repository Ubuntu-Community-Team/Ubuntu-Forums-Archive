---
title: "Lexmark z810 printer cups driver"
date: 2007-07-20
forum: Hardware &amp; Laptops
---

### Post by g2g591 on 2007-07-20
i found a cups driver for my lexmark printer here  [http://cerqueira.org/software/z810/](http://cerqueira.org/software/z810/) and followed the installation instructions here [https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ810](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ810)
and i've hit a snage - tar doesn't seem to recognize the driver .tar.gz file and it quits. any one have any suggestions
EDIT:got it
EDIT:**does not seem to work on Gutsy**

---

### Post by phidia on 2007-07-20
> i've hit a snage - tar doesn't seem to recognize the driver .tar.gz file and it quits

What specific command is causing the problem and what is the terminal output?

---

### Post by g2g591 on 2007-07-21
hmm for some reason my install fails with error 1 even though my printer is on and connected.

---

### Post by g2g591 on 2007-07-21
output:
kyle@kyle-desktop:~/Desktop/Z810CUPS-0.7.1# /usr/sbin/lpadmin -x Z810 
Password for root on localhost? 
kyle@kyle-desktop:~/Desktop/Z810CUPS-0.7.1# sudo make install
Copying Lexmark Z810 files ...
Configuring system ...
Restarting CUPS ...
Adding Z810 printer queue ...
make: *** [install] Error 1

EDIT:**does not seem to work on Gutsy**

---

### Post by phidia on 2007-07-21
Have you gone to [www.linuxprinting.org](www.linuxprinting.org) and looked up the staus and how-tos for your printer?
i recommend it.

---

### Post by g2g591 on 2007-07-21
I got it working!! or at least the test page to print.....

---

### Post by Rotarychainsaw on 2007-07-22
Can you give more info on what you did? I have the same printer and have given up on getting it to work in linux.

---

### Post by g2g591 on 2007-07-27
Install required files:
sudo apt-get install alien
sudo apt-get install build-essential
sudo apt-get install libcupsys2-dev
sudo apt-get install libcupsimage2-dev
sudo apt-get install p7zip-full
 
Download actual driver files:
[this,]("http://cerqueira.org/software/z810/Z810CUPS-0.7.1.tar.gz")
[ and this]("http://www.downloaddelivery.com/webcontent/support/linux/z810llpddk-2.0-3.i386.rpm") (you must accept the agreement)
 
installation:
At first, install the Lexmark library. As it is delivered in [WikiPedia]RPM package format, convert it into a [WikiPedia].deb using alien. Then install it via dpkg.
 
sudo alien z810llpddk-2.0-3.i386.rpm
sudo dpkg -i z810llpddk_2.0-4_i386.deb
 
Now, extract, compile and install the cups driver:
 
7z e Z810CUPS-0.7.1.tar.gz
cd Z810CUPS-0.7.1
sudo make rpm-compat
sudo make
sudo make install
note: here it says the install failed but keep going
now move this Lexmark-Z810-lxz810cje-cups.ppd.gz from the z810 cups/system directory to the z810 cups directory
sudo /usr/sbin/lpadmin -p Z810 -E -P Lexmark-Z810-lxz810cje-cups.ppd.gz -v z810:/dev/usblp0 
 
these are slightly modified instructions - original (doesn't work) [here]("https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ810")
EDIT:**does not seem to work on Gutsy**

---

### Post by domino1241 on 2007-08-26
When I try the last step I get:

ryan@frank2:~/.z816/Z810CUPS-0.7.1$ sudo /usr/sbin/lpadmin -p Z810 -E -P Lexmark-Z810-lxz810cje-cups.ppd.gz -v z810:/dev/usblp0
lpadmin: Unable to open file "Lexmark-Z810-lxz810cje-cups.ppd.gz": No such file or directory

Could this be caused be one of the following:

[LIST=1]
[*]When I made the directory to install everything in, I called it .z816 instead of z810
[*]when I used alien, I used --scripts because I was getting a warning if I didn't use it
[*]The printer was not plugged in when I did this whole installation
[/LIST]

I have a feeling not plugging the printer in could have caused this issue, but how do I fix it?

---

### Post by g2g591 on 2007-09-02
you need the printer pluged in, I don't think the --scripts matters, directory name doesn't matter. You must move Lexmark-Z810-lxz810cje-cups.ppd.gz from ~/.z816/Z810CUPS-0.7.1/system to ~/.z816/Z810CUPS-0.7.1

---

### Post by appye on 2008-03-07
Anyone managed to get this running under gutsy?  I am reluctant to even try given all these EDITS.

---

### Post by mindhaq on 2008-05-06
> **appye said:**
> Anyone managed to get this running under gutsy?  I am reluctant to even try given all these EDITS.

This worked for me with Gutsy, and did again with Hardy.

Only thing is - Ubuntu auto-installs another 810_series printer as a text-only printer. Deleting it does not help, it gets auto-installed again after some time. But well...

---

### Post by randomerror on 2008-07-16
On Hardy I required libstdc++5 and the gcc-3.4 to get stuff compiled properly
> sudo apt-get install libstdc++5
> export CC=gcc-3.4

The linker complained about unresolved symbols while compiling the lexmark stuff with the default gcc-4.x and libstdc++6

Hope that helps...

---

### Post by randomerror on 2008-07-16
Oh, what I nearly forgot...

If you have installed the Photo-printing cartridge you might experience problems. I had to replace it with a plain black-color-cartridge to get usable results...

---

