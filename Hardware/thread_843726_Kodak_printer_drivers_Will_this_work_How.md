---
title: "Kodak printer drivers? Will this work? How?"
date: 2008-06-28
forum: Hardware
---

### Post by daytonageeks on 2008-06-28
Found this in another thread - can someone explain how to implement this, or if it will work, please?
Blessings,
            daytonageeks (Jim)



Old  April 7th, 2008   	   #7
bathmat
First Cup of Ubuntu
 
Join Date: Apr 2008
Posts: 1
Thanks: 0
Thanked 0 Times in 0 Posts
	
Re: kodak printer driver
*PPD-Adobe: "4.3"
*%PPD file for CUPS/Gimp-Print.
*%Copyright 1993-2001 by Easy Software Products, All Rights Reserved.
*%This PPD file may be freely used and distributed under the terms of
*%the GNU GPL.

*FormatVersion: "4.3"
*FileVersion: "1.1.0"
*LanguageVersion: English
*LanguageEncoding: UTF-8
*PCFileName: "KD_5X00.PPD"

*Manufacturer: "Kodak"
*Product: "(Eastman Kodak Company KODAK 5100 AiO)"
*Product: "(Eastman Kodak Company KODAK 5300 AiO)"
*Product: "(Eastman Kodak Company KODAK 5500 AiO)"
*ModelName: "KODAK EASYSHARE 5000 Series AiO Printer"
*ShortNickName: "KODAK 5X00 AiO"
*% To simply the Home Center code, the US English Nickname is used for all languages.
*NickName: "KODAK EASYSHARE 5000 Series AiO"
*PSVersion: "(2017.000) 705"
*LanguageLevel: "3"
*ColorDevice: True
*DefaultColorSpace: RGB
*TTRasterizer: None

*% DefaultBitsPerPixel: 8

*% CUPS extentions to PPD keywords (CUPS Interface Design Description V1.1, idd.pdf)
*cupsFilter: "application/vnd.cups-raster 100 /Library/Printers/Kodak/5000_Series_A
iO/AiODriver.bundle/Contents/MacOS/driver"
*cupsFlipDuplex: True
*% Note: cupsManualCopies is not supported prior to Tiger (David Gelphman, Printing Li
st post, 3 Sep 2004);
*% Note: For Tiger, if cupsManualCopies is False, only one image for each page is sent
for noncollated jobs.
*cupsManualCopies: True
*cupsModelNumber: 5000
*cupsVersion: 1.1

*% Apple PPD keywords (OS X 10.3: see QA1352)
*APDialogExtension: "/Library/Printers/Kodak/5000_Series_AiO/PrinterOptions.plugin"
*APPrinterIconPath: "/Library/Printers/Kodak/5000_Series_AiO/AiODriver.bundle/Conte
nts/Resources/Printer.icns"
*APPrinterUtilityPath: "/Library/Printers/Kodak/5000_Series_AiO/KODAK AiO Home Center"

*% Format is: *cupsICCProfile ColorModel.MediaType.Resolution/Mode: <profile location>
*% where a missing item is a "wildcard" (per Printing List message from Paul D on 7 Oc
t 2003)
*cupsICCProfile RGB../RGB Profile: "/Library/Printers/Kodak/5000_Series_AiO/AiODriver.
bundle/Contents/Resources/RGB.icc"

*% Apple PPD keywords (OS X 10.4: see TN2144)
*% *APPrinterLowInkTool <not implemented: see WWDC 2005 session 212>

*% CUPS PPD keywords such as cupsColorSpace, cupsColorOrder, and cupsBitsPerColor
*% must be set via setpagedevice, as is done below. (See QA1368 for allowed combinatio
ns)

