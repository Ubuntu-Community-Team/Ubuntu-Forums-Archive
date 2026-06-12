---
title: "Brother HL-3070CW"
date: 2010-03-05
forum: Hardware
---

### Post by demoric on 2010-03-05
I have now spent the better part of 2 days trying to figure out HOW to get the printer setup for wireless and wired connections.  I'd get it running then try to install on another computer only to find it not working in that environment.  After alot of trial and error I found out how to network it in either environment.  In this mini-tutorial I'll hit most of the major steps but I'm going to gloss over some of the smaller things like getting your ip address, and navigating the printers web interface.

==== mini-tutorial ====

Download foomatic to remove any old printers. In a terminal type
*sudo apt-get install foomatic-gui*
then type:
*sudo foomatic-gui*

Get the linux drivers from brother [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

Download and install lpr driver .deb
Download and install cups wrapper .deb

Connect printer physically to LAN using Cat5e cable connection
Open your browser and type that IP address in.
Change IP to a static address using the web interface for your printer

In ubuntu:
Administration -> Printers
Server -> Add Nework Printer
Select Device -> Network Printer
Choose the device showing the physical IP
**!!!IMPORTANT!!!  Change Connection Type to LPD network printer via DNS-SD before hitting forward.**
[I]
NOTE: The same setup can be used for WLAN neworks.[/I]

===============

I hope this helps someone else.


========================================
NEW PROBLEM

After installing and having the printer work fine I waited 24 hrs.  Now when I print I get a message saying its not connected.  HOWEVER if I wait 10-15 minutes it'll print, OR if I remove and do the setup routine again its instantaneous.

I tried using the printer troubleshooter and the test page in cups prints instantaneous.  I'm at a loss here.

---

### Post by Mr.SASQUATCH on 2010-04-21
Thank you very much, works perfectly now! 

:)

---

### Post by wkulecz on 2010-08-22
Here is how I installed the HL-3070CW on Ubuntu 10.04 64-bit as a networked printer.

Download the two deb files from the Brother web site:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

hl3070cwcupswrapper-1.1.1-4.i386.deb
hl3070cwlpr-1.1.1-4.i386.deb

Connect to the printer with your web browser and set it for static IP on an address that is not in the range of DHCP settings on your router.  I set wired and wireless to the same IP as the printer only allows one to be active.  Get it working wired first and then sorry about wireless, way less headaches in the long run.  After it reboots verify its on the new address, the auto redirect from the rebot should recconect it in your browser once you click "apply"


They don't have 64-bit drivers so make sure you are setup for 32-bit lib compatability

Do sudo -i and change to the directory where you downloaded the two files and give the command:

dpkg -i --force-all *.deb

Ignore all the errors and when it completes open System->Administratin->Printing.

Delete the printer it has installed.  It is using some lpd deamon url, which I expect you can make work if you really want this and know what your are doing, but since you are reading this, forget about this and do it the easy way using the features you've paid for when getting the CW model!

Click on the add printer button and select Network Printer HP Jet Direct.  Put the static IP you assigned your printer in the box (the default port 9100 is correct) and fill in the names as you wish and click OK.

Print a test page and be happy!

Print quality blows away the Samsung CLP-300 this replaces, especially for photos, not that its a photo printer but its very usable "Sunday Supplement" color quality on plain laser paper.

HTH.

---

### Post by demoric on 2010-08-22
I forgot to reply back.  The delay in printing wasn't a driver issue but an issue with how pdf files were processed.

---

### Post by arungoyal on 2010-09-12
Easiest way to connect the wireless printer is to use cable directly to the wireless router and use the instructions on the disc. 
I initially tried to connect using network cable to the computer which did not work.

---

### Post by frogotronic on 2011-01-11
Hello,

  I just bought this printer and installed it.  I am using Karmic Koala (9.10) x32.  I followed the instructions exactly as they appeared on the Brother website, including doing all of the twelve pre-install steps.  Then installed the drivers (downloaded from the website).

  One thing I did do, is set the IP address of the printer to "Static".  This was achieved by logging into the web administration of the printer (**login:** *admin* , psswd: *access*) and changing TCP/IP Settings to "Static".

  After installing the printer, I right-clicked on the printer, chose Properties and then changed the connection to LPD.  Then selected "Detect" and then selected "Apply"

  Nothing could be simpler.

  BTW:  I called Brother technical support and they said that I could set the printer up using HP JetDirect if I wanted.  Actually, Brother were _**excellent**_ for tech support.

- CH

---

