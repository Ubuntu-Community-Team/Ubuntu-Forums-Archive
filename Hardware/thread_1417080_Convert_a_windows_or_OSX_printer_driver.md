---
title: "Convert a windows or OSX printer driver?"
date: 2010-02-26
forum: Hardware
---

### Post by Lorefanatic on 2010-02-26
Strange question. I have a Kyocera FS-C1020MFP printer, and it's one of the few printers that Kyocera doesn't produce a Linux driver for. They (obviously) have Win-based drivers, and even have an OS-X driver for it, but no Linux drivers. 

Is there any way to convert a Win driver or a Mac driver to Linux.

PS - currently running new install of karmic.

Thanks!

Bryan

---

### Post by MS-Hater on 2010-02-26
Have you tried hooking it up and seeing if Ubuntu recognizes it, and can use it? For the record, there's no way to convert a driver from any OS to another; you'd need the souce code, and the ability to build it (the driver) as a module. I'd try plugging the printer in and seeing if it works first, though... If that fails, get in touch with the tech support for your printer, and see if they'll email you the souce code for compiling the driver. Once you have that, you should be able to build it and install it.

---

### Post by Lorefanatic on 2010-03-03
It seems like the generic postscript drivers are working for it, although I've lost much of the functionality. No go on getting the source from the manufacturer, however I've at least put a couple requests in - so lets see if their devs will do it. Here's hoping...

---

### Post by lykwydchykyn on 2010-03-03
OSX also uses CUPS for printing, so it might work if you can get the .ppd file from the OSX driver.  If it requires special binaries, then it probably won't work.

---

### Post by tgalati4 on 2010-03-03
Not only does Apple use CUPS for the mac printing framework, they purchased it!  So if you have a fully-functioning mac driver, then you may be able to use the *.ppd file in Ubuntu CUPS.

First, find a mac user and hook up your printer.  The OS X tends to install the printer automatically.  See what features are available.  It's possible that the mac driver is using a generic PDF driver as well.  So if you don't get extra functionality under OS X, then it will be difficult to get those features in linux with out a proper driver.

Send an email to Kyocera asking when will they provide a linux driver.  Post their response.  

Sell it on craigslist and get a replacement printer that is supported.

---

### Post by thodpol on 2010-06-15
I know that this thread is probably inactive but I just bought an FS-1020MFP and made it print. So in case someone has the same problem this might be helpful.

I have already connected the device with the ethernet interface, switched it on and gave it a static IP.

I use kubuntu 10.04 so I navigated to 
System Settings --> Printer Configuration --> New Printer --> New Network Printer.

I waited some seconds until the printer was located, I selected it, pressed forward and in the driver selection window, there is an option that says "*Provide PPD file*" 

You can find the .ppd file in the cd that they provide (it is available in their site as well). Navigate to the file:

*PrnDrv/PS/XP_VISTA/ENGLISH/DISK1/K8EP.ppd*

I guess that there is a similar wizard in ubuntu/gnome where it asks for the ppd file. I know this is not the right solution because I do not know if the windows .ppd driver has any difference from the linux driver, but at least it worked for me.

I am still trying to use the scanner through ethernet with xsane but without success. I cannot even find a driver for scanning using the usb connection.

---

