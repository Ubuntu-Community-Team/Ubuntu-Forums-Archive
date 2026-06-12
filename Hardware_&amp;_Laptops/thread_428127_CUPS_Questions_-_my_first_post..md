---
title: "CUPS Questions - my first post."
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by waelaltaqi on 2007-04-30
Hi, 
I'm originally a Fedora user and i recently switched to Debian/Ubuntu due to the fact that YUM and RPM have pissed me off couple of times. Everything is working fine so far except for this nasty problem. i'm trying to add my Lexmark printer from shell:

```
  lpadmin -p lexmark -E -v usb:/dev/usblp0 -m /usr/share/cups/lexmark.ppd 
lpadmin: Unable to copy PPD file!

```

when i take a look at /var/log/cups/erro_log i get this: 
```
E [30/Apr/2007:00:08:20 -0500] copy_model: empty PPD file! 
E [30/Apr/2007:00:08:20 -0500] PID 14273 (/usr/lib/cups/daemon/cups-driverd) st

```

the file is not empty .. here it is:
```
*PPD-Adobe: "4.3"
*FormatVersion:	"4.3"
*FileVersion:	"1.0"
*LanguageVersion: English 
*LanguageEncoding: ISOLatin1
*PCFileName:	"LXZ600CJ.PPD"
*Manufacturer:	"Lexmark"
*Product:	"(CUPS v1.1)"
*cupsVersion:	1.1
*cupsManualCopies: True
*cupsModelNumber:  1
*cupsFilter:	"application/vnd.cups-raster 0 rastertoz600"
*ModelName:     "Lexmark Z600 Color Jetprinter"
*ShortNickName: "Lexmark Z600"
*NickName:      "Lexmark Z600 v1.0-1"
*PSVersion:	"(3010.000) 550"
*PSVersion:	"(3010.000) 651"
*PSVersion:	"(3010.000) 652"
*LanguageLevel:	"3"
*ColorDevice:	True
*DefaultColorSpace:	RGB
*FileSystem:	False
*Throughput:	"15"
*LandscapeOrientation: Plus90
*VariablePaperSize: False
*TTRasterizer:	Type42

 

*OpenUI *PageSize/Media Size: PickOne
*OrderDependency: 20 AnySetup *PageSize 
*DefaultPageSize: Letter
*PageSize Letter/Letter: "<</PageSize[612 792]/ImagingBBox null>>setpagedevice"
*PageSize A4/A4: "<</PageSize[595 842]/ImagingBBox null>>setpagedevice"
*PageSize Statement/Statement: "<</PageSize[396 612]/ImagingBBox null>>setpagedevice"
*PageSize Legal/Legal: "<</PageSize[612 1008]/ImagingBBox null>>setpagedevice"
*PageSize B5/B5: "<</PageSize[516 729]/ImagingBBox null>>setpagedevice"
*PageSize Executive/Executive: "<</PageSize[522 756]/ImagingBBox null>>setpagedevice"
*PageSize A5/A5: "<</PageSize[420 595]/ImagingBBox null>>setpagedevice"
*PageSize A6Cardstock/A6 Cardstock: "<</PageSize[298 420]/ImagingBBox null>>setpagedevice"
*PageSize IndexCard3X5/Index Card 3x5: "<</PageSize[216 360]/ImagingBBox null>>setpagedevice"
*PageSize Postcard4X6/Postcard 4x6: "<</PageSize[288 432]/ImagingBBox null>>setpagedevice"
*PageSize Hagaki/Hagaki: "<</PageSize[283 420]/ImagingBBox null>>setpagedevice"
*PageSize Envelope634/Envelope 6 3/4: "<</PageSize[261 468]/ImagingBBox null>>setpagedevice"
*PageSize Envelope9/Envelope #9: "<</PageSize[279 639]/ImagingBBox null>>setpagedevice"
*PageSize Envelope10/Envelope #10: "<</PageSize[297 684]/ImagingBBox null>>setpagedevice"
*PageSize EnvelopeDL/Envelope DL: "<</PageSize[312 624]/ImagingBBox null>>setpagedevice"
*PageSize EnvelopeC5/Envelope C5: "<</PageSize[459 649]/ImagingBBox null>>setpagedevice"
*PageSize EnvelopeC6/Envelope C6: "<</PageSize[323 459]/ImagingBBox null>>setpagedevice"
*PageSize EnvelopeB5/Envelope B5: "<</PageSize[499 708]/ImagingBBox null>>setpagedevice"
*PageSize Envelope734/Envelope 7 3/4: "<</PageSize[279 540]/ImagingBBox null>>setpagedevice"
*PageSize A2Baronial/A2 Baronial: "<</PageSize[315 414]/ImagingBBox null>>setpagedevice"
*PageSize Chokei3/Chokei 3: "<</PageSize[340 666]/ImagingBBox null>>setpagedevice"
*PageSize Chokei4/Chokei 4: "<</PageSize[255 581]/ImagingBBox null>>setpagedevice"
*PageSize Chokei40/Chokei 40: "<</PageSize[255 638]/ImagingBBox null>>setpagedevice"
*PageSize Kakugata3/Kakugata 3: "<</PageSize[612 785]/ImagingBBox null>>setpagedevice"
*PageSize Kakugata4/Kakugata 4: "<</PageSize[558 757]/ImagingBBox null>>setpagedevice"
*PageSize Kakugata5/Kakugata 5: "<</PageSize[539 680]/ImagingBBox null>>setpagedevice"
*PageSize Kakugata6/Kakugata 6: "<</PageSize[459 649]/ImagingBBox null>>setpagedevice"
*PageSize L/L: "<</PageSize[252 360]/ImagingBBox null>>setpagedevice"
*PageSize 2L/2L: "<</PageSize[360 505]/ImagingBBox null>>setpagedevice"
*CloseUI: *PageSize

*OpenUI *PageRegion: PickOne
*OrderDependency: 10 AnySetup *PageRegion
*DefaultPageRegion: Letter
*PageRegion Letter/Letter: "<</PageSize[612 792]/ImagingBBox null>>setpagedevice"
*PageRegion A4/A4: "<</PageSize[595 842]/ImagingBBox null>>setpagedevice"
*PageRegion Statement/Statement: "<</PageSize[396 612]/ImagingBBox null>>setpagedevice"
*PageRegion Legal/Legal: "<</PageSize[612 1008]/ImagingBBox null>>setpagedevice"
*PageRegion B5/B5: "<</PageSize[516 729]/ImagingBBox null>>setpagedevice"
*PageRegion Executive/Executive: "<</PageSize[522 756]/ImagingBBox null>>setpagedevice"
*PageRegion A5/A5: "<</PageSize[420 595]/ImagingBBox null>>setpagedevice"
*PageRegion A6Cardstock/A6 Cardstock: "<</PageSize[298 420]/ImagingBBox null>>setpagedevice"
*PageRegion IndexCard3X5/Index Card 3x5: "<</PageSize[216 360]/ImagingBBox null>>setpagedevice"
*PageRegion Postcard4X6/Postcard 4x6: "<</PageSize[288 432]/ImagingBBox null>>setpagedevice"
*PageRegion Hagaki/Hagaki: "<</PageSize[283 420]/ImagingBBox null>>setpagedevice"
*PageRegion Envelope634/Envelope 6 3/4: "<</PageSize[261 468]/ImagingBBox null>>setpagedevice"
*PageRegion Envelope9/Envelope #9: "<</PageSize[279 639]/ImagingBBox null>>setpagedevice"
*PageRegion Envelope10/Envelope #10: "<</PageSize[297 684]/ImagingBBox null>>setpagedevice"
*PageRegion EnvelopeDL/Envelope DL: "<</PageSize[312 624]/ImagingBBox null>>setpagedevice"
*PageRegion EnvelopeC5/Envelope C5: "<</PageSize[459 649]/ImagingBBox null>>setpagedevice"
*PageRegion EnvelopeC6/Envelope C6: "<</PageSize[323 459]/ImagingBBox null>>setpagedevice"
*PageRegion EnvelopeB5/Envelope B5: "<</PageSize[499 708]/ImagingBBox null>>setpagedevice"
*PageRegion Envelope734/Envelope 7 3/4: "<</PageSize[279 540]/ImagingBBox null>>setpagedevice"
*PageRegion A2Baronial/A2 Baronial: "<</PageSize[315 414]/ImagingBBox null>>setpagedevice"
*PageRegion Chokei3/Chokei 3: "<</PageSize[340 666]/ImagingBBox null>>setpagedevice"
*PageRegion Chokei4/Chokei 4: "<</PageSize[255 581]/ImagingBBox null>>setpagedevice"
*PageRegion Chokei40/Chokei 40: "<</PageSize[255 638]/ImagingBBox null>>setpagedevice"
*PageRegion Kakugata3/Kakugata 3: "<</PageSize[612 785]/ImagingBBox null>>setpagedevice"
*PageRegion Kakugata4/Kakugata 4: "<</PageSize[558 757]/ImagingBBox null>>setpagedevice"
*PageRegion Kakugata5/Kakugata 5: "<</PageSize[539 680]/ImagingBBox null>>setpagedevice"
*PageRegion Kakugata6/Kakugata 6: "<</PageSize[459 649]/ImagingBBox null>>setpagedevice"
*PageRegion L/L: "<</PageSize[252 360]/ImagingBBox null>>setpagedevice"
*PageRegion 2L/2L: "<</PageSize[360 505]/ImagingBBox null>>setpagedevice"
*CloseUI: *PageRegion

*DefaultImageableArea: Letter
*ImageableArea Letter/Letter: "18 36 594 787"
*ImageableArea A4/A4: "18 36 585 837"
*ImageableArea Statement/Statement: "18 36 378 607"
*ImageableArea Legal/Legal: "18 36 594 1003"
*ImageableArea B5/B5: "18 36 506 724"
*ImageableArea Executive/Executive: "18 36 504 751"
*ImageableArea A5/A5: "18 36 410 590"
*ImageableArea A6Cardstock/A6 Cardstock: "18 36 280 415"
*ImageableArea IndexCard3X5/Index Card 3x5: "18 36 198 355"
*ImageableArea Postcard4X6/Postcard 4x6: "18 36 270 427"
*ImageableArea Hagaki/Hagaki: "18 36 265 415"
*ImageableArea Envelope634/Envelope 6 3/4: "18 36 256 463"
*ImageableArea Envelope9/Envelope #9: "18 36 274 634"
*ImageableArea Envelope10/Envelope #10: "18 36 292 679"
*ImageableArea EnvelopeDL/Envelope DL: "18 36 307 619"
*ImageableArea EnvelopeC5/Envelope C5: "18 36 454 644"
*ImageableArea EnvelopeC6/Envelope C6: "18 36 318 454"
*ImageableArea EnvelopeB5/Envelope B5: "18 36 494 703"
*ImageableArea Envelope734/Envelope 7 3/4: "18 36 274 535"
*ImageableArea A2Baronial/A2 Baronial: "18 36 310 409"
*ImageableArea Chokei3/Chokei 3: "18 36 335 661"
*ImageableArea Chokei4/Chokei 4: "18 36 250 576"
*ImageableArea Chokei40/Chokei 40: "18 36 250 678"
*ImageableArea Kakugata3/Kakugata 3: "18 36 607 780"
*ImageableArea Kakugata4/Kakugata 4: "18 36 553 752"
*ImageableArea Kakugata5/Kakugata 5: "18 36 534 675"
*ImageableArea Kakugata6/Kakugata 6: "18 36 454 644"
*ImageableArea L/L: "18 36 234 355"
*ImageableArea 2L/2L: "18 36 342 500"

*DefaultPaperDimension: Letter
*PaperDimension Letter/Letter: "612 792"
*PaperDimension A4/A4: "595 842"
*PaperDimension Statement/Statement: "396 612"
*PaperDimension Legal/Legal: "612 1008"
*PaperDimension B5/B5: "516 729"
*PaperDimension Executive/Executive: "522 756"
*PaperDimension A5/A5: "420 595"
*PaperDimension A6Cardstock/A6 Cardstock: "298 420"
*PaperDimension IndexCard3X5/Index Card 3x5: "216 360"
*PaperDimension Postcard4X6/Postcard 4x6: "288 432"
*PaperDimension Hagaki/Hagaki: "283 420"
*PaperDimension Envelope634/Envelope 6 3/4: "261 468"
*PaperDimension Envelope9/Envelope #9: "279 639"
*PaperDimension Envelope10/Envelope #10: "297 684"
*PaperDimension EnvelopeDL/Envelope DL: "312 624"
*PaperDimension EnvelopeC5/Envelope C5: "459 649"
*PaperDimension EnvelopeC6/Envelope C6: "323 459"
*PaperDimension EnvelopeB5/Envelope B5: "499 708"
*PaperDimension Envelope734/Envelope 7 3/4: "279 540"
*PaperDimension A2Baronial/A2 Baronial: "315 414"
*PaperDimension Chokei3/Chokei 3: "340 666"
*PaperDimension Chokei4/Chokei 4: "255 581"
*PaperDimension Chokei40/Chokei 40: "255 683"
*PaperDimension Kakugata3/Kakugata 3: "612 785"
*PaperDimension Kakugata4/Kakugata 4: "558 757"
*PaperDimension Kakugata5/Kakugata 5: "539 680"
*PaperDimension Kakugata6/Kakugata 6: "459 649"
*PaperDimension L/L: "252 360"
*PaperDimension 2L/2L: "360 505"

*MaxMediaWidth:		"618"
*MaxMediaHeight:	"936"
*HWMargins:		0 15 0 5
*CustomPageSize True:	"pop pop pop <</PageSize[5 -2 roll]/ImagingBBox null>>setpagedevice"
*ParamCustomPageSize	Width:		1 points 144 618
*ParamCustomPageSize	Height:		2 points 288 936
*ParamCustomPageSize	WidthOffset:	3 points 0 0
*ParamCustomPageSize	HeightOffset:	4 points 0 0
*ParamCustomPageSize 	Orientation:	5 int 0 0
	
*OpenUI *MediaType/Media Type: PickOne
*OrderDependency: 10 AnySetup *MediaType 
*DefaultMediaType: Plain
*MediaType Plain/Plain Paper: "<</cupsMediaType 0>>setpagedevice"
*MediaType Coated/Coated Paper: "<</cupsMediaType 1>>setpagedevice"
*MediaType Glossy/Glossy Paper: "<</cupsMediaType 2>>setpagedevice"
*MediaType Transparency/Transparency: "<</cupsMediaType 3>>setpagedevice"
*MediaType Greeting/Greeting Card: "<</cupsMediaType 4>>setpagedevice"
*MediaType IronOn/Iron-On Transfer: "<</cupsMediaType 5>>setpagedevice"
*%MediaType Automatic/Media Sense: "<</cupsMediaType 6>>setpagedevice"
*CloseUI: *MediaType

*OpenGroup: Others

*OpenUI *PrintQuality/Print Quality: PickOne
*OrderDependency: 20 AnySetup *PrintQuality 
*DefaultPrintQuality: Normal
*PrintQuality Draft/Draft  (300 dpi): "<</HWResolution[300 300]/cupsCompression 0>>setpagedevice"
*PrintQuality Normal/Normal (600 dpi): "<</HWResolution[600 600]/cupsCompression 1>>setpagedevice"
*PrintQuality Better/Better (1200 dpi): "<</HWResolution[600 600]/cupsCompression 2>>setpagedevice"
*PrintQuality Best/Best (2400 dpi): "<</HWResolution[600 600]/cupsCompression 3>>setpagedevice"
*CloseUI: *PrintQuality

*OpenUI *ColorModel/Output Mode: PickOne
*OrderDependency: 10 AnySetup *ColorModel 
*DefaultColorModel: Color
*ColorModel Color/Color: "<</cupsColorOrder 0/cupsColorSpace 1/cupsBitsPerColor 8/cupsRowCount 0>>setpagedevice"
*ColorModel Black/Grayscale: "<</cupsColorOrder 0/cupsColorSpace 1/cupsBitsPerColor 8/cupsRowCount 1>>setpagedevice"
*CloseUI: *ColorModel

*OpenUI *Inkset/Inkset: PickOne
*OrderDependency: 10 AnySetup *Inkset 
*DefaultInkset: CMYK
*Inkset CMY/CMY: "<</cupsRowStep 1>>setpagedevice"
*Inkset K/K: "<</cupsRowStep 2>>setpagedevice"
*Inkset CMYK/CMYK: "<</cupsRowStep 3>>setpagedevice"
*CloseUI: *Inkset

*CloseGroup: Others

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

can anybody explain for me what's the problem?

thanks.

---

### Post by tgalati4 on 2007-04-30
sudo lpadmin -p lexmark -E -v usb:/dev/usblp0 -m /usr/share/cups/lexmark.ppd

Welcome to the forums.

---

