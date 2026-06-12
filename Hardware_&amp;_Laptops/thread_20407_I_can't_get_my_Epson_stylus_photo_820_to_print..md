---
title: "I can't get my Epson stylus photo 820 to print."
date: 2005-03-16
forum: Hardware &amp; Laptops
---

### Post by SHY_GUY on 2005-03-16
[SIZE=7]I can't get my Epson stylus photo 820 to print.The printer is recondizied by Ubuntu but when I try to print a test page it just tells me that the parallel port is busy and will try again in 30 seconds. the green light on top of the printer dosn't even start blinking like it's trying to print. I'm new to linux, and have no clue what to do. can someone help. [email]eschmidt32@cox.net[/email]

---

### Post by kleeman on 2005-03-16
Your printer appears to be "perfectly" supported in linux according to linuxprinting.org
I noticed that it has either parrallel or usb connect. Try usb if you can and rerun the printer wizard. Also there seems to be a pretty busy epson forum here:

[http://linuxprinting.org/forums.cgi?group=linuxprinting.epson.general](http://linuxprinting.org/forums.cgi?group=linuxprinting.epson.general)

Might help. One other thing check out your /var/log/cups/error_log for any useful info....

---

### Post by David Haas on 2005-03-16
I see that the Epson stylus photo 820 is among the printers listed in Ubuntu, so all the drivers and PPD files are probably within the distribution, but not yet made available by you yet. 

(Turn on your printer before the computer for ease of recognition.)

Then work through Synaptic Package Manager to make sure that the CUPS is installed and operational. Click "Computer" at the top menu bar, and then System configuration" and then "Synaptic Package Manager". In Synaptic, click "settings" and then "repositories." Enable all the repositories.

Then go to the cups (common unix printing system) packages in Synaptic--It's quickest to set the left column in Synaptic as "alphabertic". Here you'll see "cupsys, cupsys-bsd, cupsys-client, cupsys-driver-gimprint, and cupsys-driver-gimprint-data". If not marked as installed, install them in Synaptic. 

You might also want to go to gimpprint and install "gimpprint.doc" and "gimpprint-locales", though it's not essential.

Next, make sure that all the "foomatic" packages are installed.

Now click "computer > system configuration>printing. If you already have a printer icon there listed as Epson stylus photo 820, right click on it and select properties. If not work to add a printer to "Newprinter." In the properties dialog box, select the Epson stylus photo 820 and then click "install driver". Here is where you select the PPD file. To locate this file, click on "Filesystem". Then select the following directories in order: usr>share>cups>model>gimp-print>4.2. In this last one scroll down to escp2-820.ppd.gz and select this for your PPD file. 

Because I've only used Linux for a couple of months, i can't be certain this will work, but I set up my Epson stylus c82 this way.

---