*% Set the color space to 8-bit RGB, but don't display any UI (other color spaces are
commented out)
*OpenUI *ColorModel/Color Space: PickOne
*OrderDependency: 10 AnySetup *ColorModel
*DefaultColorModel: RGB
*% ColorModel W/Luminance Color: "<</cupsBitsPerColor 8/cupsColorOrder 0/cupsColorSpac
e 0/cupsCompression 0>>setpagedevice"
*ColorModel RGB/RGB Color: "<</cupsBitsPerColor 8/cupsColorOrder 0/cupsColorSpace
1/cupsCompression 0>>setpagedevice"
*% % ColorModel K/Grayscale: "<</cupsBitsPerColor 8/cupsColorOrder 0/cupsColorSp
ace 3/cupsCompression 2>>setpagedevice"
*% ColorModel CMYK/CMYK Color: "<</cupsBitsPerColor 8/cupsColorOrder 0/cupsColorSpac
e 6/cupsCompression 0>>setpagedevice"
*% ColorModel KCMY/KCMY Color: "<</cupsBitsPerColor 8/cupsColorOrder 0/cupsColorSpac
e 8/cupsCompression 0>>setpagedevice"
*CloseUI: *ColorModel

*OpenUI *Duplex/Duplex: PickOne
*DefaultDuplex: None
*Duplex None/1-Sided: "<</Duplex false>> setpagedevice"
*Duplex DuplexNoTumble/2-Sided, Long-Edge Binding (No Tumble): "<</Duplex true/Tumble
false>> setpagedevice"
*Duplex DuplexTumble/2-Sided, Short-Edge Binding (Tumble): "<</Duplex true/Tumble true
>> setpagedevice"
*CloseUI: *Duplex

*OpenUI *Resolution/Resolution: PickOne
*OrderDependency: 20 AnySetup *Resolution
*DefaultResolution: 600dpi
*Resolution 300dpi/Draft: "<</HWResolution[300 300]>>setpaged
evice"
*Resolution 600dpi/Normal: "<</HWResolution[600 600]>>setpaged
evice"
*Resolution 1200dpi/Best: "<</HWResolution[1200 1200]>>setpag
edevice"
*CloseUI: *Resolution


*Font Courier: Standard "(004.000)" Standard Disk

*DefaultOutputOrder: Reverse

*% LandscapeOrientation: Plus90


*% Paper Handling ===================
*% OpenUI *PageSize: PickOne
*% OrderDependency: 10 AnySetup *PageSize
*DefaultPageSize: na-letter
*PageSize na-letter/US Letter: "1 dict dup/PageSize[612.00 792.00]put setpagedevice"
*PageSize na-letter-borderless/Borderless US Letter: "1 dict dup/PageSize[612.00 792.0
0]put setpagedevice"
*PageSize na-legal/US Legal: "1 dict dup/PageSize[612.00 1008.00]put setpagedevice"
*PageSize ek-aio-executive/Executive: "1 dict dup/PageSize[522.00 756.00]put setpagede
vice"
*PageSize iso-a4/A4: "1 dict dup/PageSize[595.28 841.89]put setpagedevice"
*PageSize iso-a4-borderless/Borderless A4: "1 dict dup/PageSize[595.28 841.89]put setp
agedevice"
*PageSize iso-a5/A5: "1 dict dup/PageSize[419.53 595.28]put setpagedevice"
*PageSize iso-a6/A6: "1 dict dup/PageSize[297.64 419.53]put setpagedevice"
*PageSize iso-b5/B5: "1 dict dup/PageSize[498.90 708.66]put setpagedevice"
*PageSize ek-aio-7_75-envelope/#7 3/4 Envelope: "1 dict dup/PageSize[279.00 540.00]put
setpagedevice"
*PageSize ek-aio-9-envelope/#9 Envelope: "1 dict dup/PageSize[279.00 632.52]put setpag
edevice"
*PageSize ek-aio-10-envelope/#10 Envelope: "1 dict dup/PageSize[297.00 684.00]put setp
agedevice"
*PageSize ek-aio-a2-envelope/A2 Envelope: "1 dict dup/PageSize[314.65 413.86]put setpa
gedevice"
*PageSize iso-c5-envelope/C5 Envelope: "1 dict dup/PageSize[459.21 649.13]put setpaged
evice"
*PageSize iso-c6-envelope/C6 Envelope: "1 dict dup/PageSize[323.15 459.21]put setpaged
evice"
*PageSize ek-aio-dl-envelope/DL Envelope: "1 dict dup/PageSize[311.81 623.62]put setpa
gedevice"
*PageSize ek-aio-3x5-index/3x5 in: "1 dict dup/PageSize[216.00 360.00]put setpagedevic
e"
*PageSize ek-aio-hagaki/Hagaki: "1 dict dup/PageSize[283.46 419.53]put setpagedevice"
*PageSize ek-aio-3_5x5/3.5x5 in: "1 dict dup/PageSize[252.00 360.00]put setpagedevice"
*PageSize ek-aio-3_5x5-borderless/Borderless 3.5x5 in: "1 dict dup/PageSize[252.00 360
.00]put setpagedevice"
*PageSize ek-aio-4x6/4x6 in: "1 dict dup/PageSize[288.00 432.00]put setpagedevice"
*PageSize ek-aio-4x6-borderless/Borderless 4x6 in: "1 dict dup/PageSize[288.00 432.00]
put setpagedevice"
*PageSize ek-aio-4x12/4x12 in: "1 dict dup/PageSize[288.00 864.00]put setpagedevice"
*PageSize ek-aio-4x12-borderless/Borderless 4x12 in: "1 dict dup/PageSize[288.00 864.0
0]put setpagedevice"
*PageSize ek-aio-5x7/5x7 in: "1 dict dup/PageSize[360.00 504.00]put setpagedevice"
*PageSize ek-aio-5x7-borderless/Borderless 5x7 in: "1 dict dup/PageSize[360.00 504.00]
put setpagedevice"
*PageSize ek-aio-8x10/8x10 in: "1 dict dup/PageSize[576.00 720.00]put setpagedevice"
*PageSize ek-aio-8x10-borderless/Borderless 8x10 in: "1 dict dup/PageSize[576.00 720.0
0]put setpagedevice"
*% CloseUI: *PageSize

