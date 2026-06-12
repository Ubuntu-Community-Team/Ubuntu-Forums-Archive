---
title: "Brother MFC-7460DN network printer."
date: 2011-08-31
forum: Hardware
---

### Post by dumitru on 2011-08-31
I bought a Brother MFC-7460DN multifunctional printer and I'm trying to install it as a network printer (through the router). The good thing is that on the brother.com site there are all the drivers for Linux and even the instructions how to use them, but the bad thing is I'm not an advanced Linux user and can hardly use the terminal.

Below, I print-screened the installation steps. Maybe some of you, the advanced users, can take a look on this and advice me what to do.

If it will help, I work in HP Pavilion DV6646US. I have installed Ubuntu 11.04 (32 bit).


So, my system automatically detected the Network Printer:

_[IMG]http://ubuntuforums.org/attachment.php?attachmentid=201204&stc=1&d=1314847038[/IMG]_


I want to mention that before that I've installed the "LPR Driver" and the "cupswrapper driver" (both through Ubuntu software Center). I don't know what are their for and what they mean, I just installed them.

During the printer adding process there were no drivers for my MFC-7460DN in the list, so I've installed the recommended option.




[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=201205&stc=1&d=1314847038[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=201205&stc=1&d=1314847038")


I thought that maybe the problem is in the other printer's driver. So I tried another option - to "Provide PPD file". 
Because I've  installed the "LPR Driver" and the "cupswrapper driver" earlier, I could find the "MFC7460DN.ppd" file in "usr/share/cups/model"

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=201210&stc=1&d=1314850136[/IMG]



After the 'successful' installation I tried to print the Test Page, but the system gave the error "Stopped - Unable to locate printer ..."

[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=201206&stc=1&d=1314847038[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=201206&stc=1&d=1314847038")



Do you have any idea what to do?

---

### Post by dumitru on 2011-09-01
I found the solution myself on another thread and did it as well.


"Did not work  for me until I typed in the IP address of the printer in the Host: field  under Select Device > Network Printer > AppSocket/HP JetDirect

Now it works!"

Just in case anybody needs it.

---

### Post by Borfo on 2011-11-28
I just installed one of these today - followed the instructions and installed the linux drivers from the Brother support site:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

I just installed the Printer (CUPS) driver, the Printer (LPR) driver, the Scanner driver and the Scan-key-tool.  Everything's working really well, including the scan-to-pc option on the printer itself (scan from the scanner control panel to a script on the PC.)

I'm hooked up to the printer by USB, not sure how the network setup would differ.

By the way, I just discovered gscan2pdf (it's in the software center), and it's a great scanning application.  The PDFs it creates are not unreasonably huge like they tend to be through simplescan or whatever.

---

### Post by wazupwiop on 2011-12-04
> **dumitru said:**
> I found the solution myself on another thread and did it as well.


"Did not work  for me until I typed in the IP address of the printer in the Host: field  under Select Device > Network Printer > AppSocket/HP JetDirect

Now it works!"

Just in case anybody needs it.

Thanks dude!  It worked for me.

---

### Post by here.david on 2012-01-16
> **Borfo said:**
> I just installed one of these today - followed the instructions and installed the linux drivers from the Brother support site:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

I just installed the Printer (CUPS) driver, the Printer (LPR) driver, the Scanner driver and the Scan-key-tool.  Everything's working really well, including the scan-to-pc option on the printer itself (scan from the scanner control panel to a script on the PC.)

I'm hooked up to the printer by USB, not sure how the network setup would differ.

By the way, I just discovered gscan2pdf (it's in the software center), and it's a great scanning application.  The PDFs it creates are not unreasonably huge like they tend to be through simplescan or whatever.

THANKS worked!

---

### Post by ionospheric on 2013-01-01
I just got a Brother MFC-7460DN printer and am trying to get it to work under Ubuntu 12.04 and Ethernet. 
Making progress. Installed the cupswrapper and LPR drivers from the Brother web site, but could not print. Went to the CUPS web admin interface. It said "Processing: waiting for printer to become available."

I noticed that the connection was set to USB. I changed it to network, and got my first print. :popcorn:

Now on to scanning.

---

### Post by ionospheric on 2013-01-02
Scannng works too. :p

followed the instructions at

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html#config1]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html#config1")


```
sudo dpkg  -i  --force-all brscan4-0.4.1-3.i386.deb
```

```
brsaneconfig4 -a name=SCANNER model=MFC7460DN ip=192.168.1.28
```

How did I get the IP address? From the router admin page under attached devices.

The CUPS admin address:
[http://localhost:631/printers]("http://localhost:631/printers")

---

### Post by evanrmurphy on 2013-10-31
> **ionospheric said:**
> I noticed that the connection was set to USB. I changed it to network, and got my first print.

Thanks, that did it! :)

---

### Post by ABvsPredator on 2014-10-04
I know I'm insanely late to this party, but can anyone help me get my printer going?  I can't find where somebody points to of "select device > " etc.

> Did not work  for me until I typed in the IP address of the printer in  the Host: field  under Select Device > Network Printer >  AppSocket/HP JetDirect

Where is this "Select device > network printer > " choice at?

---

