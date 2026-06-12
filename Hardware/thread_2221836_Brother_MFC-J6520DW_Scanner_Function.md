---
title: "Brother MFC-J6520DW Scanner Function"
date: 2014-05-04
forum: Hardware
---

### Post by Brad wilkinson on 2014-05-04
I have a new Brother MFC-J6520DW and it will show up as a printer in my 12.04LTS but I don't know where or if it is putting the pages I scan when I use the scanner.

I have read lots of the Brother Printer messages on the forums, so I went and used the install script from [here]("http://support.brother.com/g/b/downloadhowto.aspx?c=au&lang=en&prod=mfcj6520dw_us_eu_as&os=128&dlid=dlf006893_000&flang=4&type3=625"), which seems to be the thing to do.

It looked like it worked, and I can print to the machine (with pdf viewers, OpenOffice and so on) but I cannot find where the scans are.

The scanner part of the printer is working as it will copy a page.

I also read the last entry in [this]("http://ubuntuforums.org/showthread.php?t=2221283") thread, and I checked my usb information as it suggested. The brother is listed as a connected device. See attached screenshot.

So does anyone know where the scanned pictures should be? Or is there something else I need to install first?

Can someone from Canoniacal talk to someone from Brother and get them to set up a PPA so us long-suffering Linux users don't have to keep going through this rubbish like its 1998?

**************************************************

EDIT:

So I found the answer in [this]("https://answers.launchpad.net/ubuntu/+source/simple-scan/+question/160332") thread on Launchpad.

---

### Post by pdc on 2014-05-04
Hi Brad; must all be a bit exasperating for you; glad it is all working;

I am guessing that the answer was to paste into a terminal the command

> [COLOR="#FF0000"]gksudo gedit /lib/udev/rules.d/40-libsane.rules[/COLOR]

and so that uses the text editor [COLOR="#0000FF"]gedi[/COLOR]t to open the file that is called [COLOR="#008000"]40-libsane.rules[/COLOR] with read/write powers as it is suffixed by sudo; 

and that one should add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):

    The lines to be added---------------------------

> [COLOR="#EE82EE"]# Brother scanners
    ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"[/COLOR]

would I have got that correct?

---