*% OpenUI *PageRegion: PickOne
*OrderDependency: 10 AnySetup *PageRegion
*DefaultPageRegion: na-letter
*PageRegion na-letter/US Letter: "1 dict dup/PageSize[612.00 792.00]put setpagedevice"
*PageRegion na-letter-borderless/Borderless US Letter: "1 dict dup/PageSize[612.00 792
.00]put setpagedevice"
*PageRegion na-legal/US Legal: "1 dict dup/PageSize[612.00 1008.00]put setpagedevice"
*PageRegion ek-aio-executive/Executive: "1 dict dup/PageSize[522.00 756.00]put setpage
device"
*PageRegion iso-a4/A4: "1 dict dup/PageSize[595.28 841.89]put setpagedevice"
*PageRegion iso-a4-borderless/Borderless A4: "1 dict dup/PageSize[595.28 841.89]put se
tpagedevice"
*PageRegion iso-a5/A5: "1 dict dup/PageSize[419.53 595.28]put setpagedevice"
*PageRegion iso-a6/A6: "1 dict dup/PageSize[297.64 419.53]put setpagedevice"
*PageRegion iso-b5/B5: "1 dict dup/PageSize[498.90 708.66]put setpagedevice"
*PageRegion ek-aio-7_75-envelope/#7 3/4 Envelope: "1 dict dup/PageSize[279.00 540.00]p
ut setpagedevice"
*PageRegion ek-aio-9-envelope/#9 Envelope: "1 dict dup/PageSize[279.00 632.52]put setp
agedevice"
*PageRegion ek-aio-10-envelope/#10 Envelope: "1 dict dup/PageSize[297.00 684.00]put se
tpagedevice"
*PageRegion ek-aio-a2-envelope/A2 Envelope: "1 dict dup/PageSize[314.65 413.86]put set
pagedevice"
*PageRegion iso-c5-envelope/C5 Envelope: "1 dict dup/PageSize[459.21 649.13]put setpag
edevice"
*PageRegion iso-c6-envelope/C6 Envelope: "1 dict dup/PageSize[323.15 459.21]put setpag
edevice"
*PageRegion ek-aio-dl-envelope/DL Envelope: "1 dict dup/PageSize[311.81 623.62]put set
pagedevice"
*PageRegion ek-aio-3x5-index/3x5 in: "1 dict dup/PageSize[216.00 360.00]put setpagedev
ice"
*PageRegion ek-aio-hagaki/Hagaki: "1 dict dup/PageSize[283.46 419.53]put setpagedevice
"
*PageRegion ek-aio-3_5x5/3.5x5 in: "1 dict dup/PageSize[252.00 360.00]put setpagedevic
e"
*PageRegion ek-aio-3_5x5-borderless/Borderless 3.5x5 in: "1 dict dup/PageSize[252.00 3
60.00]put setpagedevice"
*PageRegion ek-aio-4x6/4x6 in: "1 dict dup/PageSize[288.00 432.00]put setpagedevice"
*PageRegion ek-aio-4x6-borderless/Borderless 4x6 in: "1 dict dup/PageSize[288.00 432.0
0]put setpagedevice"
*PageRegion ek-aio-4x12/4x12 in: "1 dict dup/PageSize[288.00 864.00]put setpagedevice"
*PageRegion ek-aio-4x12-borderless/Borderless 4x12 in: "1 dict dup/PageSize[288.00 864
.00]put setpagedevice"
*PageRegion ek-aio-5x7/5x7 in: "1 dict dup/PageSize[360.00 504.00]put setpagedevice"
*PageRegion ek-aio-5x7-borderless/Borderless 5x7 in: "1 dict dup/PageSize[360.00 504.0
0]put setpagedevice"
*PageRegion ek-aio-8x10/8x10 in: "1 dict dup/PageSize[576.00 720.00]put setpagedevice"
*PageRegion ek-aio-8x10-borderless/Borderless 8x10 in: "1 dict dup/PageSize[576.00 720
.00]put setpagedevice"
*% CloseUI: *PageRegion

