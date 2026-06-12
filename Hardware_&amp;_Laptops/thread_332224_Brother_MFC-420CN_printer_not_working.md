---
title: "Brother MFC-420CN printer not working"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by Jesse121 on 2007-01-05
Hi all, I am trying to use a Brother MFC-420CN printer with Ubuntu v6.10 (64bit)
My printer shows up, but when I click "Print Test Page" the print job is immediately aborted. I have tried many things to get this printer working, here is what I have done so far in order:

Installed tcsh and csh:	Used Synaptic Package Manager

Installed LPR driver:  	sudo dpkg -i --force-architecture mfc420cnlpr-1.0.2-1.i386.deb

Created Symbolic Link: 	ln -s /etc/init.d/cupsys /etc/init.d/cups

Moved the driver file:	sudo cp /usr/share/cups/model/brmfc420cn_cups.ppd /usr/share/ppd/

Installed CUPS driver: 	sudo dpkg -i --force-architecture cupswrappermfc420cn_1.0.0-1_i386.deb

Tried copying the file which name starts with “brlpdwrapper” in the “/usr/lib/cups/filter” to the “/usr/lib64/cups/filter” but it says the files are the same.

Connected to CUPS: [http://localhost:631/](http://localhost:631/)

At this point my printer is showing up on CUPS but will not print a test page and causes CUPS to get locked up (browser timed out, can no longer open CUPS with GUI) so I have to type the following to restart it: sudo /etc/init.d/cupsys start

In the CUPS GUI
I tried removing the printer and creating a new one, and tried the switching between the ports below:
Use Connected Printer:	Brother MFC-420CN
Use Network Printer:	CUPS Printer(IPP) URI: usb:/dev/usb/lp0
Use Another Printer:	Brother MFC-420CN USB #1 (Brother MFC-420CN)
Still no success.

I tried looking at the cupsd.conf file but have no idea which settings to alter.

 I hope this has given you enough info to help me solve this problem. At this point I am out of ideas so anything you could tell me to solve this or maybe point me in the right direction would be much appreciated. Thank you.

---

### Post by adub on 2007-01-06
bump im having same exact problem

ill keep working on it and give ya feedback

---

### Post by adub on 2007-01-06
got it working in like 5 seconds after i read your post

i reinstalled through admin/printer on the setup i just went next next then browsed for the ppd file and selected it then printed test page

sudo cp /usr/share/cups/model/brmfc420cn_cups.ppd /usr/share/ppd/

browsed to the /usr/share/ppd/brmfc420cn_cups.ppd    to select driver

---

### Post by randiroo76073 on 2007-01-07
In case you're still having problems with your MFC420CN here is a great thread that you will need:  [http://ubuntuforums.org/showthread.php?t=105703](http://ubuntuforums.org/showthread.php?t=105703)
Using this thread I managed to install & solve a couple of minor problems I had with my MFC420CN :)

---

### Post by Jesse121 on 2007-01-10
Ok I managed to get it working. Everything I did was correct just needed to add one more step. After installing csh and tcsh I installed lib32stdc++6. Went through the steps again and now it works perfectly.

---

### Post by Tuxdequébec on 2007-11-18
Hi guys...

I really seem to have problems :confused: with my installation. Whatever I do, it says it can't find the file. So i did:

jeff@jeff-laptop:~$ sudo dpkg -i --force-architecture mfc420cnlpr-1.0.2-1.i386.deb
Password:
dpkg : erreur de traitement de mfc420cnlpr-1.0.2-1.i386.deb (--install) :
 ne peut pas accéder à l'archive: Aucun fichier ou répertoire de ce type
Des erreurs ont été rencontrées pendant l'exécution :
 mfc420cnlpr-1.0.2-1.i386.deb

It says it cannot access the archive. Would it have something to do with my package udates?

Thanks for helping

---

### Post by mbunchj8 on 2008-04-18
I am having some real challenges with the Brother MFC-420CN Printer.  I have tried all of the steps so far and I have even logged in as "root" only to have the same issue.  I can't seem to locate or find the brmfc42cn_cups.ppd file.

Is it available as a download from somewhere?  or where else can the mysterious file be obtained from?  

My error message is listed below:


cp: cannot stat `/usr/share/cups/model/brmfc420cn_cups.ppd': No such file or directory

Please Help -

---

