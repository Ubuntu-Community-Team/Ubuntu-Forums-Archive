---
title: "How to set Printer margin to 0 in EPSON PLQ-20 printer?"
date: 2016-06-09
forum: Hardware
---

### Post by Kasun2005 on 2016-06-09
Hi All,

I'm new to Ubuntu. I'm using Ubuntu 14.04 desktop version. i'm unable to set printer margin in EPSON PLQ-20 printer. The printer .ppd file text shown below.

If anyone could help me to set printer margin 0. Please...... Tell me how to do it.... please.......:confused::confused::confused:




*PPD-Adobe: "4.3"
*%
*% For information on using this, and to obtain the required backend
*% script, consult [http://www.openprinting.org/](http://www.openprinting.org/)
*%
*% This file is published under the GNU General Public License
*%
*% PPD-O-MATIC (4.0.0 or newer) generated this PPD file. It is for use with 
*% all programs and environments which use PPD files for dealing with
*% printer capability information. The printer must be configured with the
*% "foomatic-rip" backend filter script of Foomatic 4.0.0 or newer. This 
*% file and "foomatic-rip" work together to support PPD-controlled printer
*% driver option access with all supported printer drivers and printing
*% spoolers.
*%
*% To save this file on your disk, wait until the download has completed
*% (the animation of the browser logo must stop) and then use the
*% "Save as..." command in the "File" menu of your browser or in the 
*% pop-up manu when you click on this document with the right mouse button.
*% DO NOT cut and paste this file into an editor with your mouse. This can
*% introduce additional line breaks which lead to unexpected results.
*%
*% You may save this file as 'Epson-Dot_Matrix-epsonc.ppd'
*%
*%
*FormatVersion:    "4.3"
*FileVersion:    "1.1"
*LanguageVersion: English 
*LanguageEncoding: ISOLatin1
*PCFileName:    "EPSONC.PPD"
*Manufacturer:    "Epson"
*Product:    "(Dot Matrix)"
*cupsVersion:    1.0
*cupsManualCopies: True
*cupsModelNumber:  2
*cupsFilter:    "application/vnd.cups-postscript 100 foomatic-rip"
*cupsFilter:    "application/vnd.cups-pdf 0 foomatic-rip"
*%pprRIP:        foomatic-rip other
*ModelName:     "Epson Dot Matrix"
*ShortNickName: "Epson Dot Matrix epsonc"
*NickName:      "Epson Dot Matrix Foomatic/epsonc (recommended)"
*PSVersion:    "(3010.000) 550"
*PSVersion:    "(3010.000) 651"
*PSVersion:    "(3010.000) 652"
*PSVersion:    "(3010.000) 653"
*PSVersion:    "(3010.000) 704"
*PSVersion:    "(3010.000) 705"
*PSVersion:    "(3010.000) 800"
*PSVersion:    "(3010.000) 815"
*PSVersion:    "(3010.000) 850"
*PSVersion:    "(3010.000) 860"
*PSVersion:    "(3010.000) 861"
*PSVersion:    "(3010.000) 862"
*PSVersion:    "(3010.000) 863"
*PSVersion:    "(3010.000) 864"
*PSVersion:    "(3010.000) 870"
*LanguageLevel:    "3"
*ColorDevice:    False
*DefaultColorSpace: Gray
*FileSystem:    False
*Throughput:    "1"
*LandscapeOrientation: Plus90
*TTRasterizer:    Type42
*1284DeviceID: "DRV:Depsonc,R1,M0,TG;"

*driverName epsonc: ""
*driverType G/Ghostscript built-in: ""
*driverUrl: "http://www.ghostscript.com/"
*driverObsolete: False
*driverManufacturerSupplied: False




*HWMargins: 18 36 18 36
*VariablePaperSize: True
*MaxMediaWidth: 100000
*MaxMediaHeight: 100000
*NonUIOrderDependency: 100 AnySetup *CustomPageSize
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

*FoomaticIDs: Epson-Dot_Matrix epsonc
*FoomaticRIPCommandLine: "gs -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPA&&
USE -sDEVICE=epsonc%A%Z -sOutputFile=- -"
*End

*OpenGroup: General/General

*OpenUI *PageSize/Page Size: PickOne
*FoomaticRIPOption PageSize: enum CmdLine A
*OrderDependency: 100 AnySetup *PageSize
*DefaultPageSize: A4
*PageSize Letter/US Letter: "%% FoomaticRIPOptionSetting: PageSize=Letter"
*FoomaticRIPOptionSetting PageSize=Letter: " -dDEVICEWIDTHPOINTS=612 -&&
dDEVICEHEIGHTPOINTS=792"
*End
*PageSize A4/A4: "%% FoomaticRIPOptionSetting: PageSize=A4"
*FoomaticRIPOptionSetting PageSize=A4: " -dDEVICEWIDTHPOINTS=595 -dDEV&&
ICEHEIGHTPOINTS=842"
*End
*PageSize 3x5/3x5: "%% FoomaticRIPOptionSetting: PageSize=3x5"
*FoomaticRIPOptionSetting PageSize=3x5: " -dDEVICEWIDTHPOINTS=216 -dDE&&
VICEHEIGHTPOINTS=360"
*End
*PageSize 4x6/4x6: "%% FoomaticRIPOptionSetting: PageSize=4x6"
*FoomaticRIPOptionSetting PageSize=4x6: " -dDEVICEWIDTHPOINTS=288 -dDE&&
VICEHEIGHTPOINTS=432"
*End
*PageSize 5x7/5x7: "%% FoomaticRIPOptionSetting: PageSize=5x7"
*FoomaticRIPOptionSetting PageSize=5x7: " -dDEVICEWIDTHPOINTS=360 -dDE&&
VICEHEIGHTPOINTS=504"
*End
*PageSize 5x8/5x8: "%% FoomaticRIPOptionSetting: PageSize=5x8"
*FoomaticRIPOptionSetting PageSize=5x8: " -dDEVICEWIDTHPOINTS=360 -dDE&&
VICEHEIGHTPOINTS=576"
*End
*PageSize 6x8/6x8: "%% FoomaticRIPOptionSetting: PageSize=6x8"
*FoomaticRIPOptionSetting PageSize=6x8: " -dDEVICEWIDTHPOINTS=432 -dDE&&
VICEHEIGHTPOINTS=576"
*End0
*PageSize 8x8/8x8: "%% FoomaticRIPOptionSetting: PageSize=8x8"
*FoomaticRIPOptionSetting PageSize=8x8: " -dDEVICEWIDTHPOINTS=576 -dDE&&
VICEHEIGHTPOINTS=576"
*End0
*PageSize 8x10/8x10: "%% FoomaticRIPOptionSetting: PageSize=8x10"
*FoomaticRIPOptionSetting PageSize=8x10: " -dDEVICEWIDTHPOINTS=576 -dD&&
EVICEHEIGHTPOINTS=720"
*End
*PageSize 8x12/8x12: "%% FoomaticRIPOptionSetting: PageSize=8x12"
*FoomaticRIPOptionSetting PageSize=8x12: " -dDEVICEWIDTHPOINTS=576 -dD&&
EVICEHEIGHTPOINTS=864"
*End
*PageSize 11x14/11x14: "%% FoomaticRIPOptionSetting: PageSize=11x14"
*FoomaticRIPOptionSetting PageSize=11x14: " -dDEVICEWIDTHPOINTS=792 -d&&
DEVICEHEIGHTPOINTS=1008"
*End
*PageSize 13x19/13x19: "%% FoomaticRIPOptionSetting: PageSize=13x19"
*FoomaticRIPOptionSetting PageSize=13x19: " -dDEVICEWIDTHPOINTS=936 -d&&
DEVICEHEIGHTPOINTS=1368"
*End
*PageSize 16x20/16x20: "%% FoomaticRIPOptionSetting: PageSize=16x20"
*FoomaticRIPOptionSetting PageSize=16x20: " -dDEVICEWIDTHPOINTS=1152 -&&
dDEVICEHEIGHTPOINTS=1440"
*End
*PageSize 16x24/16x24: "%% FoomaticRIPOptionSetting: PageSize=16x24"
*FoomaticRIPOptionSetting PageSize=16x24: " -dDEVICEWIDTHPOINTS=1152 -&&
dDEVICEHEIGHTPOINTS=1728"
*End
*PageSize A3/A3: "%% FoomaticRIPOptionSetting: PageSize=A3"
*FoomaticRIPOptionSetting PageSize=A3: " -dDEVICEWIDTHPOINTS=842 -dDEV&&
ICEHEIGHTPOINTS=1191"
*End
*PageSize Legal/US Legal: "%% FoomaticRIPOptionSetting: PageSize=Legal"
*FoomaticRIPOptionSetting PageSize=Legal: " -dDEVICEWIDTHPOINTS=612 -d&&
DEVICEHEIGHTPOINTS=1008"
*End
*CloseUI: *PageSize

*OpenUI *PageRegion: PickOne
*OrderDependency: 100 AnySetup *PageRegion
*DefaultPageRegion: A4
*PageRegion Letter/US Letter: "%% FoomaticRIPOptionSetting: PageSize=Letter"
*PageRegion A4/A4: "%% FoomaticRIPOptionSetting: PageSize=A4"
*PageRegion 3x5/3x5: "%% FoomaticRIPOptionSetting: PageSize=3x5"
*PageRegion 4x6/4x6: "%% FoomaticRIPOptionSetting: PageSize=4x6"
*PageRegion 5x7/5x7: "%% FoomaticRIPOptionSetting: PageSize=5x7"
*PageRegion 5x8/5x8: "%% FoomaticRIPOptionSetting: PageSize=5x8"
*PageRegion 6x8/6x8: "%% FoomaticRIPOptionSetting: PageSize=6x8"
*PageRegion 8x8/8x8: "%% FoomaticRIPOptionSetting: PageSize=8x8"
*PageRegion 8x10/8x10: "%% FoomaticRIPOptionSetting: PageSize=8x10"
*PageRegion 8x12/8x12: "%% FoomaticRIPOptionSetting: PageSize=8x12"
*PageRegion 11x14/11x14: "%% FoomaticRIPOptionSetting: PageSize=11x14"
*PageRegion 13x19/13x19: "%% FoomaticRIPOptionSetting: PageSize=13x19"
*PageRegion 16x20/16x20: "%% FoomaticRIPOptionSetting: PageSize=16x20"
*PageRegion 16x24/16x24: "%% FoomaticRIPOptionSetting: PageSize=16x24"
*PageRegion A3/A3: "%% FoomaticRIPOptionSetting: PageSize=A3"
*PageRegion Legal/US Legal: "%% FoomaticRIPOptionSetting: PageSize=Legal"
*CloseUI: *PageRegion

*DefaultImageableArea: A4
*ImageableArea Letter/US Letter: "18 36 594 756"
*ImageableArea A4/A4: "18 36 577 806"
*ImageableArea 3x5/3x5: "18 36 198 324"
*ImageableArea 4x6/4x6: "18 36 270 396"
*ImageableArea 5x7/5x7: "18 36 342 468"
*ImageableArea 5x8/5x8: "18 36 342 540"
*ImageableArea 6x8/6x8: "18 36 414 540"
*ImageableArea 8x8/8x8: "18 36 558 540"
*ImageableArea 8x10/8x10: "18 36 558 684"
*ImageableArea 8x12/8x12: "18 36 558 828"
*ImageableArea 11x14/11x14: "18 36 774 972"
*ImageableArea 13x19/13x19: "18 36 918 1332"
*ImageableArea 16x20/16x20: "18 36 1134 1404"
*ImageableArea 16x24/16x24: "18 36 1134 1692"
*ImageableArea A3/A3: "18 36 824 1155"
*ImageableArea Legal/US Legal: "18 36 594 972"

*DefaultPaperDimension: A4
*PaperDimension Letter/US Letter: "612 792"
*PaperDimension A4/A4: "595 842"
*PaperDimension 3x5/3x5: "216 360"
*PaperDimension 4x6/4x6: "288 432"
*PaperDimension 5x7/5x7: "360 504"
*PaperDimension 5x8/5x8: "360 576"
*PaperDimension 6x8/6x8: "432 576"
*PaperDimension 8x8/8x8: "576 576"
*PaperDimension 8x10/8x10: "576 720"
*PaperDimension 8x12/8x12: "576 864"
*PaperDimension 11x14/11x14: "792 1008"
*PaperDimension 13x19/13x19: "936 1368"
*PaperDimension 16x20/16x20: "1152 1440"
*PaperDimension 16x24/16x24: "1152 1728"
*PaperDimension A3/A3: "842 1191"
*PaperDimension Legal/US Legal: "612 1008"

*OpenUI *Resolution/Resolution: PickOne
*FoomaticRIPOption Resolution: enum CmdLine A
*OrderDependency: 100 AnySetup *Resolution
*DefaultResolution: 120x180dpi
*Resolution 60x60dpi/60x60 dpi: "%% FoomaticRIPOptionSetting: Resolution=60x60dpi"
*FoomaticRIPOptionSetting Resolution=60x60dpi: " -r60x60"
*Resolution 60x72dpi/60x72 dpi: "%% FoomaticRIPOptionSetting: Resolution=60x72dpi"
*FoomaticRIPOptionSetting Resolution=60x72dpi: " -r60x72"
*Resolution 60x180dpi/60x180 dpi: "%% FoomaticRIPOptionSetting: Resolution=60x180dpi"
*FoomaticRIPOptionSetting Resolution=60x180dpi: " -r60x180"
*Resolution 60x216dpi/60x216 dpi: "%% FoomaticRIPOptionSetting: Resolution=60x216dpi"
*FoomaticRIPOptionSetting Resolution=60x216dpi: " -r60x216"
*Resolution 120x60dpi/120x60 dpi: "%% FoomaticRIPOptionSetting: Resolution=120x60dpi"
*FoomaticRIPOptionSetting Resolution=120x60dpi: " -r120x60"
*Resolution 120x72dpi/120x72 dpi: "%% FoomaticRIPOptionSetting: Resolution=120x72dpi"
*FoomaticRIPOptionSetting Resolution=120x72dpi: " -r120x72"
*Resolution 120x180dpi/120x180 dpi: "%% FoomaticRIPOptionSetting: Resolution=120x180dpi"
*FoomaticRIPOptionSetting Resolution=120x180dpi: " -r120x180"
*Resolution 120x216dpi/120x216 dpi: "%% FoomaticRIPOptionSetting: Resolution=120x216dpi"
*FoomaticRIPOptionSetting Resolution=120x216dpi: " -r120x216"
*Resolution 180x60dpi/180x60 dpi: "%% FoomaticRIPOptionSetting: Resolution=180x60dpi"
*FoomaticRIPOptionSetting Resolution=180x60dpi: " -r180x60"
*Resolution 180x72dpi/180x72 dpi: "%% FoomaticRIPOptionSetting: Resolution=180x72dpi"
*FoomaticRIPOptionSetting Resolution=180x72dpi: " -r180x72"
*Resolution 180x180dpi/180x180 dpi: "%% FoomaticRIPOptionSetting: Resolution=180x180dpi"
*FoomaticRIPOptionSetting Resolution=180x180dpi: " -r180x180"
*Resolution 180x216dpi/180x216 dpi: "%% FoomaticRIPOptionSetting: Resolution=180x216dpi"
*FoomaticRIPOptionSetting Resolution=180x216dpi: " -r180x216"
*Resolution 240x60dpi/240x60 dpi: "%% FoomaticRIPOptionSetting: Resolution=240x60dpi"
*FoomaticRIPOptionSetting Resolution=240x60dpi: " -r240x60"
*Resolution 240x72dpi/240x72 dpi: "%% FoomaticRIPOptionSetting: Resolution=240x72dpi"
*FoomaticRIPOptionSetting Resolution=240x72dpi: " -r240x72"
*Resolution 240x180dpi/240x180 dpi: "%% FoomaticRIPOptionSetting: Resolution=240x180dpi"
*FoomaticRIPOptionSetting Resolution=240x180dpi: " -r240x180"
*Resolution 240x216dpi/240x216 dpi: "%% FoomaticRIPOptionSetting: Resolution=240x216dpi"
*FoomaticRIPOptionSetting Resolution=240x216dpi: " -r240x216"
*CloseUI: *Resolution

*CloseGroup: General


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

---

