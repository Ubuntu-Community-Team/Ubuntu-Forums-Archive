---
title: "Tally, red hat driver? Help installing printer..."
date: 2007-05-26
forum: Hardware &amp; Laptops
---

### Post by viva_cthulhu on 2007-05-26
As usual, thanks in advance and apologies if my post proves unproper.
I can't manage to configure my Tally T9312 on Ubuntu. The most similiar driver, for Tally 908, does not work at all. Linuxprinters.org [points]("http://www.linuxprinting.org/show_printer.cgi?recnum=Tally-T9212") the T9212 model to the driver for "Hp laserjet 4", the most similar one to choose in the Ubuntu printer manager, Laserjet 4000, sends my printer haywire and makes it pour contiunuous blank sheets.
I *would* have a producer-supplied driver, but I can't make out what I am to do with it; coming from ancient 2001, it claims to be for red-hat and sports a .sh file, as follows:
```
#! /bin/sh
#
# for Tally T9312 Printer
if [ -f /usr/lib/rhs/rhs-printfilters/printerdb.9312 ]; then
    echo already installed!!
else
    echo add Tally T9312 Printer!!
    cp /usr/lib/rhs/rhs-printfilters/printerdb /usr/lib/rhs/rhs-printfilters/printerdb.old
    cat /usr/lib/rhs/rhs-printfilters/printerdb.old > /usr/lib/rhs/rhs-printfilters/printerdb
    cat t9312.db >> /usr/lib/rhs/rhs-printfilters/printerdb
    cp /usr/lib/rhs/rhs-printfilters/printerdb /usr/lib/rhs/rhs-printfilters/printerdb.9312
fi
```
...the following .db:
```

StartEntry: T9312PCL5
GSDriver: ljet4
  Description: {Tally T9312 PCL5e Compatible}
  About: { \
             Driver for Tally T9312 Laser Printer PCL5e Compatible.\
         }
  Resolution: {600} {600} {}
EndEntry

StartEntry: T9312PCL4
  GSDriver: laserjet
  Description: {Tally T9312 PCL4 Compatible}
  About: { \
             Driver for Tally T9312 Laser Printer PCL4 Compatible.\
         }
  Resolution: {300} {300} {}
EndEntry
```
...and some kind of rpm labeled "gs5.50" that to my eye seems to be some sort of ancient version of ghostscript.
What do I make of them? Can I use them? Any of you has a similar printer?

---

### Post by viva_cthulhu on 2007-06-08
Geetings again...
Anyone? I managed to run the SH from the Red Hat script but it doesn't seem to work, it refers to all the wrong directories.
Has anyone ever installed a Tally on Linux?
Thanks again...

---

