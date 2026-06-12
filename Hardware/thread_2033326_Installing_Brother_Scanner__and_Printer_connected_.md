---
title: "Installing Brother Scanner  and Printer connected via network"
date: 2012-07-26
forum: Hardware
---

### Post by beboylips on 2012-07-26
Hello Community,

I have recently completed a very simple installation of Brother scanner which is connected through my router to my network. 

The installation is very easy and requires very little steps. 

**Printer**
Go to Printing.
Add New Printer
Click on the arrow next to Network Printer
The Brother printer should be listed first. 
In case it isn't, you can add it by URI. Use the http protocol, most Brother drivers support printing over HTTP. For example:
```

http://192.168.2.25:80

```Note the use of the port 80 which is the default HTTP port. 

Follow the on-screen instructions and select the **Generic PCL 5e** driver. Usually, the generic drivers are very effective and allow good printing. Ubuntu has an extensive database of Brother drivers and if your printer is listed, you can try using it first. If it doesn't work, the generic driver should usually work.

**Scanner**
This is actually the interesting part. Brother has pretty good Linux support for network drivers and their software can simulate locally connected USB drivers over the network so the Simple Scan software can recognize it.

Go to their website at:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)

Find your scanner model and select the appropriate driver (chose the .deb installation option). 
Download the .deb file and open it with Software Center and install it. Ignore all warnings and errors, and click continue installation if necessary. The package will install fine.

Note the name of the package you're installing. The number at the end is different depending on the model of your printer/scanner.

When the package is installed, follow the instructions provided here:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html)

And you're done. Try scanning something with Simple Scan.

Any questions,  please ask :)

-Beboy

---

### Post by CharlesA on 2012-07-26
Hi,

How is it supposed to print over HTTP?

I don't have a Brother printer, but both of the HP printers I have, have been found just by selecting add a network printer, and they are detected fine.

---

### Post by gifford on 2012-07-26
My experience has been that the Brother website is the best info on installing Brother printers and scanners. Using the Ubuntu software center does not always work, especially with network printers and scanners. There are specific drivers for Brother printers/scanners and the "generic" does not work for many of the products. Brother provides good documentation on how to install drivers, printers, scanners in Ubuntu. So to avoid headaches, use their site.

---

### Post by Merrattic on 2012-07-26
> **CharlesA said:**
> Hi,

How is it supposed to print over HTTP?

I don't have a Brother printer, but both of the HP printers I have, have been found just by selecting add a network printer, and they are detected fine.

It just does ;) My Brother network printer serves the whole house via the network, windows and linux pcs

---

### Post by beboylips on 2012-07-26
> **gifford said:**
> My experience has been that the Brother website is the best info on installing Brother printers and scanners. Using the Ubuntu software center does not always work, especially with network printers and scanners. There are specific drivers for Brother printers/scanners and the "generic" does not work for many of the products. Brother provides good documentation on how to install drivers, printers, scanners in Ubuntu. So to avoid headaches, use their site.

Second that, they have pretty awesome Linux support.

---

### Post by beboylips on 2012-07-26
> **CharlesA said:**
> Hi,

How is it supposed to print over HTTP?

I don't have a Brother printer, but both of the HP printers I have, have been found just by selecting add a network printer, and they are detected fine.

HTTP is one of many choices, but it's simple to remember and it works fine.

---