*DefaultImageableArea: na-letter
*ImageableArea na-letter/US Letter: "14.17 14.17 597.83 777.83"
*ImageableArea na-letter-borderless/Borderless US Letter: "0.00 0.00 612.00 792.00"
*ImageableArea na-legal/US Legal: "14.17 14.17 597.83 993.83"
*ImageableArea ek-aio-executive/Executive: "14.17 14.17 507.83 741.83"
*ImageableArea iso-a4/A4: "14.17 14.17 581.10 827.72"
*ImageableArea iso-a4-borderless/Borderless A4: "0.00 0.00 595.28 841.89"
*ImageableArea iso-a5/A5: "14.17 14.17 405.35 581.10"
*ImageableArea iso-a6/A6: "14.17 14.17 283.46 405.35"
*ImageableArea iso-b5/B5: "14.17 14.17 484.72 694.49"
*ImageableArea ek-aio-7_75-envelope/#7 3/4 Envelope: "14.17 14.17 264.83 525.83"
*ImageableArea ek-aio-9-envelope/#9 Envelope: "14.17 14.17 264.83 618.35"
*ImageableArea ek-aio-10-envelope/#10 Envelope: "14.17 14.17 282.83 669.83"
*ImageableArea ek-aio-a2-envelope/A2 Envelope: "14.17 14.17 300.47 399.69"
*ImageableArea iso-c5-envelope/C5 Envelope: "14.17 14.17 445.04 634.96"
*ImageableArea iso-c6-envelope/C6 Envelope: "14.17 14.17 308.98 445.04"
*ImageableArea ek-aio-dl-envelope/DL Envelope: "14.17 14.17 297.64 609.45"
*ImageableArea ek-aio-3x5-index/3x5 in: "14.17 14.17 201.83 345.83"
*ImageableArea ek-aio-hagaki/Hagaki: "14.17 14.17 269.29 405.35"
*ImageableArea ek-aio-3_5x5/3.5x5 in: "14.17 14.17 237.83 345.83"
*ImageableArea ek-aio-3_5x5-borderless/Borderless 3.5x5 in: "0.00 0.00 252.00 360.00"
*ImageableArea ek-aio-4x6/4x6 in: "14.17 14.17 273.83 417.83"
*ImageableArea ek-aio-4x6-borderless/Borderless 4x6 in: "0.00 0.00 288.00 432.00"
*ImageableArea ek-aio-4x12/4x12 in: "14.17 14.17 273.83 849.83"
*ImageableArea ek-aio-4x12-borderless/Borderless 4x12 in: "0.00 0.00 288.00 864.00"
*ImageableArea ek-aio-5x7/5x7 in: "14.17 14.17 345.83 489.83"
*ImageableArea ek-aio-5x7-borderless/Borderless 5x7 in: "0.00 0.00 360.00 504.00"
*ImageableArea ek-aio-8x10/8x10 in: "14.17 14.17 561.83 705.83"
*ImageableArea ek-aio-8x10-borderless/Borderless 8x10 in: "0.00 0.00 576.00 720.00"

