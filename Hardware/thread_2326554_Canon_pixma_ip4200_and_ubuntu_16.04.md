---
title: "Canon pixma ip4200 and ubuntu 16.04"
date: 2016-06-02
forum: Hardware
---

### Post by ublintu on 2016-06-02
I will buy a canon pixma ip4200 printer, because I want to print photos and print on transparent film. Is the printer will work with 16.04, or am I need to add, install something?

---

### Post by ublintu on 2016-06-04
So I bought the printer. Simply need to plug in and working, BUT not every printing option working correctly and biggest problem is the resolution. I can only print on 600x600 instead of 9600x2400. How can I get 9600x2400?

---

### Post by X-RED_Tech on 2016-06-04
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters)

---

### Post by ublintu on 2016-06-06
Thank you for your reply. When I try to follow the instructions there, I het this:
sudo apt-get install alien libxml1 libpng12-0 libpng12-dev libgtk1.2 libgtk1.2-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libgtk1.2-doc' for regex 'libgtk1.2'
E: Unable to locate package libxml1
E: Unable to locate package libgtk1.2-common
E: Couldn't find any package by glob 'libgtk1.2-common'
E: Couldn't find any package by regex 'libgtk1.2-common'

---

### Post by ublintu on 2016-06-06
In some other threads I saw that need to edit this section after this command. Can I edit this just simply add more resolution options, like 2400x2400 and 1200x1200? Actually I just need a high resolution transparency option!

sudo gedit /etc/cups/ppd/iP4200.ppd

*ColorKeyWords: "Quality"
*OpenUI *StpQuality/Print Quality: PickOne
*OPOptionHints Quality: "dropdown"
*OrderDependency: 10 AnySetup *StpQuality
*StpStpQuality: 0 1 0 0 255 0.000 0.000 0.000
*DefaultStpQuality: Standard
*StpDefaultStpQuality: Standard
*StpQuality None/Manual Control:    "<</HWResolution[600 600]/cupsRowFeed 1>>setpagedevice"
*StpQuality Standard/Standard:    "<</HWResolution[600 600]/cupsRowFeed 2>>setpagedevice"
*CloseUI: *StpQuality


*ColorKeyWords: "Resolution"
*OpenUI *Resolution/Resolution: PickOne
*OPOptionHints Resolution: "resolution radiobuttons"
*OrderDependency: 10 AnySetup *Resolution
*StpStpResolution: 0 1 0 0 255 0.000 0.000 0.000
*DefaultResolution: 600dpi
*StpDefaultResolution: 601x600dpi
*Resolution 601x600dpi/Automatic:    "<</HWResolution[600 600]>>setpagedevice"
*StpResolutionMap: 601x600dpi None
*Resolution 600dpi/600x600 DPI HIGH:    "<</HWResolution[600 600]/cupsCompression 1>>setpagedevice"
*StpResolutionMap: 600dpi 600x600dpi_high
*Resolution 602x600dpi/600x600 DPI:    "<</HWResolution[600 600]/cupsCompression 2>>setpagedevice"
*StpResolutionMap: 602x600dpi 600x600dpi
*Resolution 603x600dpi/600x600 DPI DRAFT:    "<</HWResolution[600 600]/cupsCompression 3>>setpagedevice"
*StpResolutionMap: 603x600dpi 600x600dpi_draft
*Resolution 300dpi/300x300 DPI:    "<</HWResolution[300 300]/cupsCompression 4>>setpagedevice"
*StpResolutionMap: 300dpi 300x300dpi
*Resolution 301x300dpi/300x300 DPI DRAFT:    "<</HWResolution[300 300]/cupsCompression 5>>setpagedevice"
*StpResolutionMap: 301x300dpi 300x300dpi_draft
*Resolution 604x600dpi/600x600 DPI PHOTO DRAFT:    "<</HWResolution[600 600]/cupsCompression 6>>setpagedevice"
*StpResolutionMap: 604x600dpi 600x600dpi_photodraft
*Resolution 605x600dpi/600x600 DPI inkjet Hagaki:    "<</HWResolution[600 600]/cupsCompression 7>>setpagedevice"
*StpResolutionMap: 605x600dpi 600x600dpi_photo2
*Resolution 606x600dpi/600x600 DPI DRAFT inkjet Hagaki:    "<</HWResolution[600 600]/cupsCompression 8>>setpagedevice"
*StpResolutionMap: 606x600dpi 600x600dpi_photodraft2
*Resolution 607x600dpi/600x600 DPI HIGH Env/Hagaki:    "<</HWResolution[600 600]/cupsCompression 9>>setpagedevice"
*StpResolutionMap: 607x600dpi 600x600dpi_high2
*Resolution 608x600dpi/600x600 DPI Env/Hagaki:    "<</HWResolution[600 600]/cupsCompression 10>>setpagedevice"
*StpResolutionMap: 608x600dpi 600x600dpi_std2
*Resolution 609x600dpi/600x600 DPI T-Shirt:    "<</HWResolution[600 600]/cupsCompression 11>>setpagedevice"
*StpResolutionMap: 609x600dpi 600x600dpi_tshirt
*Resolution 610x600dpi/600x600 DPI HIGH Transparency:    "<</HWResolution[600 600]/cupsCompression 12>>setpagedevice"
*StpResolutionMap: 610x600dpi 600x600dpi_photohigh3
*Resolution 611x600dpi/600x600 DPI Transparency:    "<</HWResolution[600 600]/cupsCompression 13>>setpagedevice"
*StpResolutionMap: 611x600dpi 600x600dpi_photo3
*CloseUI: *Resolution

---

### Post by ublintu on 2016-06-08
I just installed canon drivers, I added 1200 x1200, 2400x 2400 lines to the ppd file, reconfigured, but nothing really changed in the resolution. I will start a new thread with the transparecy print program setup...

---

