---
title: "HP 3600n printer error in 11.04 Natty using hplip driver"
date: 2011-05-08
forum: Hardware
---

### Post by bwallum on 2011-05-08
I have a problem with an HP3600n printer on an ethernet LAN.

The printer worked before upgrade from Maverick to Natty in the same environment.
The printer self tests ok using the control panel on the printer. 
It fails when trying to print a test page from 'Printing' within Ubuntu System folder. 
Unity is running
I have removed and re-installed hplip from both the Ubuntu Software Centre and HP's web site without success.
I have enabled 'Publish shared printers connected to this system'. The trouble-shooter moves on but the result is the same malfunction.

The screen shot shows how the problem manifests itself. The pdf file shows the error log. The printer prints the following when attempting to print test page from Natty:-

PCL XL error
  Subsystem: KERNEL
  Error: IllegalTag
  Operator: 0x45
  Position: 7

How can I resolve this issue please?

---

### Post by philtheman0901 on 2011-05-08
I have this same exact problem with my Lexmark Prevail Pro705 wireless printer. It stopped working once i upgraded to Natty.

---

### Post by Al218 on 2011-05-11
I have precisely the same problem with our HP 3600n lan printer after upgrading to natty.

---

### Post by b1tnut on 2011-05-11
Same here. I have the exact same issue. Any solutions or filed bug-report yet?

---

### Post by Pat53N6W on 2011-05-11
Add another me-too

---

### Post by chiraz on 2011-05-13
Same here.

I tried to reinstall the printer by reselecting the driver. No luck. There's a general error message "foomatic-rip failed", but that's probably because it couldn't print anything. After reinstalling the driver, it asks me to reconnect, but same error occurs every time.

I switched to the proprietary hpcups drivers and then it works. I did all maintenance stuff through the CUPS web interface ( localhost:631 probably ).

Good stuff, I can print again. Bad stuff, using a proprietary driver.

---

### Post by ibich on 2011-05-17
Hi, I have the same problem with HP Color LaserJet 3500, connected through LAN after upgrade to Natty. I can print after reinstalling with hpcups driver too, but the problem is with colors which print incorrectly.

From printer, I got this message:

PCL XL error
Subsystem: KERNEL
Error: IllegalTag
Operator: 0x45
Position: 7

And with foomatic/pxljr driver in the CUPS web interface I found error

"/usr/lib/cups/filter/foomatic-rip failed"

Does anyone know what to do to fix this issue (either the color problem with hpcups or the error with foomatic)?

---

### Post by jmaccelari on 2011-05-17
Same problem here - Ubuntu 11.04.

---

### Post by Al218 on 2011-05-19
I solved the problem by switching to the hplip-3.11.5 driver available for download from the HP Linux Imaging and Printing website. Installed from the .run download - was missing a required libcups package, but that was easily solved using synaptic.

---

### Post by djvictoid on 2011-05-19
I have this same issue with the pxljr driver on a laserjet 3600dn and 11.04 32-bit.

I turned on debugging in /etc/foomatic/filter.conf and found this error at the bottom of the /tmp/foomatic-rip.log ...

```
PaperSize = 8.5x11
Dpi not set, using default (600)
PaperType not set, using default Normal (0)
Copies not set, using default (1)
Tumble not set, using default Off (0)
Quality: Low
  Bitmap size 4928x6400 (8.21333x10.6667 in)
Unsupported color conversion request
GPL Ghostscript 9.01: Unrecoverable error, exit code 1
renderer exited with status 1
Possible error on renderer command line or PostScript error. Check options.Kid3 exit status: 3
```

Ubuntu 11.04 has upgraded ghostscript-cups to 9.01 from 8.71, and I wonder if this is the issue.  Does anyone know if attempting to downgrade back to 8.71 will be problematic elsewhere?

---

### Post by djvictoid on 2011-05-20
Comment #9 works!  The hplip driver is available here:
[http://sourceforge.net/projects/hplip/files/hplip/3.11.5/hplip-3.11.5.run/download](http://sourceforge.net/projects/hplip/files/hplip/3.11.5/hplip-3.11.5.run/download)

Manual and Bonjour/mDNS network discovery attempts didn't work for me in the installer, but just switching to SLP in the Advanced options did the trick.  Thanks Al218.

---

### Post by jmaccelari on 2011-06-05
I can confirm the hplip 3.11.5 trick worked for me.

However, the colours were totally broken. I found another thread that recommended using the Best option for the colour and this sorted that problem out.

So my printer is finally working again...

---

### Post by lesuisse on 2011-06-06
HI

I did the same thing as you did. I'm still getting strange colors. 
So which packages did you have to add using semantics? 
Could you please elaborate a bit more :-)

Thank you very much.

---

### Post by lesuisse on 2011-06-06
Yes, this works for me as well. 
Regarding the strange colors:
Go to HPLIP select your printer,
and go to -> general -> print quality and set it to best

That resolves the color issue as well

---

### Post by vancouverite on 2011-06-30
Hello,
I'm using an HP 3600dn and installing the hplip driver is only a partial solution.

I can now print pdfs in color by setting color to "Best", but other printing utilities that lack this setting (like GNOME Photo Printer) give the wrong color space.  I have to print to file, then print using Evince.

Also, I cannot print in grey scale.  Setting the color mode to grey scale prints out a page with the error:

PCL XL Error
       Subsystem: KERNEL
       Error:     IllegalAttributeValue
       Operator:  SetColorSpace
       Position:  5

This error is compounded with the annoyance of having a poorly integrated, 3rd party print manager (funny pop-ups, another symbol in the system tray) to make the hplip solution not that great.

Van

---

