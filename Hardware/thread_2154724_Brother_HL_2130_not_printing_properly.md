---
title: "Brother HL 2130 not printing properly"
date: 2013-06-15
forum: Hardware
---

### Post by todaymueller on 2013-06-15
[FONT=Verdana][SIZE=2]I have just bought a Brother HL 2130 printer. I have followed the instructions for installing the driver and although it has printed some documents ok. Others have taken an age to print and some have printed the top third on one sheet and then after a wait the bottom 2 thirds on another. Any ideas on whats going wrong?   [/SIZE][/FONT]

---

### Post by todaymueller on 2013-06-16
[FONT=Verdana][SIZE=2]I just installed the printer on a non Ubuntu PC and it printed fine. I tried printing on the Ubuntu PC earlier, nothing complicated just 2 sheets of music score, and after 30 minutes of processing ie the the print queue dialog box saying it was proccesing and the green light flashing on the printer indicating proccesing I canceled it. I am wondering if it is a usb issue as my external hard drive is also excrusiatingly slow and prone to errors.  [/SIZE][/FONT]

---

### Post by kurt18947 on 2013-06-16
I'm not sure if this will help you but it helped me.  What driver for the HL2130 are you using?  I have an MFC-7820n which installs brscript by default.  It was sorta slow on the first page and slower yet on 2nd and subsequent pages (maybe 2 pages/min).  I found a CUPS driver for my machine via Synaptic and installed it.  MUCH better, speed is equivalent to Windows.

---

### Post by pdc on 2013-06-16
It is not clear what driver you have installed; could you please post back what 

> [COLOR="#FF0000"]sudo dpkg -l | grep Brother[/COLOR]

gives....if you copy and paste the above command into a terminal; 

also: is your system 32bit or 64bit

(I ask the above questions as Brother provide drivers and alternately: Kurt says there are CUPS drivers)

.........also .....if you choose the Brother route: you can either install the drivers yourself; or let the Brother install script do all the work)

---

### Post by kurt18947 on 2013-06-16
> **pdc said:**
> It is not clear what driver you have installed; could you please post back what 



gives....if you copy and paste the above command into a terminal; 

also: is your system 32bit or 64bit

(I ask the above questions as Brother provide drivers and alternately: Kurt says there are CUPS drivers)

.........also .....if you choose the Brother route: you can either install the drivers yourself; or let the Brother install script do all the work)

The Brother provided script does seem to work very well.  It is a bash script run from a terminal.  Here's a link:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

---

### Post by todaymueller on 2013-06-18
[FONT=Verdana][SIZE=2]Thanks for the replies guys. I am running 32 bit version of precise pangolin LTS.
It says I am running a brother driver - ii  printer-driver-ptouch                         1.3-3ubuntu0.1                                  printer driver Brother P-touch label printers-
 How do I change to a cups driver? [/SIZE][/FONT]

---

### Post by kurt18947 on 2013-06-18
> **todaymueller said:**
> [FONT=Verdana][SIZE=2]Thanks for the replies guys. I am running 32 bit version of precise pangolin LTS.
It says I am running a brother driver - ii  printer-driver-ptouch                         1.3-3ubuntu0.1                                  printer driver Brother P-touch label printers-
 How do I change to a cups driver? [/SIZE][/FONT]

ptouch? That doesn't sound much like a laser printer.;)   IMO one of the shortcomings of Unity/Gnome-shell is printer administration.  The current app is a dumbed down version of the older app which is still used in Xubuntu and I think Lubuntu.  Fortunately, the older better app can be installed from the repositories.  It's called "system-config-printer".  It can be called from a terminal if it isn't on the dash.  The title at the top of the window is 'Printers-localhost' as opposed to just 'Printers' on the newer 'simpler' one.  Right-click the printer's icon and select properties.  If you need help from there, feel free to ask.

Some people run generic HP5(e?) laser drivers on Brother lasers and report it works fine.  If you want to use Brother's driver, go to Brother's page found here:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2170W](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2170W)
There is a link for instructions as well.  Be aware that Brother relies on command line interface rather than GUI.  You're fortunate to be using a 32 bit O.S.  All Brother drivers afaik are 32 bit and 64 bit O.S.s require a little more playing.  I suspect you could just download the two .deb files and install them from Ubuntu Software Center or or method of installing .deb files.  Software Center will probably complain about the quality of the .deb.  I ignore it and click install anyway.  There's a bunch of "before you install" stuff on Brother's site.  It appears most of it is obsolete, no longer required with newer Ubuntus.

Having said all that, if you're comfortable with CLI and bash scripts, the Brother provided one sure seems to work pretty well.  Worst case IME you may have to correct the device URI after installation finishes.

P.S.  One thing - if you install the Brother drivers, be sure to install the LPR driver before the CUPS driver.  You want both and in that order.

---

### Post by todaymueller on 2013-06-18
[FONT=Verdana][SIZE=2]I have installed different drivers and it seems to be working fine :D  I will have to give the printer a good work out over the next few days....I shall report back.[/SIZE][/FONT]

---

### Post by kurt18947 on 2013-06-18
> **todaymueller said:**
> [FONT=Verdana][SIZE=2]I have installed different drivers and it seems to be working fine :D  I will have to give the printer a good work out over the next few days....I shall report back.[/SIZE][/FONT]

Yes please!  If things continue to work properly, could you mark this thread 'solved' so others searching can benefit?

---

### Post by todaymueller on 2013-06-29
OK, I have given the printer a good work out and it seems to be working fine.

---

