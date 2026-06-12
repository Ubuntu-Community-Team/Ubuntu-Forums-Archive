---
title: "canon LBP6030 laser printer"
date: 2017-07-07
forum: Hardware
---

### Post by ya-paulle on 2017-07-07
I have a **canon LBP6030 laser printer** and can't get it printing. Printer is connected with usb-cable. Printer seems to be installed (showing in printer configuration). If I try to print something; i get the status message printjob done. But nothing, no printout.
I'm using Ubuntu Gnome 17.04. Printer is ok, because is printing in windows. Is there somebody who this printer up and running or some advice how to get the printer working.

---

### Post by pdc on 2017-07-07
Hi ya-paulle

Canon supply their UFR driver for linux for this printer; if you go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100595001.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100595001.html)

and click to download and SAVE, it should end up in your Downloads folder as [COLOR="#0000FF"]linux-UFRIILT-drv-v131-uken.tar.gz[/COLOR]

_________

........ before installing a new driver, if you open your PRINTERS folder; (use DASH to find it .......) and delete your existing LBP6030 entry ...... if it doesn't work ....... best remove it ??

________
you need to open a terminal ......... hold down control, alt and t all at once ........ then to PASTE into the terminal; right-click at the text prompt and look for PASTE in the menu ........

so copy and paste each of these commands below

```
cd Downloads
```
```
tar -zxvf  linux-UFRIILT-drv-v131-uken.tar.gz
```
```
cd  linux-UFRIILT-drv-v131-uken
```

the last command runs the install script; watch the terminal as it may ask you various questions 
```
./install.sh
```

The install script should 1) install the drivers and 2) register the printer with lpadmin ......... so all should be good ..... let us know how it goes

---

### Post by ya-paulle on 2017-07-08
Hi @pdc, did as you described and the printer is printing. Thank you very much,

---

### Post by pdc on 2017-07-08
well done; glad it is all working well; looks like a very nice printer you have there

---

### Post by ya-paulle on 2017-07-09
Yes have it since a few days. As I 95% do only text printing and this sometimes a lot and other times nothing for 2 or 3 weeks, I don't want any more an ink-printer. Always had trouble with dirty printheads and dried colour-cartouches. So this time I decided for a monochrome laser printer to avoid these types of problems. Time will show if it was the right decision.

---

