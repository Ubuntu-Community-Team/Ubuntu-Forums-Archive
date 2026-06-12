---
title: "Installing Brother Printer, depends on libc6 (&gt;= 2.2.5) error"
date: 2011-05-01
forum: Hardware
---

### Post by n0y0x on 2011-05-01
Hi there, I've just installed Ubuntu for the first time with 11.04 onto my new laptop.

I'm trying to install the LPR driver provided by Brother, (found here:[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html) ) followed by the cupswrapper driver. I am following the instructions provided on the Brother website.

When installing the LPR driver, I run into

```
Unpacking brhl2040lpr:i386 (from brhl2040lpr-2.0.1-1.i386.deb) ...
dpkg: dependency problems prevent configuration of brhl2040lpr:i386:
 brhl2040lpr:i386 depends on libc6 (>= 2.2.5).
dpkg: error processing brhl2040lpr:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 brhl2040lpr:i386

```

Checking on synaptic, I have libc version 2.13-0ubuntu13. **Why is this a problem?**

I am running 64 bit Natty and I have both lib32stdc++6 AND ia32-libs installed.

Thanks!

---

### Post by Fazky on 2011-05-02
I have exactly the same problem with the BrotherHl2150N lpr and cupswrapper driver.

Thanks,
Fazky

Edit: I found the solution to this problem at:
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/701856]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/701856")

Cheers

---

### Post by n0y0x on 2011-05-02
I found another quasi solution. I installed the Brother HL-2035 Foomatic/hl1250 driver which was included with CUPS, even though my printer is the HL2040. Seems to work fine so far.

---

### Post by mhelmstetter on 2011-05-05
I finally got my Brother HL-2140 working on 64-bit Ubuntu 11.04 Natty.

My printer was detected fine from a fresh install as an HL-2140.  When I  attempted to print the printer would continuously print blank pages.

I had tried Faxky's solution above, building the new debs and installing them.  The new printer showed up in the Printing gui but the "Printer State" seemed to be stuck at Processing.  So I gave up on that and tried changing the driver which luckily worked.


[LIST=1]
[*]In the Printing gui, I right-clicked and selected "Properties" on the HL-2140-series printer that had been installed automatically when I installed the system.
[*]Under Settings->Make and Model, click the Change button.
[*]Click Forward on the Choose driver page after the list populates and should have "Brother (recommended)" selected in the list.
[*]The Model on the left should be selected as "HL-2140 (recommended)" or whatever Brother model you're using.  The Driver selected to the right for me was "Brother HL-2140 Foomatic/Postscript [en] (recommended)".  I changed that to the next option in the list, "Brother HL-2140 Foomatic/hpijs-pcl5e [en]".
[*]Click Forward to select
[*]I chose the "Use the new PPD as is"
[*]Tried printing a test page from the printer page and it worked!
[/LIST]

---

### Post by rotox on 2011-05-09
> **n0y0x said:**
> I found another quasi solution. I installed the Brother HL-2035 Foomatic/hl1250 driver which was included with CUPS, even though my printer is the HL2040. Seems to work fine so far.

Thank you! I have installed and uninstalled several different printer drivers (including the official Brother drivers) and so far nothing worked. I installed the Brother HL-2035 Foomatic/hl1250 driver expecting it to fail because I'd mess around with the drivers so much but IT WORKS!

Thank you! =D>

---

