---
title: "FujiXerox C1190FS"
date: 2010-02-03
forum: Hardware
---

### Post by deathbypizza on 2010-02-03
Hi All,

Has anyone out there managed to get a FujiXerox C1190FS working under 9.10?
I can't find anything online anywhere relating to this printer under Ubuntu.
FujiXerox releases a linux driver as an RPM (can be found here: [http://www.fujixeroxprinters.com/downloads/uploaded/DPC1190FS-linux-webpack_ede1.zip](http://www.fujixeroxprinters.com/downloads/uploaded/DPC1190FS-linux-webpack_ede1.zip)).
I've converted it to a dpkg with alien and installed. The driver has to be pointed to manually when installing the printer (installs to /usr/share/cups/model/FujiXerox/en/Fuji_Xerox_DocuPrint_C1190_FS.ppd) but it still fails to work. Print jobs stall and tasks like querying for toner levels result in the printing of jibberish. Hope someone out there has done better than I have.

Cheers,
DBP

---

### Post by Mr Y on 2010-06-23
I am also trying to get this printer driver going.

I am using 10.04.

Using the diagnostics in CUPS there is a permission denied error in the FXM_PS module.

I am waiting for a response from FX

Murray

---

### Post by Mr Y on 2010-06-23
I search the forums and found a suggestion to use the generic PCL drivers.

I tried it and it worked but only in b&w or greyscale, no colour :(

So there's definitely a problem with the FX driver.

Murray

---

### Post by Mr Y on 2010-06-23
I found what I think is a workaround.

try Xerox
Xerox WorkCentre 7345
Xerox WorkCentre 7345 Foomatic/pixlcolor [en]

seems to work on test page in colour.

trying sending a pdf to it now but it's taking a bloody long time

Murray

---

### Post by Mr Y on 2010-06-23
yes, verified working but very slow.

Am still following up with FujiXerox, 

good luck!

Murray

---

### Post by Mr Y on 2010-06-26
Further update,

it's not as slow as I thought, just I was printing graphics with a lot of details.

Also when you interrogate the printer via CUPS it iwll not read things like toner levels.

At the moment it works OK.

Let's see what FX come up with?

Murray

---

### Post by 0x0065 on 2010-09-05
Team

Thanks for your tips & leads. They helped greatly in resolving my issues.

Not sure what the go is with your generic pcl drivers. I now have 2 drivers configured:
[LIST=1]
[*]Generic PCL 6/PCL XL Printer Foomatic/pxlcolor (recommended) and
[*]Generic PCL 6/PCL XL Printer Foomatic/pxlmono
[/LIST]
as:
[LIST=1]
[*]Xerox Colour Laser and
[*]Xerox Greyscale Laser
[/LIST]
respectively. When pointed at my "FUJI XEROX DocuPrint C1190 FS", these drivers produce the results that you might sensibly expect from their names. Biggest gotcha is that you need to set the tray to "Tray 2" in the driver to get "Tray 1" on the printer.

FYI: "Tray 1" in the driver corresponds with the manual feed on the printer.

Both have been re-configured to default to best and 600dpi. Colour was CHANGED to default to colour. Haven't tested any other settings. Don't particularly plan to either. :) works for me.

---

