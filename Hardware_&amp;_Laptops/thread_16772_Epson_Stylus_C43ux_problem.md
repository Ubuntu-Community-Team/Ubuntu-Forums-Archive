---
title: "Epson Stylus C43ux problem"
date: 2005-02-23
forum: Hardware &amp; Laptops
---

### Post by yoshic on 2005-02-23
hi!!, well i've got an c43ux and a friend share me the driver from Mandrake. the *.pdd file,  ubuntu detects the printer in the usb port,  i can install the driver and i can see the preferences tab, but when i send to print somenthing, nothing happens, the jobs just  get queqed,  anybody can help me pease???

(p.d. sorry if i have mistakes, english is not my native languaje :wink: )

---

### Post by David Haas on 2005-02-24
I see that the Epson C43ux is among the printers listed in Ubuntu, so all the drivers and PPD files are probably within the distribution, but not yet available.

(Turn on your printer before the computer for ease of recognition.)

Here is what I did to enable my Epson Stylus C82, which now prints perfectly, whereas initially it did nothing at all. 

I'd work through Synaptic Package Manager first. Click "Computer" at the top menu bar, and then System configuration" and then "Synaptic Package Manager". In Synaptic, click "settings" and then "repositories." Enable all the repositories.

Then go to the cups (common unix printing system) packages in Synaptic--It's qiuickest to set the left column in Synaptic as "alphabertic". Her you'll see "cupsys, cupsys-bsd, cupsys-client, cupsys-driver-gimprint, and cupsys-driver-gimprint-data". If not marked as installed, install them in Synaptic. 

You might also want to go to gimpprint and install "gimpprint.doc" and "gimpprint-locales", though it's not essential.

Next, make sure that all the "foomatic" packages are installed.

Now click "computer > system configuration>printing. If you already have a printer icon there listed as C43ux, right click on it and select properties. If not work to add a printer to "Newprinter." In the properties dialog box, select the epson C43ux and then click "install driver". Here is where you select the PPD file. To locate this file, click on "Filesystem". Then select the following directories in order: usr>share>cups>model>gimp-print>4.2. in this last one scroll down to escp2-c43ux.ppd.gz and select this for your PPD file.

---

### Post by yoshic on 2005-02-26
thank you, it's been helpful  :D

---

