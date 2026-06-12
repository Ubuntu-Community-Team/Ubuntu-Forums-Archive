---
title: "I cannot find a driver for a Brother MFC 790CW Ver.1.02 en-US"
date: 2014-03-25
forum: Hardware
---

### Post by Antonio_Sheister on 2014-03-25
I need help finding a driver for my printer, its a Brother MFC 790CW Ver.1.02 en-US.  Please help if you can.

---

### Post by kurt18947 on 2014-03-25
Here's the driver & instructions.  

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-790CW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-790CW)

My experience is that with newer Ubuntu distros you can pretty much ignore the 'pre-install' stuff.  I believe you still need to install both the lpr & CUPS drivers even though it says the CUPS driver is preferred.  I've not done a manual install in some time.  I've had very good success using the installer script mentioned here:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

The most difficult part for me was figuring out how to download the script.  There is a successor script (2.0,0,x) that will download the scanner driver as well but that one seems hard to find.

You might find this thread helpful if you're going to install the scanner driver even though it doesn't directly address your machine.

[http://ubuntuforums.org/showthread.php?t=2209429](http://ubuntuforums.org/showthread.php?t=2209429)

There are two glitches mentioned with the scanner portion.  The scanner fix varies with what scanner driver is correct,  brscan, brscan3 etc.  The script that installs the printer driver does not address these issues.

---

### Post by Antonio_Sheister on 2014-03-27
Im new to linux so when you say cups and stuff like that im lost but im gradually learning just by messing around

---

### Post by pqwoerituytrueiwoq on 2014-03-27
basically download and install the debs, i would think that should get the job done (i hope they work on 64bit)
if you don't understand save this code as a file
```
#!/bin/sh
wget http://www.brother.com/pub/bsc/linux/dlf/mfc790cwcupswrapper-1.1.2-2.i386.deb
wget http://www.brother.com/pub/bsc/linux/dlf/mfc790cwlpr-1.1.2-2.i386.deb
sudo dpkg -i ./mfc790cw*-1.1.2-2.i386.deb
sudo apt-get -f install
```
open a terminal emulator window and type sh and a space ("sh " without quotes)
drag and drop that file you saved into the terminal and press enter
type password when asked and press enter (ignore the fact that you don't see dots or asterisks, it is a security feature)

---

