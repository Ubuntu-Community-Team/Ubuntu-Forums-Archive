---
title: "Fail to setup HP printer"
date: 2006-10-24
forum: Hardware &amp; Laptops
---

### Post by satimis on 2006-10-24
Hi folks,

Ubuntu-6.06 Live CD
gnome desktop
HP Deskjet 5740 - USB printer

Followed "HpPrinterInstallationAndMaintenanceDapper";
[https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper](https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper)

to install the printer

Add a USB printer using gnome-cups-manager

Started gnome-cups-manager --> Add Printer --> Step 1
[check] local printer
[check] Use a detected printer:```

HP Deskjet 5700
HP Deskjet_5700

```
(only 2 displayed)

~$ sudo lpinfo -v```

network socket
....
direct hp:/usb/Deskjet_5700?serial=MY4B5131V9049M
....

```

highlighted "HP Deskjet_5700" and clicked [Forward] 
--> Step 2, on Model, highlighted "Deskjet 5740
(Driver: hpijs (recommended) - HPLIP 0.9.7 (Suggested)
Clicked [Forward] --> Step 3
Filled in;
Name : DeskJet-5740
Description : HP_Printer
Location : Local

and clicked [Apply] to proceed.

No printer was added on the window of gnome-cups-manager.


Please help.  TIA


B.R.
Stephen

---

### Post by mssever on 2006-10-25
Several suggestions:
[LIST]
[*]Look in System > Administration > Users and Groups > your username > properties > user privileges tab and make sure that the "setup printers" box is checked.
[*]Try the other detected printer.
[*]Point a web browser at [http://localhost:631](http://localhost:631) and try to configure your printer from there.[/LIST]

---

### Post by satimis on 2006-10-25
Hi mssever,

> 
[*]Look in System > Administration > Users and Groups > your username > properties > user privileges tab and make sure that the "setup printers" box is checked.
Checked already.

> [*]Try the other detected printer.
Also tried, same result.

> [*]Point a web browser at [http://localhost:631](http://localhost:631) and try to configure your printer from there.
Started Firefox and typed in "http://localhost:631" -->
Administration;```

[Add This Printer] HP Deskjet 5700 (HP Deskjet 5700 USB #1)
[Add This Printer] HP Deskjet_5700 (hp:/usb/Deskjet_5700?serial=MY4B5131V9049M)
[Add This Printer] CANON (Parallel Port #1)
[Add This Printer] EPSON (Parallel Port #1)

```
I only have one printer "HP deskjet 5740" connected.  It displayed 3 printers there.

Clicked [Add This Printer] corresponding to "HP Deskjet 5700 (HP Deskjet 5700 USB #1)" --> "Model/Driver for HP_Deskjet_5700_USB_1"

highlighted "HP Deskjet 5740 Foomatic/hpijs (recommended)-HPLIP 0.9.7 (en)" and clicked [Add Printer] button.

It displayed```

413 Request Entity Too Large

HTTP/1.1 413 Request Entity Too Large Date: Wed, 25 Oct 2006 12:59:08 GMT Server: CUPS/1.2 Content-Language: en_US Upgrade: TLS/1.0,HTTP/1.1 Connection: close
```

on another page.  Tks

B.R.
satimis

---

### Post by mssever on 2006-10-25
Hmm... My HP 5150 installed perfectly. I can't figure out how come you don't have a printer icon.

Here are a couple of shots in the dark.

Open up OpenOffice and see what happens if you try to print. Do you see a printer in the OOo print dialog?

Open up a terminal and type ```
gnome-cups-manager
``` Go through the process of adding the printer and see if any errors are printed in the terminal window. If so, paste them here.

Also, could you post /etc/cups/printers.conf (be sure to sanitize it of passwords and other sensitive info)?

---

### Post by satimis on 2006-10-25
Hi mssever,

> Open up OpenOffice and see what happens if you try to print. Do you see a printer in the OOo print dialog?
No, HP deskjet 5740 printer was not there, only "Generic printer'

> Open up a terminal and type ```
gnome-cups-manager
``` Go through the process of adding the printer and see if any errors are printed in the terminal window. If so, paste them here.

On console;
$ gnome-cups-manager

1)
highlighted HP-DeskJet_5740
printout on console```

.........
Selected ppd file = linuxprinting.org-gs-builtin/HP/HP-DeskJet-pcl3.ppd
Selected ppd file = hpijs/HP/HP-DeskJet_5740-hpijs.ppd

** (gnome-cups-add:7307): WARNING **: IPP request failed with status 1280

```

2)
highlighted HP-DeskJet_5740
printout on console```

....
Selected ppd file = hpijs/HP/HP-DeskJet_5740-hpijs.ppd

** (gnome-cups-add:7422): WARNING **: IPP request failed with status 1280

```

Still the same.

Both selected ppd file = hpijs/HP/HP-DeskJet_5740-hpijs.ppd


> post /etc/cups/printers.conf (be sure to sanitize it of passwords and other sensitive info)?

$ sudo ls -l /etc/cups | grep printers.conf
$ ls -l /etc/cups | grep printers.conf
$ ls -l /etc/cups | grep printer
all without printout


B.R.
satimis

---

### Post by mssever on 2006-10-25
Here's what I just did. I installed your printer on my system and posted the changes/files that I found. I don't know whether or not this will work. Be sure to back up any file that exists prior to following these instructions.

```
cd /etc/cups
sudo nano printers.conf
```and paste the following into the file: ```
# Printer configuration file for CUPS v1.2.2
# Written by cupsd on 2006-10-25 13:48
<Printer DeskJet-5740>
Info
Location
DeviceURI 
hp:/usb/Deskjet_5700?serial=MY4B5131V9049M
State Idle
StateTime 1161802118
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy stop-printer
</Printer>
```Save and exit. Type ```
sudo chmod 600 printers.conf
sudo chown cupsys:lp printers.conf
sudo nano ppd/DeskJet-5740.ppd
```Paste the following: ```
*PPD-Adobe: "4.3"
*%
*% For information on using this, and to obtain the required backend
*% script, consult http://www.linuxprinting.org/
*%
*% This file is published under the GNU General Public License
*%
*% PPD-O-MATIC (3.0.0 or newer) generated this PPD file. It is for use with 
*% all programs and environments which use PPD files for dealing with
*% printer capability information. The printer must be configured with the
*% "foomatic-rip" backend filter script of Foomatic 3.0.0 or newer. This 
*% file and "foomatic-rip" work together to support PPD-controlled printer
*% driver option access with arbitrary free software printer drivers and
*% printing spoolers.
*%
*% To save this file on your disk, wait until the download has completed
*% (the animation of the browser logo must stop) and then use the
*% "Save as..." command in the "File" menu of your browser or in the 
*% pop-up manu when you click on this document with the right mouse button.
*% DO NOT cut and paste this file into an editor with your mouse. This can
*% introduce additional line breaks which lead to unexpected results.
*%
*% You may save this file as 'HP-DeskJet_5740-hpijs.ppd'
*%
*%
*FormatVersion:    "4.3"
*FileVersion:    "1.1"
*LanguageVersion: English 
*LanguageEncoding: ISOLatin1
*PCFileName:    "HPIJS.PPD"
*Manufacturer:    "HP"
*Product:    "(deskjet 5740)"
*cupsVersion:    1.0
*cupsManualCopies: True
*cupsModelNumber:  2
*cupsFilter:    "application/vnd.cups-postscript 0 foomatic-rip"
*%pprRIP:        foomatic-rip other
*ModelName:     "HP DeskJet 5740"
*ShortNickName: "HP DeskJet 5740 hpijs"
*NickName:      "HP DeskJet 5740 Foomatic/hpijs (recommended) - HPLIP 0.9.7"
*PSVersion:    "(3010.000) 550"
*PSVersion:    "(3010.000) 651"
*PSVersion:    "(3010.000) 652"
*PSVersion:    "(3010.000) 653"
*PSVersion:    "(3010.000) 704"
*PSVersion:    "(3010.000) 705"
*PSVersion:    "(3010.000) 800"
*LanguageLevel:    "3"
*ColorDevice:    True
*DefaultColorSpace: RGB
*FileSystem:    False
*Throughput:    "1"
*LandscapeOrientation: Plus90
*TTRasterizer:    Type42
*1284DeviceID: "
  MFG:HP;
  MDL:Deskjet 5700;
  CMD:MLC,PCL,PML,DW-PCL,DESKJET,DYN;
  CLS:PRINTER;
  DES:574X;
"
*End
*DefaultResolution: 1200dpi



*HWMargins: 18 36 18 9
*VariablePaperSize: True
*MaxMediaWidth: 100000
*MaxMediaHeight: 100000
*NonUIOrderDependency: 105 AnySetup *CustomPageSize
*CustomPageSize True: "pop pop pop pop pop
%% FoomaticRIPOptionSetting: PageSize=Custom"
*End
*FoomaticRIPOptionSetting PageSize=Custom: " -dDEVICEWIDTHPOINTS=0 -dD&&
EVICEHEIGHTPOINTS=0"
*End
*ParamCustomPageSize Width: 1 points 36 100000
*ParamCustomPageSize Height: 2 points 36 100000
*ParamCustomPageSize Orientation: 3 int 0 0
*ParamCustomPageSize WidthOffset: 4 points 0 0
*ParamCustomPageSize HeightOffset: 5 points 0 0

*FoomaticIDs: HP-DeskJet_5740 hpijs
*FoomaticRIPCommandLine: "gs -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPA&&
USE -sDEVICE=ijs -sIjsServer=hpijs%A%B%C -dIjsUseOutputFD%Z -sOutputFi&&
le=- -"
*End

*FoomaticRIPOption Model: enum CmdLine A 100
*FoomaticRIPOptionSetting Model=HP-DeskJet_5740: " -sDeviceManufacture&&
r="HEWLETT-PACKARD" -sDeviceModel="deskjet 5600""
*End

*OpenGroup: General/General

*OpenUI *PrintoutMode/Printout Mode: PickOne
*FoomaticRIPOption PrintoutMode: enum Composite B
*OrderDependency: 10 AnySetup *PrintoutMode
*DefaultPrintoutMode: Normal
*PrintoutMode Draft/Draft (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=Draft"
*FoomaticRIPOptionSetting PrintoutMode=Draft: "Quality=300FastDraftCol&&
orCMYK"
*End
*PrintoutMode Draft.Gray/Draft Grayscale (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=Draft.Gray"
*FoomaticRIPOptionSetting PrintoutMode=Draft.Gray: "Quality=300FastDra&&
ftGrayscaleCMYK"
*End
*PrintoutMode Normal/Normal (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=Normal"
*FoomaticRIPOptionSetting PrintoutMode=Normal: "Quality=300ColorCMYK"
*PrintoutMode Normal.Gray/Normal Grayscale (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=Normal.Gray"
*FoomaticRIPOptionSetting PrintoutMode=Normal.Gray: "Quality=300Graysc&&
aleCMYK"
*End
*PrintoutMode High/High Quality (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=High"
*FoomaticRIPOptionSetting PrintoutMode=High: "Quality=600ColorCMYK"
*PrintoutMode High.Gray/High Quality Grayscale (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=High.Gray"
*FoomaticRIPOptionSetting PrintoutMode=High.Gray: "Quality=600Grayscal&&
eCMYK"
*End
*PrintoutMode Photo/Photo (on photo paper): "%% FoomaticRIPOptionSetting: PrintoutMode=Photo"
*FoomaticRIPOptionSetting PrintoutMode=Photo: "Quality=1200PhotoCMYKFu&&
llBleed"
*End
*CloseUI: *PrintoutMode

*OpenUI *PageSize/Page Size: PickOne
*FoomaticRIPOption PageSize: enum CmdLine A
*OrderDependency: 105 AnySetup *PageSize
*DefaultPageSize: Letter
*PageSize Letter/Letter: "%% FoomaticRIPOptionSetting: PageSize=Letter"
*FoomaticRIPOptionSetting PageSize=Letter: " -dDEVICEWIDTHPOINTS=612 -&&
dDEVICEHEIGHTPOINTS=792"
*End
*PageSize A4/A4: "%% FoomaticRIPOptionSetting: PageSize=A4"
*FoomaticRIPOptionSetting PageSize=A4: " -dDEVICEWIDTHPOINTS=595 -dDEV&&
ICEHEIGHTPOINTS=842"
*End
*PageSize Photo/Photo/4x6 inch index card: "%% FoomaticRIPOptionSetting: PageSize=Photo"
*FoomaticRIPOptionSetting PageSize=Photo: " -dDEVICEWIDTHPOINTS=288 -d&&
DEVICEHEIGHTPOINTS=432"
*End
*PageSize Photo5x7/Photo/5x7 inch index card: "%% FoomaticRIPOptionSetting: PageSize=Photo5x7"
*FoomaticRIPOptionSetting PageSize=Photo5x7: " -dDEVICEWIDTHPOINTS=360&&
 -dDEVICEHEIGHTPOINTS=504"
*End
*PageSize PhotoTearOff/Photo with tear-off tab: "%% FoomaticRIPOptionSetting: PageSize=PhotoTearOff"
*FoomaticRIPOptionSetting PageSize=PhotoTearOff: " -dDEVICEWIDTHPOINTS&&
=288 -dDEVICEHEIGHTPOINTS=432"
*End
*PageSize 3x5/3x5 inch index card: "%% FoomaticRIPOptionSetting: PageSize=3x5"
*FoomaticRIPOptionSetting PageSize=3x5: " -dDEVICEWIDTHPOINTS=216 -dDE&&
VICEHEIGHTPOINTS=360"
*End
*PageSize 5x8/5x8 inch index card: "%% FoomaticRIPOptionSetting: PageSize=5x8"
*FoomaticRIPOptionSetting PageSize=5x8: " -dDEVICEWIDTHPOINTS=360 -dDE&&
VICEHEIGHTPOINTS=576"
*End
*PageSize A5/A5: "%% FoomaticRIPOptionSetting: PageSize=A5"
*FoomaticRIPOptionSetting PageSize=A5: " -dDEVICEWIDTHPOINTS=420 -dDEV&&
ICEHEIGHTPOINTS=595"
*End
*PageSize A6/A6: "%% FoomaticRIPOptionSetting: PageSize=A6"
*FoomaticRIPOptionSetting PageSize=A6: " -dDEVICEWIDTHPOINTS=297 -dDEV&&
ICEHEIGHTPOINTS=420"
*End
*PageSize A6TearOff/A6 with tear-off tab: "%% FoomaticRIPOptionSetting: PageSize=A6TearOff"
*FoomaticRIPOptionSetting PageSize=A6TearOff: " -dDEVICEWIDTHPOINTS=29&&
7 -dDEVICEHEIGHTPOINTS=420"
*End
*PageSize B5JIS/B5 (JIS): "%% FoomaticRIPOptionSetting: PageSize=B5JIS"
*FoomaticRIPOptionSetting PageSize=B5JIS: " -dDEVICEWIDTHPOINTS=516 -d&&
DEVICEHEIGHTPOINTS=729"
*End
*PageSize Env10/Envelope #10: "%% FoomaticRIPOptionSetting: PageSize=Env10"
*FoomaticRIPOptionSetting PageSize=Env10: " -dDEVICEWIDTHPOINTS=297 -d&&
DEVICEHEIGHTPOINTS=684"
*End
*PageSize EnvC5/Envelope C5: "%% FoomaticRIPOptionSetting: PageSize=EnvC5"
*FoomaticRIPOptionSetting PageSize=EnvC5: " -dDEVICEWIDTHPOINTS=459 -d&&
DEVICEHEIGHTPOINTS=649"
*End
*PageSize EnvC6/Envelope C6: "%% FoomaticRIPOptionSetting: PageSize=EnvC6"
*FoomaticRIPOptionSetting PageSize=EnvC6: " -dDEVICEWIDTHPOINTS=323 -d&&
DEVICEHEIGHTPOINTS=459"
*End
*PageSize EnvDL/Envelope DL: "%% FoomaticRIPOptionSetting: PageSize=EnvDL"
*FoomaticRIPOptionSetting PageSize=EnvDL: " -dDEVICEWIDTHPOINTS=312 -d&&
DEVICEHEIGHTPOINTS=624"
*End
*PageSize EnvISOB5/Envelope B5: "%% FoomaticRIPOptionSetting: PageSize=EnvISOB5"
*FoomaticRIPOptionSetting PageSize=EnvISOB5: " -dDEVICEWIDTHPOINTS=499&&
 -dDEVICEHEIGHTPOINTS=709"
*End
*PageSize EnvMonarch/Envelope Monarch: "%% FoomaticRIPOptionSetting: PageSize=EnvMonarch"
*FoomaticRIPOptionSetting PageSize=EnvMonarch: " -dDEVICEWIDTHPOINTS=2&&
79 -dDEVICEHEIGHTPOINTS=540"
*End
*PageSize Executive/Executive: "%% FoomaticRIPOptionSetting: PageSize=Executive"
*FoomaticRIPOptionSetting PageSize=Executive: " -dDEVICEWIDTHPOINTS=52&&
2 -dDEVICEHEIGHTPOINTS=756"
*End
*PageSize FLSA/American Foolscap: "%% FoomaticRIPOptionSetting: PageSize=FLSA"
*FoomaticRIPOptionSetting PageSize=FLSA: " -dDEVICEWIDTHPOINTS=612 -dD&&
EVICEHEIGHTPOINTS=936"
*End
*PageSize Hagaki/Hagaki: "%% FoomaticRIPOptionSetting: PageSize=Hagaki"
*FoomaticRIPOptionSetting PageSize=Hagaki: " -dDEVICEWIDTHPOINTS=283 -&&
dDEVICEHEIGHTPOINTS=420"
*End
*PageSize Legal/Legal: "%% FoomaticRIPOptionSetting: PageSize=Legal"
*FoomaticRIPOptionSetting PageSize=Legal: " -dDEVICEWIDTHPOINTS=612 -d&&
DEVICEHEIGHTPOINTS=1008"
*End
*PageSize Oufuku/Oufuku-Hagaki: "%% FoomaticRIPOptionSetting: PageSize=Oufuku"
*FoomaticRIPOptionSetting PageSize=Oufuku: " -dDEVICEWIDTHPOINTS=420 -&&
dDEVICEHEIGHTPOINTS=567"
*End
*PageSize w558h774/16K: "%% FoomaticRIPOptionSetting: PageSize=w558h774"
*FoomaticRIPOptionSetting PageSize=w558h774: " -dDEVICEWIDTHPOINTS=558&&
 -dDEVICEHEIGHTPOINTS=774"
*End
*PageSize w612h935/Executive (JIS): "%% FoomaticRIPOptionSetting: PageSize=w612h935"
*FoomaticRIPOptionSetting PageSize=w612h935: " -dDEVICEWIDTHPOINTS=612&&
 -dDEVICEHEIGHTPOINTS=935"
*End
*CloseUI: *PageSize

*OpenUI *PageRegion: PickOne
*OrderDependency: 105 AnySetup *PageRegion
*DefaultPageRegion: Letter
*PageRegion Letter/Letter: "%% FoomaticRIPOptionSetting: PageSize=Letter"
*PageRegion A4/A4: "%% FoomaticRIPOptionSetting: PageSize=A4"
*PageRegion Photo/Photo/4x6 inch index card: "%% FoomaticRIPOptionSetting: PageSize=Photo"
*PageRegion Photo5x7/Photo/5x7 inch index card: "%% FoomaticRIPOptionSetting: PageSize=Photo5x7"
*PageRegion PhotoTearOff/Photo with tear-off tab: "%% FoomaticRIPOptionSetting: PageSize=PhotoTearOff"
*PageRegion 3x5/3x5 inch index card: "%% FoomaticRIPOptionSetting: PageSize=3x5"
*PageRegion 5x8/5x8 inch index card: "%% FoomaticRIPOptionSetting: PageSize=5x8"
*PageRegion A5/A5: "%% FoomaticRIPOptionSetting: PageSize=A5"
*PageRegion A6/A6: "%% FoomaticRIPOptionSetting: PageSize=A6"
*PageRegion A6TearOff/A6 with tear-off tab: "%% FoomaticRIPOptionSetting: PageSize=A6TearOff"
*PageRegion B5JIS/B5 (JIS): "%% FoomaticRIPOptionSetting: PageSize=B5JIS"
*PageRegion Env10/Envelope #10: "%% FoomaticRIPOptionSetting: PageSize=Env10"
*PageRegion EnvC5/Envelope C5: "%% FoomaticRIPOptionSetting: PageSize=EnvC5"
*PageRegion EnvC6/Envelope C6: "%% FoomaticRIPOptionSetting: PageSize=EnvC6"
*PageRegion EnvDL/Envelope DL: "%% FoomaticRIPOptionSetting: PageSize=EnvDL"
*PageRegion EnvISOB5/Envelope B5: "%% FoomaticRIPOptionSetting: PageSize=EnvISOB5"
*PageRegion EnvMonarch/Envelope Monarch: "%% FoomaticRIPOptionSetting: PageSize=EnvMonarch"
*PageRegion Executive/Executive: "%% FoomaticRIPOptionSetting: PageSize=Executive"
*PageRegion FLSA/American Foolscap: "%% FoomaticRIPOptionSetting: PageSize=FLSA"
*PageRegion Hagaki/Hagaki: "%% FoomaticRIPOptionSetting: PageSize=Hagaki"
*PageRegion Legal/Legal: "%% FoomaticRIPOptionSetting: PageSize=Legal"
*PageRegion Oufuku/Oufuku-Hagaki: "%% FoomaticRIPOptionSetting: PageSize=Oufuku"
*PageRegion w558h774/16K: "%% FoomaticRIPOptionSetting: PageSize=w558h774"
*PageRegion w612h935/Executive (JIS): "%% FoomaticRIPOptionSetting: PageSize=w612h935"
*CloseUI: *PageRegion

*DefaultImageableArea: Letter
*ImageableArea Letter/Letter: "18 36 594 783"
*ImageableArea A4/A4: "9.72 36 585.28 833"
*ImageableArea Photo/Photo/4x6 inch index card: "0 36 288 432"
*ImageableArea Photo5x7/Photo/5x7 inch index card: "0 36 360 504"
*ImageableArea PhotoTearOff/Photo with tear-off tab: "0 0 288 432"
*ImageableArea 3x5/3x5 inch index card: "0 36 216 360"
*ImageableArea 5x8/5x8 inch index card: "0 36 360 576"
*ImageableArea A5/A5: "9 36 411 586"
*ImageableArea A6/A6: "0 36 297 420"
*ImageableArea A6TearOff/A6 with tear-off tab: "0 0 297 420"
*ImageableArea B5JIS/B5 (JIS): "18 36 498 720"
*ImageableArea Env10/Envelope #10: "0 36 297 684"
*ImageableArea EnvC5/Envelope C5: "18 36 441 640"
*ImageableArea EnvC6/Envelope C6: "0 36 323 459"
*ImageableArea EnvDL/Envelope DL: "0 36 312 624"
*ImageableArea EnvISOB5/Envelope B5: "18 36 481 700"
*ImageableArea EnvMonarch/Envelope Monarch: "0 36 279 540"
*ImageableArea Executive/Executive: "18 36 504 747"
*ImageableArea FLSA/American Foolscap: "18 36 594 927"
*ImageableArea Hagaki/Hagaki: "0 36 283 420"
*ImageableArea Legal/Legal: "18 36 594 999"
*ImageableArea Oufuku/Oufuku-Hagaki: "0 36 420 567"
*ImageableArea w558h774/16K: "18 36 540 765"
*ImageableArea w612h935/Executive (JIS): "18 36 594 926"

*DefaultPaperDimension: Letter
*PaperDimension Letter/Letter: "612 792"
*PaperDimension A4/A4: "595 842"
*PaperDimension Photo/Photo/4x6 inch index card: "288 432"
*PaperDimension Photo5x7/Photo/5x7 inch index card: "360 504"
*PaperDimension PhotoTearOff/Photo with tear-off tab: "288 432"
*PaperDimension 3x5/3x5 inch index card: "216 360"
*PaperDimension 5x8/5x8 inch index card: "360 576"
*PaperDimension A5/A5: "420 595"
*PaperDimension A6/A6: "297 420"
*PaperDimension A6TearOff/A6 with tear-off tab: "297 420"
*PaperDimension B5JIS/B5 (JIS): "516 729"
*PaperDimension Env10/Envelope #10: "297 684"
*PaperDimension EnvC5/Envelope C5: "459 649"
*PaperDimension EnvC6/Envelope C6: "323 459"
*PaperDimension EnvDL/Envelope DL: "312 624"
*PaperDimension EnvISOB5/Envelope B5: "499 709"
*PaperDimension EnvMonarch/Envelope Monarch: "279 540"
*PaperDimension Executive/Executive: "522 756"
*PaperDimension FLSA/American Foolscap: "612 936"
*PaperDimension Hagaki/Hagaki: "283 420"
*PaperDimension Legal/Legal: "612 1008"
*PaperDimension Oufuku/Oufuku-Hagaki: "420 567"
*PaperDimension w558h774/16K: "558 774"
*PaperDimension w612h935/Executive (JIS): "612 935"

*OpenUI *InputSlot/Media Source: PickOne
*FoomaticRIPOption InputSlot: enum CmdLine C
*OrderDependency: 100 AnySetup *InputSlot
*DefaultInputSlot: Default
*InputSlot Default/Printer default: "%% FoomaticRIPOptionSetting: InputSlot=Default"
*FoomaticRIPOptionSetting InputSlot=Default: ",PS:MediaPosition=7"
*InputSlot PhotoTray/Photo Tray: "%% FoomaticRIPOptionSetting: InputSlot=PhotoTray"
*FoomaticRIPOptionSetting InputSlot=PhotoTray: ",PS:MediaPosition=6"
*InputSlot Upper/Upper Tray: "%% FoomaticRIPOptionSetting: InputSlot=Upper"
*FoomaticRIPOptionSetting InputSlot=Upper: ",PS:MediaPosition=1"
*InputSlot Lower/Lower Tray: "%% FoomaticRIPOptionSetting: InputSlot=Lower"
*FoomaticRIPOptionSetting InputSlot=Lower: ",PS:MediaPosition=4"
*InputSlot Envelope/Envelope Feeder: "%% FoomaticRIPOptionSetting: InputSlot=Envelope"
*FoomaticRIPOptionSetting InputSlot=Envelope: ",PS:MediaPosition=3"
*InputSlot LargeCapacity/Large Capacity Tray: "%% FoomaticRIPOptionSetting: InputSlot=LargeCapacity"
*FoomaticRIPOptionSetting InputSlot=LargeCapacity: ",PS:MediaPosition=&&
5"
*End
*InputSlot Manual/Manual Feeder: "%% FoomaticRIPOptionSetting: InputSlot=Manual"
*FoomaticRIPOptionSetting InputSlot=Manual: ",PS:MediaPosition=2"
*InputSlot MPTray/Multi Purpose Tray: "%% FoomaticRIPOptionSetting: InputSlot=MPTray"
*FoomaticRIPOptionSetting InputSlot=MPTray: ",PS:MediaPosition=8"
*CloseUI: *InputSlot

*OpenUI *Duplex/Double-Sided Printing: PickOne
*FoomaticRIPOption Duplex: enum CmdLine A
*OrderDependency: 120 AnySetup *Duplex
*DefaultDuplex: None
*Duplex DuplexNoTumble/Long Edge (Standard): "%% FoomaticRIPOptionSetting: Duplex=DuplexNoTumble"
*FoomaticRIPOptionSetting Duplex=DuplexNoTumble: " -dDuplex=true -dTum&&
ble=false"
*End
*Duplex DuplexTumble/Short Edge (Flip): "%% FoomaticRIPOptionSetting: Duplex=DuplexTumble"
*FoomaticRIPOptionSetting Duplex=DuplexTumble: " -dDuplex=true -dTumbl&&
e=true"
*End
*Duplex None/Off: "%% FoomaticRIPOptionSetting: Duplex=None"
*FoomaticRIPOptionSetting Duplex=None: " -dDuplex=false"
*CloseUI: *Duplex

*CloseGroup: General

*OpenGroup: PrintoutMode/Printout Mode

*OpenUI *Quality/Resolution, Quality, Ink Type, Media Type: PickOne
*FoomaticRIPOption Quality: enum CmdLine B
*OrderDependency: 100 AnySetup *Quality
*DefaultQuality: FromPrintoutMode
*Quality FromPrintoutMode/Controlled by 'Printout Mode': "%% FoomaticRIPOptionSetting: Quality=@PrintoutMode"
*Quality 300ColorCMYK/300 dpi, Color, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=300ColorCMYK"
*FoomaticRIPOptionSetting Quality=300ColorCMYK: " -r300 -sIjsParams=Qu&&
ality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet&&
=2"
*End
*Quality 300ColorCMYKFullBleed/300 dpi, Color, Full Bleed, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=300ColorCMYKFullBleed"
*FoomaticRIPOptionSetting Quality=300ColorCMYKFullBleed: " -r300 -sIjs&&
Params=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quali&&
ty:PenSet=2,Quality:FullBleed=1"
*End
*Quality 300DraftColorCMYK/300 dpi, Draft, Color, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=300DraftColorCMYK"
*FoomaticRIPOptionSetting Quality=300DraftColorCMYK: " -r300 -sIjsPara&&
ms=Quality:Quality=1,Quality:ColorMode=2,Quality:MediaType=0,Quality:P&&
enSet=2"
*End
*Quality 300DraftGrayscaleCMYK/300 dpi, Draft, Grayscale, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=300DraftGrayscaleCMYK"
*FoomaticRIPOptionSetting Quality=300DraftGrayscaleCMYK: " -r300 -sIjs&&
Params=Quality:Quality=1,Quality:ColorMode=0,Quality:MediaType=0,Quali&&
ty:PenSet=2"
*End
*Quality 300FastDraftColorCMYK/300 dpi, FastDraft, Color, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=300FastDraftColorCMYK"
*FoomaticRIPOptionSetting Quality=300FastDraftColorCMYK: " -r300 -sIjs&&
Params=Quality:Quality=4,Quality:ColorMode=2,Quality:MediaType=0,Quali&&
ty:PenSet=2"
*End
*Quality 300FastDraftGrayscaleCMYK/300 dpi, FastDraft, Grayscale, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=300FastDraftGrayscaleCMYK"
*FoomaticRIPOptionSetting Quality=300FastDraftGrayscaleCMYK: " -r300 -&&
sIjsParams=Quality:Quality=4,Quality:ColorMode=0,Quality:MediaType=0,Q&&
uality:PenSet=2"
*End
*Quality 300GrayscaleCMYK/300 dpi, Grayscale, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=300GrayscaleCMYK"
*FoomaticRIPOptionSetting Quality=300GrayscaleCMYK: " -r300 -sIjsParam&&
s=Quality:Quality=0,Quality:ColorMode=0,Quality:MediaType=0,Quality:Pe&&
nSet=2"
*End
*Quality 600ColorCMYK/600 dpi, Color, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=600ColorCMYK"
*FoomaticRIPOptionSetting Quality=600ColorCMYK: " -r600 -sIjsParams=Qu&&
ality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet&&
=2"
*End
*Quality 600ColorCMYKFullBleed/600 dpi, Color, Full Bleed, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=600ColorCMYKFullBleed"
*FoomaticRIPOptionSetting Quality=600ColorCMYKFullBleed: " -r600 -sIjs&&
Params=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quali&&
ty:PenSet=2,Quality:FullBleed=1"
*End
*Quality 600GrayscaleCMYK/600 dpi, Grayscale, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=600GrayscaleCMYK"
*FoomaticRIPOptionSetting Quality=600GrayscaleCMYK: " -r600 -sIjsParam&&
s=Quality:Quality=0,Quality:ColorMode=0,Quality:MediaType=0,Quality:Pe&&
nSet=2"
*End
*Quality 1200PhotoCMYK/1200 dpi, Photo, Black + Color Cartr., Photo Paper: "%% FoomaticRIPOptionSetting: Quality=1200PhotoCMYK"
*FoomaticRIPOptionSetting Quality=1200PhotoCMYK: " -r1200 -sIjsParams=&&
Quality:Quality=3,Quality:ColorMode=2,Quality:MediaType=2,Quality:PenS&&
et=2"
*End
*Quality 1200PhotoCMYKFullBleed/1200 dpi, Photo, Full Bleed, Black + Color Cartr., Photo Paper: "%% FoomaticRIPOptionSetting: Quality=1200PhotoCMYKFullBleed"
*FoomaticRIPOptionSetting Quality=1200PhotoCMYKFullBleed: " -r1200 -sI&&
jsParams=Quality:Quality=3,Quality:ColorMode=2,Quality:MediaType=2,Qua&&
lity:PenSet=2,Quality:FullBleed=1"
*End
*CloseUI: *Quality

*CloseGroup: PrintoutMode


*% Generic boilerplate PPD stuff as standard PostScript fonts and so on

*DefaultFont: Courier
*Font AvantGarde-Book: Standard "(001.006S)" Standard ROM
*Font AvantGarde-BookOblique: Standard "(001.006S)" Standard ROM
*Font AvantGarde-Demi: Standard "(001.007S)" Standard ROM
*Font AvantGarde-DemiOblique: Standard "(001.007S)" Standard ROM
*Font Bookman-Demi: Standard "(001.004S)" Standard ROM
*Font Bookman-DemiItalic: Standard "(001.004S)" Standard ROM
*Font Bookman-Light: Standard "(001.004S)" Standard ROM
*Font Bookman-LightItalic: Standard "(001.004S)" Standard ROM
*Font Courier: Standard "(002.004S)" Standard ROM
*Font Courier-Bold: Standard "(002.004S)" Standard ROM
*Font Courier-BoldOblique: Standard "(002.004S)" Standard ROM
*Font Courier-Oblique: Standard "(002.004S)" Standard ROM
*Font Helvetica: Standard "(001.006S)" Standard ROM
*Font Helvetica-Bold: Standard "(001.007S)" Standard ROM
*Font Helvetica-BoldOblique: Standard "(001.007S)" Standard ROM
*Font Helvetica-Narrow: Standard "(001.006S)" Standard ROM
*Font Helvetica-Narrow-Bold: Standard "(001.007S)" Standard ROM
*Font Helvetica-Narrow-BoldOblique: Standard "(001.007S)" Standard ROM
*Font Helvetica-Narrow-Oblique: Standard "(001.006S)" Standard ROM
*Font Helvetica-Oblique: Standard "(001.006S)" Standard ROM
*Font NewCenturySchlbk-Bold: Standard "(001.009S)" Standard ROM
*Font NewCenturySchlbk-BoldItalic: Standard "(001.007S)" Standard ROM
*Font NewCenturySchlbk-Italic: Standard "(001.006S)" Standard ROM
*Font NewCenturySchlbk-Roman: Standard "(001.007S)" Standard ROM
*Font Palatino-Bold: Standard "(001.005S)" Standard ROM
*Font Palatino-BoldItalic: Standard "(001.005S)" Standard ROM
*Font Palatino-Italic: Standard "(001.005S)" Standard ROM
*Font Palatino-Roman: Standard "(001.005S)" Standard ROM
*Font Symbol: Special "(001.007S)" Special ROM
*Font Times-Bold: Standard "(001.007S)" Standard ROM
*Font Times-BoldItalic: Standard "(001.009S)" Standard ROM
*Font Times-Italic: Standard "(001.007S)" Standard ROM
*Font Times-Roman: Standard "(001.007S)" Standard ROM
*Font ZapfChancery-MediumItalic: Standard "(001.007S)" Standard ROM
*Font ZapfDingbats: Special "(001.004S)" Standard ROM

```Save and exit.
```
sudo chown cupsys:lp ppd/DeskJet-5740.ppd
sudo chmod 644 ppd/DeskJet-5740.ppd
sudo /etc/init.d/cupsys restart
```Now, open up OpenOffice (close it first if it's already open) and see what happens.

---

### Post by satimis on 2006-10-25
Hi mssever,

Ubuntu 6.06 Live CD
HP Deskjet 5740

Lot of tks for your detail advice.

Did all steps as advised.

$ cat /etc/cups/printers.conf```

# Printer configuration file for CUPS v1.2.2
# Written by cupsd on 2006-10-25 13:48
<Printer DeskJet-5740>
Info
Location
DeviceURI 
hp:/usb/Deskjet_5700?serial=MY4B5131V9049M
State Idle
StateTime 1161802118
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy stop-printer
</Printer>
```

$ cat /etc/cups/ppd/DeskJet-5740.ppd```

*PPD-Adobe: "4.3"
*%
*% For information on using this, and to obtain the required backend
*% script, consult http://www.linuxprinting.org/
*%
*% This file is published under the GNU General Public License
*%
*% PPD-O-MATIC (3.0.0 or newer) generated this PPD file. It is for use with 
*% all programs and environments which use PPD files for dealing with
*% printer capability information. The printer must be configured with the
*% "foomatic-rip" backend filter script of Foomatic 3.0.0 or newer. This 
*% file and "foomatic-rip" work together to support PPD-controlled printer
*% driver option access with arbitrary free software printer drivers and
*% printing spoolers.
*%
*% To save this file on your disk, wait until the download has completed
*% (the animation of the browser logo must stop) and then use the
*% "Save as..." command in the "File" menu of your browser or in the 
*% pop-up manu when you click on this document with the right mouse button.
*% DO NOT cut and paste this file into an editor with your mouse. This can
*% introduce additional line breaks which lead to unexpected results.
*%
*% You may save this file as 'HP-DeskJet_5740-hpijs.ppd'
*%
*%
*FormatVersion:    "4.3"
*FileVersion:    "1.1"
*LanguageVersion: English 
*LanguageEncoding: ISOLatin1
*PCFileName:    "HPIJS.PPD"
*Manufacturer:    "HP"
*Product:    "(deskjet 5740)"
*cupsVersion:    1.0
*cupsManualCopies: True
*cupsModelNumber:  2
*cupsFilter:    "application/vnd.cups-postscript 0 foomatic-rip"
*%pprRIP:        foomatic-rip other
*ModelName:     "HP DeskJet 5740"
*ShortNickName: "HP DeskJet 5740 hpijs"
*NickName:      "HP DeskJet 5740 Foomatic/hpijs (recommended) - HPLIP 0.9.7"
*PSVersion:    "(3010.000) 550"
*PSVersion:    "(3010.000) 651"
*PSVersion:    "(3010.000) 652"
*PSVersion:    "(3010.000) 653"
*PSVersion:    "(3010.000) 704"
*PSVersion:    "(3010.000) 705"
*PSVersion:    "(3010.000) 800"
*LanguageLevel:    "3"
*ColorDevice:    True
*DefaultColorSpace: RGB
*FileSystem:    False
*Throughput:    "1"
*LandscapeOrientation: Plus90
*TTRasterizer:    Type42
*1284DeviceID: "
  MFG:HP;
  MDL:Deskjet 5700;
  CMD:MLC,PCL,PML,DW-PCL,DESKJET,DYN;
  CLS:PRINTER;
  DES:574X;
"
*End
*DefaultResolution: 1200dpi



*HWMargins: 18 36 18 9
*VariablePaperSize: True
*MaxMediaWidth: 100000
*MaxMediaHeight: 100000
*NonUIOrderDependency: 105 AnySetup *CustomPageSize
*CustomPageSize True: "pop pop pop pop pop
%% FoomaticRIPOptionSetting: PageSize=Custom"
*End
*FoomaticRIPOptionSetting PageSize=Custom: " -dDEVICEWIDTHPOINTS=0 -dD&&
EVICEHEIGHTPOINTS=0"
*End
*ParamCustomPageSize Width: 1 points 36 100000
*ParamCustomPageSize Height: 2 points 36 100000
*ParamCustomPageSize Orientation: 3 int 0 0
*ParamCustomPageSize WidthOffset: 4 points 0 0
*ParamCustomPageSize HeightOffset: 5 points 0 0

*FoomaticIDs: HP-DeskJet_5740 hpijs
*FoomaticRIPCommandLine: "gs -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPA&&
USE -sDEVICE=ijs -sIjsServer=hpijs%A%B%C -dIjsUseOutputFD%Z -sOutputFi&&
le=- -"
*End

*FoomaticRIPOption Model: enum CmdLine A 100
*FoomaticRIPOptionSetting Model=HP-DeskJet_5740: " -sDeviceManufacture&&
r="HEWLETT-PACKARD" -sDeviceModel="deskjet 5600""
*End

*OpenGroup: General/General

*OpenUI *PrintoutMode/Printout Mode: PickOne
*FoomaticRIPOption PrintoutMode: enum Composite B
*OrderDependency: 10 AnySetup *PrintoutMode
*DefaultPrintoutMode: Normal
*PrintoutMode Draft/Draft (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=Draft"
*FoomaticRIPOptionSetting PrintoutMode=Draft: "Quality=300FastDraftCol&&
orCMYK"
*End
*PrintoutMode Draft.Gray/Draft Grayscale (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=Draft.Gray"
*FoomaticRIPOptionSetting PrintoutMode=Draft.Gray: "Quality=300FastDra&&
ftGrayscaleCMYK"
*End
*PrintoutMode Normal/Normal (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=Normal"
*FoomaticRIPOptionSetting PrintoutMode=Normal: "Quality=300ColorCMYK"
*PrintoutMode Normal.Gray/Normal Grayscale (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=Normal.Gray"
*FoomaticRIPOptionSetting PrintoutMode=Normal.Gray: "Quality=300Graysc&&
aleCMYK"
*End
*PrintoutMode High/High Quality (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=High"
*FoomaticRIPOptionSetting PrintoutMode=High: "Quality=600ColorCMYK"
*PrintoutMode High.Gray/High Quality Grayscale (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=High.Gray"
*FoomaticRIPOptionSetting PrintoutMode=High.Gray: "Quality=600Grayscal&&
eCMYK"
*End
*PrintoutMode Photo/Photo (on photo paper): "%% FoomaticRIPOptionSetting: PrintoutMode=Photo"
*FoomaticRIPOptionSetting PrintoutMode=Photo: "Quality=1200PhotoCMYKFu&&
llBleed"
*End
*CloseUI: *PrintoutMode

*OpenUI *PageSize/Page Size: PickOne
*FoomaticRIPOption PageSize: enum CmdLine A
*OrderDependency: 105 AnySetup *PageSize
*DefaultPageSize: Letter
*PageSize Letter/Letter: "%% FoomaticRIPOptionSetting: PageSize=Letter"
*FoomaticRIPOptionSetting PageSize=Letter: " -dDEVICEWIDTHPOINTS=612 -&&
dDEVICEHEIGHTPOINTS=792"
*End
*PageSize A4/A4: "%% FoomaticRIPOptionSetting: PageSize=A4"
*FoomaticRIPOptionSetting PageSize=A4: " -dDEVICEWIDTHPOINTS=595 -dDEV&&
ICEHEIGHTPOINTS=842"
*End
*PageSize Photo/Photo/4x6 inch index card: "%% FoomaticRIPOptionSetting: PageSize=Photo"
*FoomaticRIPOptionSetting PageSize=Photo: " -dDEVICEWIDTHPOINTS=288 -d&&
DEVICEHEIGHTPOINTS=432"
*End
*PageSize Photo5x7/Photo/5x7 inch index card: "%% FoomaticRIPOptionSetting: PageSize=Photo5x7"
*FoomaticRIPOptionSetting PageSize=Photo5x7: " -dDEVICEWIDTHPOINTS=360&&
 -dDEVICEHEIGHTPOINTS=504"
*End
*PageSize PhotoTearOff/Photo with tear-off tab: "%% FoomaticRIPOptionSetting: PageSize=PhotoTearOff"
*FoomaticRIPOptionSetting PageSize=PhotoTearOff: " -dDEVICEWIDTHPOINTS&&
=288 -dDEVICEHEIGHTPOINTS=432"
*End
*PageSize 3x5/3x5 inch index card: "%% FoomaticRIPOptionSetting: PageSize=3x5"
*FoomaticRIPOptionSetting PageSize=3x5: " -dDEVICEWIDTHPOINTS=216 -dDE&&
VICEHEIGHTPOINTS=360"
*End
*PageSize 5x8/5x8 inch index card: "%% FoomaticRIPOptionSetting: PageSize=5x8"
*FoomaticRIPOptionSetting PageSize=5x8: " -dDEVICEWIDTHPOINTS=360 -dDE&&
VICEHEIGHTPOINTS=576"
*End
*PageSize A5/A5: "%% FoomaticRIPOptionSetting: PageSize=A5"
*FoomaticRIPOptionSetting PageSize=A5: " -dDEVICEWIDTHPOINTS=420 -dDEV&&
ICEHEIGHTPOINTS=595"
*End
*PageSize A6/A6: "%% FoomaticRIPOptionSetting: PageSize=A6"
*FoomaticRIPOptionSetting PageSize=A6: " -dDEVICEWIDTHPOINTS=297 -dDEV&&
ICEHEIGHTPOINTS=420"
*End
*PageSize A6TearOff/A6 with tear-off tab: "%% FoomaticRIPOptionSetting: PageSize=A6TearOff"
*FoomaticRIPOptionSetting PageSize=A6TearOff: " -dDEVICEWIDTHPOINTS=29&&
7 -dDEVICEHEIGHTPOINTS=420"
*End
*PageSize B5JIS/B5 (JIS): "%% FoomaticRIPOptionSetting: PageSize=B5JIS"
*FoomaticRIPOptionSetting PageSize=B5JIS: " -dDEVICEWIDTHPOINTS=516 -d&&
DEVICEHEIGHTPOINTS=729"
*End
*PageSize Env10/Envelope #10: "%% FoomaticRIPOptionSetting: PageSize=Env10"
*FoomaticRIPOptionSetting PageSize=Env10: " -dDEVICEWIDTHPOINTS=297 -d&&
DEVICEHEIGHTPOINTS=684"
*End
*PageSize EnvC5/Envelope C5: "%% FoomaticRIPOptionSetting: PageSize=EnvC5"
*FoomaticRIPOptionSetting PageSize=EnvC5: " -dDEVICEWIDTHPOINTS=459 -d&&
DEVICEHEIGHTPOINTS=649"
*End
*PageSize EnvC6/Envelope C6: "%% FoomaticRIPOptionSetting: PageSize=EnvC6"
*FoomaticRIPOptionSetting PageSize=EnvC6: " -dDEVICEWIDTHPOINTS=323 -d&&
DEVICEHEIGHTPOINTS=459"
*End
*PageSize EnvDL/Envelope DL: "%% FoomaticRIPOptionSetting: PageSize=EnvDL"
*FoomaticRIPOptionSetting PageSize=EnvDL: " -dDEVICEWIDTHPOINTS=312 -d&&
DEVICEHEIGHTPOINTS=624"
*End
*PageSize EnvISOB5/Envelope B5: "%% FoomaticRIPOptionSetting: PageSize=EnvISOB5"
*FoomaticRIPOptionSetting PageSize=EnvISOB5: " -dDEVICEWIDTHPOINTS=499&&
 -dDEVICEHEIGHTPOINTS=709"
*End
*PageSize EnvMonarch/Envelope Monarch: "%% FoomaticRIPOptionSetting: PageSize=EnvMonarch"
*FoomaticRIPOptionSetting PageSize=EnvMonarch: " -dDEVICEWIDTHPOINTS=2&&
79 -dDEVICEHEIGHTPOINTS=540"
*End
*PageSize Executive/Executive: "%% FoomaticRIPOptionSetting: PageSize=Executive"
*FoomaticRIPOptionSetting PageSize=Executive: " -dDEVICEWIDTHPOINTS=52&&
2 -dDEVICEHEIGHTPOINTS=756"
*End
*PageSize FLSA/American Foolscap: "%% FoomaticRIPOptionSetting: PageSize=FLSA"
*FoomaticRIPOptionSetting PageSize=FLSA: " -dDEVICEWIDTHPOINTS=612 -dD&&
EVICEHEIGHTPOINTS=936"
*End
*PageSize Hagaki/Hagaki: "%% FoomaticRIPOptionSetting: PageSize=Hagaki"
*FoomaticRIPOptionSetting PageSize=Hagaki: " -dDEVICEWIDTHPOINTS=283 -&&
dDEVICEHEIGHTPOINTS=420"
*End
*PageSize Legal/Legal: "%% FoomaticRIPOptionSetting: PageSize=Legal"
*FoomaticRIPOptionSetting PageSize=Legal: " -dDEVICEWIDTHPOINTS=612 -d&&
DEVICEHEIGHTPOINTS=1008"
*End
*PageSize Oufuku/Oufuku-Hagaki: "%% FoomaticRIPOptionSetting: PageSize=Oufuku"
*FoomaticRIPOptionSetting PageSize=Oufuku: " -dDEVICEWIDTHPOINTS=420 -&&
dDEVICEHEIGHTPOINTS=567"
*End
*PageSize w558h774/16K: "%% FoomaticRIPOptionSetting: PageSize=w558h774"
*FoomaticRIPOptionSetting PageSize=w558h774: " -dDEVICEWIDTHPOINTS=558&&
 -dDEVICEHEIGHTPOINTS=774"
*End
*PageSize w612h935/Executive (JIS): "%% FoomaticRIPOptionSetting: PageSize=w612h935"
*FoomaticRIPOptionSetting PageSize=w612h935: " -dDEVICEWIDTHPOINTS=612&&
 -dDEVICEHEIGHTPOINTS=935"
*End
*CloseUI: *PageSize

*OpenUI *PageRegion: PickOne
*OrderDependency: 105 AnySetup *PageRegion
*DefaultPageRegion: Letter
*PageRegion Letter/Letter: "%% FoomaticRIPOptionSetting: PageSize=Letter"
*PageRegion A4/A4: "%% FoomaticRIPOptionSetting: PageSize=A4"
*PageRegion Photo/Photo/4x6 inch index card: "%% FoomaticRIPOptionSetting: PageSize=Photo"
*PageRegion Photo5x7/Photo/5x7 inch index card: "%% FoomaticRIPOptionSetting: PageSize=Photo5x7"
*PageRegion PhotoTearOff/Photo with tear-off tab: "%% FoomaticRIPOptionSetting: PageSize=PhotoTearOff"
*PageRegion 3x5/3x5 inch index card: "%% FoomaticRIPOptionSetting: PageSize=3x5"
*PageRegion 5x8/5x8 inch index card: "%% FoomaticRIPOptionSetting: PageSize=5x8"
*PageRegion A5/A5: "%% FoomaticRIPOptionSetting: PageSize=A5"
*PageRegion A6/A6: "%% FoomaticRIPOptionSetting: PageSize=A6"
*PageRegion A6TearOff/A6 with tear-off tab: "%% FoomaticRIPOptionSetting: PageSize=A6TearOff"
*PageRegion B5JIS/B5 (JIS): "%% FoomaticRIPOptionSetting: PageSize=B5JIS"
*PageRegion Env10/Envelope #10: "%% FoomaticRIPOptionSetting: PageSize=Env10"
*PageRegion EnvC5/Envelope C5: "%% FoomaticRIPOptionSetting: PageSize=EnvC5"
*PageRegion EnvC6/Envelope C6: "%% FoomaticRIPOptionSetting: PageSize=EnvC6"
*PageRegion EnvDL/Envelope DL: "%% FoomaticRIPOptionSetting: PageSize=EnvDL"
*PageRegion EnvISOB5/Envelope B5: "%% FoomaticRIPOptionSetting: PageSize=EnvISOB5"
*PageRegion EnvMonarch/Envelope Monarch: "%% FoomaticRIPOptionSetting: PageSize=EnvMonarch"
*PageRegion Executive/Executive: "%% FoomaticRIPOptionSetting: PageSize=Executive"
*PageRegion FLSA/American Foolscap: "%% FoomaticRIPOptionSetting: PageSize=FLSA"
*PageRegion Hagaki/Hagaki: "%% FoomaticRIPOptionSetting: PageSize=Hagaki"
*PageRegion Legal/Legal: "%% FoomaticRIPOptionSetting: PageSize=Legal"
*PageRegion Oufuku/Oufuku-Hagaki: "%% FoomaticRIPOptionSetting: PageSize=Oufuku"
*PageRegion w558h774/16K: "%% FoomaticRIPOptionSetting: PageSize=w558h774"
*PageRegion w612h935/Executive (JIS): "%% FoomaticRIPOptionSetting: PageSize=w612h935"
*CloseUI: *PageRegion

*DefaultImageableArea: Letter
*ImageableArea Letter/Letter: "18 36 594 783"
*ImageableArea A4/A4: "9.72 36 585.28 833"
*ImageableArea Photo/Photo/4x6 inch index card: "0 36 288 432"
*ImageableArea Photo5x7/Photo/5x7 inch index card: "0 36 360 504"
*ImageableArea PhotoTearOff/Photo with tear-off tab: "0 0 288 432"
*ImageableArea 3x5/3x5 inch index card: "0 36 216 360"
*ImageableArea 5x8/5x8 inch index card: "0 36 360 576"
*ImageableArea A5/A5: "9 36 411 586"
*ImageableArea A6/A6: "0 36 297 420"
*ImageableArea A6TearOff/A6 with tear-off tab: "0 0 297 420"
*ImageableArea B5JIS/B5 (JIS): "18 36 498 720"
*ImageableArea Env10/Envelope #10: "0 36 297 684"
*ImageableArea EnvC5/Envelope C5: "18 36 441 640"
*ImageableArea EnvC6/Envelope C6: "0 36 323 459"
*ImageableArea EnvDL/Envelope DL: "0 36 312 624"
*ImageableArea EnvISOB5/Envelope B5: "18 36 481 700"
*ImageableArea EnvMonarch/Envelope Monarch: "0 36 279 540"
*ImageableArea Executive/Executive: "18 36 504 747"
*ImageableArea FLSA/American Foolscap: "18 36 594 927"
*ImageableArea Hagaki/Hagaki: "0 36 283 420"
*ImageableArea Legal/Legal: "18 36 594 999"
*ImageableArea Oufuku/Oufuku-Hagaki: "0 36 420 567"
*ImageableArea w558h774/16K: "18 36 540 765"
*ImageableArea w612h935/Executive (JIS): "18 36 594 926"

*DefaultPaperDimension: Letter
*PaperDimension Letter/Letter: "612 792"
*PaperDimension A4/A4: "595 842"
*PaperDimension Photo/Photo/4x6 inch index card: "288 432"
*PaperDimension Photo5x7/Photo/5x7 inch index card: "360 504"
*PaperDimension PhotoTearOff/Photo with tear-off tab: "288 432"
*PaperDimension 3x5/3x5 inch index card: "216 360"
*PaperDimension 5x8/5x8 inch index card: "360 576"
*PaperDimension A5/A5: "420 595"
*PaperDimension A6/A6: "297 420"
*PaperDimension A6TearOff/A6 with tear-off tab: "297 420"
*PaperDimension B5JIS/B5 (JIS): "516 729"
*PaperDimension Env10/Envelope #10: "297 684"
*PaperDimension EnvC5/Envelope C5: "459 649"
*PaperDimension EnvC6/Envelope C6: "323 459"
*PaperDimension EnvDL/Envelope DL: "312 624"
*PaperDimension EnvISOB5/Envelope B5: "499 709"
*PaperDimension EnvMonarch/Envelope Monarch: "279 540"
*PaperDimension Executive/Executive: "522 756"
*PaperDimension FLSA/American Foolscap: "612 936"
*PaperDimension Hagaki/Hagaki: "283 420"
*PaperDimension Legal/Legal: "612 1008"
*PaperDimension Oufuku/Oufuku-Hagaki: "420 567"
*PaperDimension w558h774/16K: "558 774"
*PaperDimension w612h935/Executive (JIS): "612 935"

*OpenUI *InputSlot/Media Source: PickOne
*FoomaticRIPOption InputSlot: enum CmdLine C
*OrderDependency: 100 AnySetup *InputSlot
*DefaultInputSlot: Default
*InputSlot Default/Printer default: "%% FoomaticRIPOptionSetting: InputSlot=Default"
*FoomaticRIPOptionSetting InputSlot=Default: ",PS:MediaPosition=7"
*InputSlot PhotoTray/Photo Tray: "%% FoomaticRIPOptionSetting: InputSlot=PhotoTray"
*FoomaticRIPOptionSetting InputSlot=PhotoTray: ",PS:MediaPosition=6"
*InputSlot Upper/Upper Tray: "%% FoomaticRIPOptionSetting: InputSlot=Upper"
*FoomaticRIPOptionSetting InputSlot=Upper: ",PS:MediaPosition=1"
*InputSlot Lower/Lower Tray: "%% FoomaticRIPOptionSetting: InputSlot=Lower"
*FoomaticRIPOptionSetting InputSlot=Lower: ",PS:MediaPosition=4"
*InputSlot Envelope/Envelope Feeder: "%% FoomaticRIPOptionSetting: InputSlot=Envelope"
*FoomaticRIPOptionSetting InputSlot=Envelope: ",PS:MediaPosition=3"
*InputSlot LargeCapacity/Large Capacity Tray: "%% FoomaticRIPOptionSetting: InputSlot=LargeCapacity"
*FoomaticRIPOptionSetting InputSlot=LargeCapacity: ",PS:MediaPosition=&&
5"
*End
*InputSlot Manual/Manual Feeder: "%% FoomaticRIPOptionSetting: InputSlot=Manual"
*FoomaticRIPOptionSetting InputSlot=Manual: ",PS:MediaPosition=2"
*InputSlot MPTray/Multi Purpose Tray: "%% FoomaticRIPOptionSetting: InputSlot=MPTray"
*FoomaticRIPOptionSetting InputSlot=MPTray: ",PS:MediaPosition=8"
*CloseUI: *InputSlot

*OpenUI *Duplex/Double-Sided Printing: PickOne
*FoomaticRIPOption Duplex: enum CmdLine A
*OrderDependency: 120 AnySetup *Duplex
*DefaultDuplex: None
*Duplex DuplexNoTumble/Long Edge (Standard): "%% FoomaticRIPOptionSetting: Duplex=DuplexNoTumble"
*FoomaticRIPOptionSetting Duplex=DuplexNoTumble: " -dDuplex=true -dTum&&
ble=false"
*End
*Duplex DuplexTumble/Short Edge (Flip): "%% FoomaticRIPOptionSetting: Duplex=DuplexTumble"
*FoomaticRIPOptionSetting Duplex=DuplexTumble: " -dDuplex=true -dTumbl&&
e=true"
*End
*Duplex None/Off: "%% FoomaticRIPOptionSetting: Duplex=None"
*FoomaticRIPOptionSetting Duplex=None: " -dDuplex=false"
*CloseUI: *Duplex

*CloseGroup: General

*OpenGroup: PrintoutMode/Printout Mode

*OpenUI *Quality/Resolution, Quality, Ink Type, Media Type: PickOne
*FoomaticRIPOption Quality: enum CmdLine B
*OrderDependency: 100 AnySetup *Quality
*DefaultQuality: FromPrintoutMode
*Quality FromPrintoutMode/Controlled by 'Printout Mode': "%% FoomaticRIPOptionSetting: Quality=@PrintoutMode"
*Quality 300ColorCMYK/300 dpi, Color, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=300ColorCMYK"
*FoomaticRIPOptionSetting Quality=300ColorCMYK: " -r300 -sIjsParams=Qu&&
ality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet&&
=2"
*End
*Quality 300ColorCMYKFullBleed/300 dpi, Color, Full Bleed, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=300ColorCMYKFullBleed"
*FoomaticRIPOptionSetting Quality=300ColorCMYKFullBleed: " -r300 -sIjs&&
Params=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quali&&
ty:PenSet=2,Quality:FullBleed=1"
*End
*Quality 300DraftColorCMYK/300 dpi, Draft, Color, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=300DraftColorCMYK"
*FoomaticRIPOptionSetting Quality=300DraftColorCMYK: " -r300 -sIjsPara&&
ms=Quality:Quality=1,Quality:ColorMode=2,Quality:MediaType=0,Quality:P&&
enSet=2"
*End
*Quality 300DraftGrayscaleCMYK/300 dpi, Draft, Grayscale, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=300DraftGrayscaleCMYK"
*FoomaticRIPOptionSetting Quality=300DraftGrayscaleCMYK: " -r300 -sIjs&&
Params=Quality:Quality=1,Quality:ColorMode=0,Quality:MediaType=0,Quali&&
ty:PenSet=2"
*End
*Quality 300FastDraftColorCMYK/300 dpi, FastDraft, Color, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=300FastDraftColorCMYK"
*FoomaticRIPOptionSetting Quality=300FastDraftColorCMYK: " -r300 -sIjs&&
Params=Quality:Quality=4,Quality:ColorMode=2,Quality:MediaType=0,Quali&&
ty:PenSet=2"
*End
*Quality 300FastDraftGrayscaleCMYK/300 dpi, FastDraft, Grayscale, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=300FastDraftGrayscaleCMYK"
*FoomaticRIPOptionSetting Quality=300FastDraftGrayscaleCMYK: " -r300 -&&
sIjsParams=Quality:Quality=4,Quality:ColorMode=0,Quality:MediaType=0,Q&&
uality:PenSet=2"
*End
*Quality 300GrayscaleCMYK/300 dpi, Grayscale, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=300GrayscaleCMYK"
*FoomaticRIPOptionSetting Quality=300GrayscaleCMYK: " -r300 -sIjsParam&&
s=Quality:Quality=0,Quality:ColorMode=0,Quality:MediaType=0,Quality:Pe&&
nSet=2"
*End
*Quality 600ColorCMYK/600 dpi, Color, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=600ColorCMYK"
*FoomaticRIPOptionSetting Quality=600ColorCMYK: " -r600 -sIjsParams=Qu&&
ality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet&&
=2"
*End
*Quality 600ColorCMYKFullBleed/600 dpi, Color, Full Bleed, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=600ColorCMYKFullBleed"
*FoomaticRIPOptionSetting Quality=600ColorCMYKFullBleed: " -r600 -sIjs&&
Params=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quali&&
ty:PenSet=2,Quality:FullBleed=1"
*End
*Quality 600GrayscaleCMYK/600 dpi, Grayscale, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=600GrayscaleCMYK"
*FoomaticRIPOptionSetting Quality=600GrayscaleCMYK: " -r600 -sIjsParam&&
s=Quality:Quality=0,Quality:ColorMode=0,Quality:MediaType=0,Quality:Pe&&
nSet=2"
*End
*Quality 1200PhotoCMYK/1200 dpi, Photo, Black + Color Cartr., Photo Paper: "%% FoomaticRIPOptionSetting: Quality=1200PhotoCMYK"
*FoomaticRIPOptionSetting Quality=1200PhotoCMYK: " -r1200 -sIjsParams=&&
Quality:Quality=3,Quality:ColorMode=2,Quality:MediaType=2,Quality:PenS&&
et=2"
*End
*Quality 1200PhotoCMYKFullBleed/1200 dpi, Photo, Full Bleed, Black + Color Cartr., Photo Paper: "%% FoomaticRIPOptionSetting: Quality=1200PhotoCMYKFullBleed"
*FoomaticRIPOptionSetting Quality=1200PhotoCMYKFullBleed: " -r1200 -sI&&
jsParams=Quality:Quality=3,Quality:ColorMode=2,Quality:MediaType=2,Qua&&
lity:PenSet=2,Quality:FullBleed=1"
*End
*CloseUI: *Quality

*CloseGroup: PrintoutMode


*% Generic boilerplate PPD stuff as standard PostScript fonts and so on

*DefaultFont: Courier
*Font AvantGarde-Book: Standard "(001.006S)" Standard ROM
*Font AvantGarde-BookOblique: Standard "(001.006S)" Standard ROM
*Font AvantGarde-Demi: Standard "(001.007S)" Standard ROM
*Font AvantGarde-DemiOblique: Standard "(001.007S)" Standard ROM
*Font Bookman-Demi: Standard "(001.004S)" Standard ROM
*Font Bookman-DemiItalic: Standard "(001.004S)" Standard ROM
*Font Bookman-Light: Standard "(001.004S)" Standard ROM
*Font Bookman-LightItalic: Standard "(001.004S)" Standard ROM
*Font Courier: Standard "(002.004S)" Standard ROM
*Font Courier-Bold: Standard "(002.004S)" Standard ROM
*Font Courier-BoldOblique: Standard "(002.004S)" Standard ROM
*Font Courier-Oblique: Standard "(002.004S)" Standard ROM
*Font Helvetica: Standard "(001.006S)" Standard ROM
*Font Helvetica-Bold: Standard "(001.007S)" Standard ROM
*Font Helvetica-BoldOblique: Standard "(001.007S)" Standard ROM
*Font Helvetica-Narrow: Standard "(001.006S)" Standard ROM
*Font Helvetica-Narrow-Bold: Standard "(001.007S)" Standard ROM
*Font Helvetica-Narrow-BoldOblique: Standard "(001.007S)" Standard ROM
*Font Helvetica-Narrow-Oblique: Standard "(001.006S)" Standard ROM
*Font Helvetica-Oblique: Standard "(001.006S)" Standard ROM
*Font NewCenturySchlbk-Bold: Standard "(001.009S)" Standard ROM
*Font NewCenturySchlbk-BoldItalic: Standard "(001.007S)" Standard ROM
*Font NewCenturySchlbk-Italic: Standard "(001.006S)" Standard ROM
*Font NewCenturySchlbk-Roman: Standard "(001.007S)" Standard ROM
*Font Palatino-Bold: Standard "(001.005S)" Standard ROM
*Font Palatino-BoldItalic: Standard "(001.005S)" Standard ROM
*Font Palatino-Italic: Standard "(001.005S)" Standard ROM
*Font Palatino-Roman: Standard "(001.005S)" Standard ROM
*Font Symbol: Special "(001.007S)" Special ROM
*Font Times-Bold: Standard "(001.007S)" Standard ROM
*Font Times-BoldItalic: Standard "(001.009S)" Standard ROM
*Font Times-Italic: Standard "(001.007S)" Standard ROM
*Font Times-Roman: Standard "(001.007S)" Standard ROM
*Font ZapfChancery-MediumItalic: Standard "(001.007S)" Standard ROM
*Font ZapfDingbats: Special "(001.004S)" Standard ROM
```

$ ls -l /etc/cups/printers.conf```

-rw------- 1 cupsys lp 340 2006-10-26 09:33 /etc/cups/printers.conf
```
$ ls -l /etc/cups/ppd/DeskJet-5740.ppd```

-rw-r--r-- 1 cupsys lp 21956 2006-10-26 09:35 /etc/cups/ppd/DeskJet-5740.ppd
```

Started OOo Writer (it was not running)
Can't find HP Deskjet 5740 printer, only Generic Printer there.  Printing failed.

As user

on console ran;
$ gnome-cups-manager```

.....
Selected ppd file = linuxprinting.org-gs-builtin/HP/HP-DeskJet-pcl3.ppd
Selected ppd file = hpijs/HP/HP-DeskJet_5740-hpijs.ppd

** (gnome-cups-add:7664): WARNING **: IPP request failed with status 1280
```

Failed adding printer.


As root
on console ran;
# gnome-cups-manager```

.....
Selected ppd file = linuxprinting.org-gs-builtin/HP/HP-DeskJet-pcl3.ppd
Selected ppd file = hpijs/HP/HP-DeskJet_5740-hpijs.ppd

** (gnome-cups-add:7842): WARNING **: IPP request failed with status 1280

```

Still failed adding printer

---

### Post by mssever on 2006-10-25
You restarted cups, right? (sudo /etc/init.d/cupsys restart)

I just noticed that you mentioned the live CD. Is that what you're running? If so, that could be your problem. A critical part of the printer installation process might be located on a read-only part of the filesystem (since CDs are read-only). Not everything on the live CD is identical to an actual install. In that case, I'm quite sure you'll have no trouble setting up your printer once you install. HP printer setup in Ubuntu is easier than in Windows. I had no trouble setting up your printer model (except that I don't actually have the printer--I have a different model HP).

---

### Post by satimis on 2006-10-26
Hi mssever,

> You restarted cups, right? (sudo /etc/init.d/cupsys restart)
Yes, following your steps.

> I just noticed that you mentioned the live CD. Is that what you're running? If so, that could be your problem. A critical part of the printer installation process might be located on a read-only part of the filesystem (since CDs are read-only)....
Yes, I ran Ubuntu LiveCD occasionally. I'm installing/config Ubunt-LAMP-server w/o X.  I got problem on browsing Internet and read Webmail.  Therefore I run LiveCD to overcome browsing problem.

Previoulsy I ran Knoppix LiveCD which can print w/o problem.  So I thought Ubuntu LiveCD should work the same.  Printing features are on gnome desktop menu.

Anyway tks again for your effort advising me and your time spent.

B.R.
satimis

---

### Post by mssever on 2006-10-26
I'm sorry I haven't been able to help you get your printer working. It's odd that you're having these problems. If I think of anything else to try, I'll post back.

Oh...one last suggestion. If you install elinks or a something similar, you can have a web browser without running X. You might try booting normally and using elinks to install the printer via [http://localhost:631](http://localhost:631).

---

### Post by satimis on 2006-10-26
Hi mssever,

Disregarding the failure in setup HP printer, I'm much appreciated for your assistance.

> Oh...one last suggestion. If you install elinks or a something similar, you can have a web browser without running X. You might try booting normally and using elinks to install the printer via [http://localhost:631](http://localhost:631).
I suppose you referred to the browser problem on my server.

I have w3m and lynx, the text-browser, running on the server.  However I can't login on them to read webmails on yahoo mail and gmail.  On login;

1) w3m
complaining;```

unable to get local issuer Certicate-Accept? y/n
Selecting either of them popup
Can't load r/m1

```


2) lynx
Complaining;```

SSL error: Can't find common name in Certificate-Continue (y)

```
Accepted OR rejected went the same result-login failed.

I'm still looking around for solution.  openSSL not setup properly???   I haven't configured the server yet.


However it is quite funny.  Both w3m and lynx worked on Ubuntu 6.06 LiveCD seamlessly.

Remark:
w3m - default installtion on LiveCD
lynx - I ran "apt-get install lynx" to install it on running LiveCD.


Ah, one further question.  How to check whether cups is running?  Tks


B.R.
satimis

---

### Post by mssever on 2006-10-26
> **satimis said:**
> I suppose you referred to the browser problem on my server.

I have w3m and lynx, the text-browser, running on the server.  However I can't login on them to read webmails on yahoo mail and gmail.  On login;

1) w3m
complaining;```

unable to get local issuer Certicate-Accept? y/n
Selecting either of them popup
Can't load r/m1

```2) lynx
Complaining;```

SSL error: Can't find common name in Certificate-Continue (y)

```Accepted OR rejected went the same result-login failed.

I'm still looking around for solution.  openSSL not setup properly???   I haven't configured the server yet.


However it is quite funny.  Both w3m and lynx worked on Ubuntu 6.06 LiveCD seamlessly.

Remark:
w3m - default installtion on LiveCD
lynx - I ran "apt-get install lynx" to install it on running LiveCD.

Interesting. Elinks is yet another text-mode web browser, but it's more modern than the others. Try installing it (sudo apt-get install elinks). Add gpm to the mix if you want to use your mouse from the console with it (elinks even supports the mouse wheel). If you use a terminal emulater like gnome-terminal, you can use your mouse without installing anything extra.

You shouldn't have to install or configure anything manually to be able to browse SSL sites.
> Ah, one further question.  How to check whether cups is running?  Tks


B.R.
satimis```
ps -ef
``` lists all the currently-running processes. Since that list is long, pipe it through grep, which returns only those lines matching the specified regular expression. So, to see if cups is running, type ```
ps -ef | grep cups
```Enclose the regex in single quotes if it contains anything other than letters and numbers.

---

