---
title: "The True Working Install Of Lexmark Printer Drivers On Any Linux On Any Architecture"
date: 2010-05-08
forum: Hardware
---

### Post by bearsomg on 2010-05-08
I had been having problems getting my lexmark 2600 series printer to install on my Ubuntu 64 bit machine, but I have finally found out how. 

Step 1: Download the Drivers

[LIST]
[*]Go To [www.lexmark.com]("http://www.lexmark.com")
[*]Find Your Printer
[*]Click On Drivers and Downloads
[*]Click on the Unix tab
[*]Download the one for debian based systems, not the rpm one
[*]Extract the archive
[/LIST]
Step 2: Get the Deb file

[LIST]
[*]In a terminal, go to the folder in which you downloaded the driver, and run
[/LIST]
```
sudo ./lexmark-08z-series-driver-1.0-1.i386.deb.sh
```
[LIST]
[*]Once the installer opens, DO NOT close it. Instead, open a new terminal and move to the temp folder.
[*]Find a folder named selfgz13696 or something like that. Go into it.
[*]Run
[/LIST]
```
sudo ./startupinstaller.sh
```
[LIST]
[*]Go through the installer , and it will give you an error about either CUPS or it will just say failed to install. DO NOT CLICK OK ON THIS WINDOW
[*]Leave the installer and linked terminal alone, and with the native file browser for your linux system, go to the temporary fodler you went to previously.
[*]Once again, go into selfgz13696 except this time you will find a file named arch.tar
[*]Copy that file to your desktop
[*]Extract the archive on your desktop to find the deb package for the driver.
[*]Go into a terminal, cd to your desktop, and run the command
[/LIST]
```
sudo dpkg -i --force-architecture lexmark-08z-series-driver-1.0-1.i386.deb
```
[LIST]
[*]Plug in your printer to have your computer automatically install the driver for you. If it does not, you should be able to find it in the driver list.
[/LIST]


**Remember, the driver files that I used might not be the names of the ones you have. Substitute the file names I used** [B]with the ones that correspond to your files.


YOUR PRINTER MUST HAVE A LINUX DRIVER IN ORDER FOR THIS TO WORK
[/B]

---

### Post by lanceman63 on 2010-05-10
When I went to the Lexmark website I found my printer (x7350) and there is no Linux tab or reference to any Linux distros on the page for my printer.

---

### Post by bearsomg on 2010-05-11
That printer has apparently been discontinued for driver development. I think that there might be a way to fake it with another driver version for another printer, but I'm not sure.

---

### Post by cookingrock on 2010-05-11
This WORKED for my X7675 multifunction, although the Ubuntu box has to be attached to the printer via USB. I don't mind, though. I'm simply thrilled to have a reliable printer again. 

Thank you!

---

### Post by sideburns on 2010-05-12
We managed to get a new Lexmark printer installed on my sister's box without going through that.  However, even after enabling the printer and setting it as default, it doesn't print.  It works fine as a copier, but if you try to print, the output acts  like it's been directed to /dev/null.  Any suggestions?  (Yes, we do have the proper driver selected for it.)

---

### Post by Linux_junkie on 2010-05-12
About 6 or 7 years ago I bought a lexmark printer and tried to install it on my Mandrake Linux machine but even after downloading the correct driver I could not get the printer set up so in the end I bought an HP printer which worked straight away (once I downloaded its driver).  Never bought another Lexmark since and never intend in the future.

---

### Post by bearsomg on 2010-05-13
> **sideburns said:**
> We managed to get a new Lexmark printer installed on my sister's box without going through that.  However, even after enabling the printer and setting it as default, it doesn't print.  It works fine as a copier, but if you try to print, the output acts  like it's been directed to /dev/null.  Any suggestions?  (Yes, we do have the proper driver selected for it.)

I suggest uninstalling everything, including the drivers you downloaded. Then follow the tutorial I gave, to re-install it. Your problem is the fact that with the driver not interfacing with the printer. This can happen on 64-bit machines, and I had the same problem until I figured out how to solve it. Also, copying does not go through the driver at all, it all runs inside of the printers firmware.

---

### Post by sideburns on 2010-05-13
What makes you think we're using a 64-bit version of Ubuntu?

Also, I've done some more checking: the drivers we downloaded did not include one for the model we have, which is odd, because it seems to be a fairly new model.  Thus, I find it Highly Unlikely that your suggestion would work in this case.  I've asked a support question at Lexmark, and will follow their advice.

---

### Post by 504harry on 2010-06-10
I'm hoping bearsomg (or anyone else?) is able to advise - I've seen Lexmark S305 with the Linux penguin, there are two drivers (along with much technobabble) on the Lexmark.com website...
1) for Fedora 10, OpenSuse11 (from reading yr helpful post, this is NOT the one Ubuntu needs..?)
2) for Debian package manager, the file is described as follows:-
lexmark-inkjet-09-driver-1.5-1.i386.deb.sh.tar.gz 
Is this correct for Ubuntu..? Lexmark doesn't mention Ubuntu.
Am I about to wreck my installation, or is this (at last) the possibility of using cheaper printers? The  S305 is a Printer/Copy/Scan and looks quite fair value, with 4-separate ink tanks, although I don't think these are "print-heads", just tanks. I'm slightly suspicious of their "return program" - looks like a scheme to make more profit.
(My first Lexmark is still OK after 10-years, it was bought because the cartridges contain the print-head so if you clog one up, buy a replacement and hey-presto virtually new printer.
In addition these cartridges can be refilled, having no "chip" issues. However, the Z51 has never worked with Ubuntu so I gave up trying.

Regards....

---

### Post by bearsomg on 2010-06-10
Ok, I'm not quite sure what the Firmware update is, but I looked at the page

[http://support.lexmark.com/index?page=recommendedDownloads&locale=EN&productCode=LEXMARK_IMPACT_S305&segment=DOWNLOAD&userlocale=EN_US#2](http://support.lexmark.com/index?page=recommendedDownloads&locale=EN&productCode=LEXMARK_IMPACT_S305&segment=DOWNLOAD&userlocale=EN_US#2)

and found that you need the 

[Linux  driver for Debian Package Manager based distros]("http://support.lexmark.com/index?page=content&productCode=LEXMARK_IMPACT_S305&actp=RECOMMEND&id=DR20547&segment=DOWNLOAD&userlocale=EN_US&oslocale=en_US&locale=en")

one. Follow my tutorial and it should get installed.

---

### Post by hackman17 on 2010-11-28
You said this works with any architecture but does this mean it works with PPC also??

---

### Post by bearsomg on 2010-11-28
Hmm, I'm not quite sure, but since this depends on the printer's capability to communicate with the os, it might work, but then again since it's technically a different version of the os then it might not, go ahead and try and tell me if it works, I'd be interested to know

---

