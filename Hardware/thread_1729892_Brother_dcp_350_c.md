---
title: "Brother dcp 350 c"
date: 2011-04-15
forum: Hardware
---

### Post by christon74 on 2011-04-15
Hello everybody):P
I have lost the driver for my Brother DCP 350 C
 ubuntu version: 10.10 (Maverick Meerkat) and yes IT IS A STABLE VERSION, I have downloaded it from the official UBUNTU website.
I have tried the Bother website (printer solution for linux) I have downloaded cupswrapper, lpr...etc...
have done other 'fiddlings':lolflag:
 not to much avail, my printer will not print anything. 

:cry: Awww. I need my printer.....  Please help !


Christophe NAUD

---

### Post by Redblade20XX on 2011-04-15
Does the system give any notification of what's the problem? Does the print screen show your printer connected and is available for printing?

---

### Post by christon74 on 2011-04-15
it says there is something missing : 'brlpdwrapperdcp350c'. I have tried the synaptic, but there is nothing by that name....
There seems to be a driver for this particular printer, but it does not work.....

---

### Post by plucky on 2011-04-15
According to the [Ubuntu Wiki](https://wiki.ubuntu.com/BrotherDriverPackaging) for Brother Driver Packaging,your printer driver is packaged in the Ubuntu Repositories.

Open Synaptic Package Manager and search for dcp-350c and it should find ```
brother-cups-wrapper-extra
brother-lpr-drivers-extra 
``` and I think if you select the cups-wrapper driver to be installed,it will install both sets of drivers.

Then go to **System > Administration > Printer** and Add a new printer.
When it comes to the driver selection window,choose the correct one for your printer.

Good Luck

---

### Post by christon74 on 2011-04-15
Have already done that. the cups and lpr extra are already present and the only driver suggested is this:
Brother-DCP-350 C CUPS  v1.1 [en] (current)
I am thinking about buying a new printer, one which will immediately be recongnized by Ubuntu....

---

### Post by plucky on 2011-04-16
> **christon74 said:**
> Have already done that. the cups and lpr extra are already present and the only driver suggested is this:
Brother-DCP-350 C CUPS  v1.1 [en] (current)
I am thinking about buying a new printer, one which will immediately be recongnized by Ubuntu....

Open a terminal and post output of ```
dpkg -l | grep brother
```

That is the driver I get also in my list.

> it says there is something missing : 'brlpdwrapperdcp350c'. I have tried the synaptic, but there is nothing by that name....
There seems to be a driver for this particular printer, but it does not work..... 

When do you get this error?

Is your printer connected with a USB connection?

---

