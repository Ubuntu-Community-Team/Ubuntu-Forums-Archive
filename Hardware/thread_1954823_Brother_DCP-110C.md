---
title: "Brother DCP-110C"
date: 2012-04-08
forum: Hardware
---

### Post by netopalis45 on 2012-04-08
I have been trying to set up a Brother DCP110C printer with USB on Ubuntu 11.10. I installed the Brother drivers but whenever I try to print something, the print heads move and it sounds like it is printing but nothing shows up on the page. When I print a test page all I get is a small circle in the middle of the page with a few different colors and a grayscale line next to it. What else do I need to do to make this work?

---

### Post by Gremlinzzz on 2012-04-08
its old but this might help
[http://ubuntuforums.org/showthread.php?t=801416](http://ubuntuforums.org/showthread.php?t=801416)

---

### Post by plucky on 2012-04-09
> **netopalis45 said:**
> I have been trying to set up a Brother DCP110C printer with USB on Ubuntu 11.10. I installed the Brother drivers but whenever I try to print something, the print heads move and it sounds like it is printing but nothing shows up on the page. When I print a test page all I get is a small circle in the middle of the page with a few different colors and a grayscale line next to it. What else do I need to do to make this work?

How did you install the Brother Drivers?

Post output from a terminal for ```
dpkg -l | grep -i brother
```

If you open **Synaptic Package Manager** and search for **dcp-110c** you can install the lpr-drivers-extra and cupswrapper-extra drivers.
Then connect and power on your printer and you can now select the correct drivers for your printer.

Good Luck

---

### Post by mörgæs on 2012-04-09
Moved to the hardware forum.

---

### Post by netopalis45 on 2012-04-09
I installed them with apt-get. Here is the output you wanted:
ii  brother-cups-wrapper-common            1.0.0-10-0ubuntu5                                Common files for Brother cups wrapper packages
ii  brother-cups-wrapper-extra             1.2.1-0ubuntu3                                   Cups Wrapper drivers for extra brother printers
ii  brother-lpr-drivers-common             1.0.0-4-0ubuntu1                                 Common files for brother-lpr-drivers packages
ii  brother-lpr-drivers-extra              1.2.0-2-0ubuntu4                                 LPR drivers for extra brother printers
rc  cupswrapperdcp110c                     1.0.2-3                                          Brother DCP110C CUPS wrapper driver
rc  dcp110clpr                             1.0.2-1                                          Brother lpr Inkjet Printer Definitions
ii  mfc490cwcupswrapper                    1.1.2-2                                          Brother CUPS Inkjet Printer Definitions
ii  mfc490cwlpr                            1.1.2-2                                          Brother lpr Inkjet Printer Definitions
ii  ptouch-driver                          1.3-0ubuntu11                                    CUPS/Foomatic driver for Brother P-touch label printers

---

### Post by plucky on 2012-04-09
> ii brother-cups-wrapper-extra 1.2.1-0ubuntu3 Cups Wrapper drivers for extra brother printers
ii brother-lpr-drivers-extra 1.2.0-2-0ubuntu4 LPR drivers for extra brother printers

The drivers are installed,what happens if you add a new printer and select the correct driver?

Does it allow you to select the correct driver?

---

### Post by netopalis45 on 2012-04-09
Yes it does. I attached a screenshot of from my CUPS admin page

---

### Post by netopalis45 on 2012-04-09
I tried printing a web page but it was mostly pale and unreadable. Not all colors came out.

---

### Post by penguin7009 on 2012-04-09
> **netopalis45 said:**
> I tried printing a web page but it was mostly pale and unreadable. Not all colors came out.

netopalis45, Brother has an installer which you can download and it will find your Brother printer and install it for you.  This saved me from sending back my Brother MFC8890dw printer.  This is the link:

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr)

Try this, just unzip the file in your home directory or on your desktop, right click and choose properties and set to "execute" and then double click the file.  You will need to be online when you run it.  Just follow the instructions. If for some reason the above link does not work, just type into google, brother linux universal print driver installer, and it will hit several sites which have the link.

penguin):P

---

### Post by plucky on 2012-04-10
> **netopalis45 said:**
> I tried printing a web page but it was mostly pale and unreadable. Not all colors came out.

Eliminate the computer,try to copy a page which has a lot of colour.

Does that print ok?

---

### Post by netopalis45 on 2012-04-11
Thanks plucky, didn't even think of doing that. All the ink levels looked ok at first so I didn't think that would be the problem. Copying gave me the same result, very faded and hard to see with some colors missing.

---