*DefaultPaperDimension: na-letter
*PaperDimension na-letter/US Letter: "612.00 792.00"
*PaperDimension na-letter-borderless/Borderless US Letter: "612.00 792.00"
*PaperDimension na-legal/US Legal: "612.00 1008.00"
*PaperDimension ek-aio-executive/Executive: "522.00 756.00"
*PaperDimension iso-a4/A4: "595.28 841.89"
*PaperDimension iso-a4-borderless/Borderless A4: "595.28 841.89"
*PaperDimension iso-a5/A5: "419.53 595.28"
*PaperDimension iso-a6/A6: "297.64 419.53"
*PaperDimension iso-b5/B5: "498.90 708.66"
*PaperDimension ek-aio-7_75-envelope/#7 3/4 Envelope: "279.00 540.00"
*PaperDimension ek-aio-9-envelope/#9 Envelope: "279.00 632.52"
*PaperDimension ek-aio-10-envelope/#10 Envelope: "297.00 684.00"
*PaperDimension ek-aio-a2-envelope/A2 Envelope: "314.65 413.86"
*PaperDimension iso-c5-envelope/C5 Envelope: "459.21 649.13"
*PaperDimension iso-c6-envelope/C6 Envelope: "323.15 459.21"
*PaperDimension ek-aio-dl-envelope/DL Envelope: "311.81 623.62"
*PaperDimension ek-aio-3x5-index/3x5 in: "216.00 360.00"
*PaperDimension ek-aio-hagaki/Hagaki: "283.46 419.53"
*PaperDimension ek-aio-3_5x5/3.5x5 in: "252.00 360.00"
*PaperDimension ek-aio-3_5x5-borderless/Borderless 3.5x5 in: "252.00 360.00"
*PaperDimension ek-aio-4x6/4x6 in: "288.00 432.00"
*PaperDimension ek-aio-4x6-borderless/Borderless 4x6 in: "288.00 432.00"
*PaperDimension ek-aio-4x12/4x12 in: "288.00 864.00"
*PaperDimension ek-aio-4x12-borderless/Borderless 4x12 in: "288.00 864.00"
*PaperDimension ek-aio-5x7/5x7 in: "360.00 504.00"
*PaperDimension ek-aio-5x7-borderless/Borderless 5x7 in: "360.00 504.00"
*PaperDimension ek-aio-8x10/8x10 in: "576.00 720.00"
*PaperDimension ek-aio-8x10-borderless/Borderless 8x10 in: "576.00 720.00"

*CustomPageSize True: "
pop 4 dict begin 2 array astore/PageOffset exch def
2 array astore/PageSize exch def/ImagingBBox null def currentdict end setpagedevice"
*End
*ParamCustomPageSize Width: 1 points 252.00 612.00
*ParamCustomPageSize Height: 2 points 360.00 1008.00
*ParamCustomPageSize WidthOffset: 3 points 0 0
*ParamCustomPageSize HeightOffset: 4 points 0 0
*ParamCustomPageSize Orientation: 5 int 0 0
*MaxMediaWidth: "612.00"
*MaxMediaHeight: "1008.00"
*CenterRegistered: False
*HWMargins: 0.00 0.00 0.00 0.00


*%End of EASYSHARE 5X00 AiO Printer.ppd

---

### Post by LexiRedLion on 2010-09-11
Says right in the text that it's a PPD (PostScript Printer Definition) file.  I suspect you can save it as "Kodak5X00.PPD" Go to CUPS (localhost:631), Admin tab, Add Printer, select the connection type, then use that file name in the "Or Provide a PPD File" text box.

I just tried using it, but got an error.  An apostrophe or comma or somesuch is missing. <shrug>

---

