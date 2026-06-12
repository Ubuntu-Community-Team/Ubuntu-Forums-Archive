---
title: "[SOLVED] Please help me tweaking IP1500 printer ppd file"
date: 2008-05-22
forum: Hardware
---

### Post by salvador_luna on 2008-05-22
Good night to everyone.

Someone can help me tweaking the ppd file of a Canon Pixma iP1500 printer?

The printer is working fine in hardy (used [this thread]("http://ubuntuforums.org/showthread.php?t=487890&highlight=ip1500")), but it uses a lot of ink. I researched a little and found [this]("https://wiki.ubuntu.com/CanonPixmaIP1500").

I skipped the part about installing the driver and followed the step #7 and 8, modifying the instructions to something like this:

> cd /etc/cups/ppd 
sudo cp iP1500.ppd iP1500.ppd.backup
gksudo gedit iP1500.ppd

add the following lines:

*OpenUI *CNQuality/Quality: PickOne 
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality 

and replace

*OpenUI *Resolution/Output Resolution: PickOne 
*DefaultResolution: 600
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*CloseUI: *Resolution

by the following:

*OpenUI *Resolution/Output Resolution: PickOne 
*DefaultResolution: 600
*Resolution 150/150 dpi: "<</HWResolution[150 150]>>setpagedevice"
*Resolution 300/300 dpi: "<</HWResolution[300 300]>>setpagedevice"
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*CloseUI: *Resolution

I just changed the path and filename of the original howto and added the 150 dpi settings, so i can choose the economy option and a 150 resolution: it printed really fast but it still used a lot of ink.

So, the questions are:

How do i change my configuration to make printings more "grey"? (of course, using less ink)

and

How do i enable the option to print in grey scale?

This is the content of the ppd file:

> *PPD-Adobe: "4.3"
*%  CUPS add-on PPD file for Canon Bubble Jet Printer.
*%  Copyright CANON INC. 2001-2005
*%  All Rights Reserved.
*%
*%  This program is free software; you can redistribute it and/or modify
*%  it under the terms of the GNU General Public License as published by
*%  the Free Software Foundation; either version 2 of the License, or
*%  (at your option) any later version.
*%
*%  This program is distributed in the hope that it will be useful,
*%  but WITHOUT ANY WARRANTY; without even the implied warranty of
*%  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
*%  GNU General Public License for more details.
*%
*%  You should have received a copy of the GNU General Public License
*%  along with this program; if not, write to the Free Software
*%  Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA

*FileVersion: "1.0"
*FormatVersion:	"4.3"
*LanguageEncoding: ISOLatin1
*LanguageVersion: English
*Manufacturer: "Canon"
*ModelName: "Canon PIXMA iP1500"
*NickName: "Canon PIXMA iP1500 Ver.2.50"
*PCFileName: "CNPM1500.PPD"
*Product: "(pixmaip1500)"
*PSVersion: "(3010.000) 550"
*PSVersion: "(3010.000) 651"
*PSVersion: "(3010.000) 705"
*ShortNickName: "PIXMAiP1500"

*ColorDevice: True
*DefaultColorSpace: RGB
*Throughput: "1"
*LandscapeOrientation: Plus90

*cupsFilter: "application/vnd.cups-postscript 0 pstocanonbj"
*cupsManualCopies: True
*cupsModelNumber: 180
*cupsVersion: 1.1

*MaxMediaWidth: "612"
*MaxMediaHeight: "1656"
*CenterRegistered: False
*HWMargins: 9.64 14.17 9.64 8.50
*LeadingEdge Short: ""
*DefaultLeadingEdge: Short
*VariablePaperSize: True
*ParamCustomPageSize Width: 1 points 255.12 612.0
*ParamCustomPageSize Height: 2 points 340.16 1656.0
*ParamCustomPageSize WidthOffset: 3 points 0 0
*ParamCustomPageSize HeightOffset: 4 points 0 0
*ParamCustomPageSize Orientation: 5 int 1 1
*CustomPageSize True: "pop pop pop <</PageSize [5 -2 roll] /ImagingBBox null>>setpagedevice"

*OpenUI *CNQuality/Quality: PickOne 
*DefaultCNQuality: 5
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality

*OpenUI *PageSize/Paper Size: PickOne
*DefaultPageSize: letter
*PageSize a5/A5: "<</CNPageSizeName(a5)/PageSize[420 595]/ImagingBBox null>>setpagedevice"
*PageSize a4/A4: "<</CNPageSizeName(a4)/PageSize[595 842]/ImagingBBox null>>setpagedevice"
*PageSize b5/B5: "<</CNPageSizeName(b5)/PageSize[516 729]/ImagingBBox null>>setpagedevice"
*PageSize letter/Letter: "<</CNPageSizeName(letter)/PageSize[612 792]/ImagingBBox null>>setpagedevice"
*PageSize legal/Legal: "<</CNPageSizeName(legal)/PageSize[612 1008]/ImagingBBox null>>setpagedevice"
*PageSize envelope10p/Comm. Env. #10: "<</CNPageSizeName(envelope10p)/PageSize[297 684]/ImagingBBox null>>setpagedevice"
*PageSize envelopedlp/DL Env.: "<</CNPageSizeName(envelopedlp)/PageSize[312 624]/ImagingBBox null>>setpagedevice"
*PageSize 4X6/4x6in 101.6x152.4mm: "<</CNPageSizeName(4X6)/PageSize[288 432]/ImagingBBox null>>setpagedevice"
*PageSize 5X7/5x7in 127.0x177.8mm: "<</CNPageSizeName(5X7)/PageSize[360 504]/ImagingBBox null>>setpagedevice"
*CloseUI: *PageSize

*OpenUI *PageRegion: PickOne
*DefaultPageRegion: letter
*PageRegion a5/A5: "<</CNPageSizeName(a5)/PageSize[420 595]/ImagingBBox null>>setpagedevice"
*PageRegion a4/A4: "<</CNPageSizeName(a4)/PageSize[595 842]/ImagingBBox null>>setpagedevice"
*PageRegion b5/B5: "<</CNPageSizeName(b5)/PageSize[516 729]/ImagingBBox null>>setpagedevice"
*PageRegion letter/Letter: "<</CNPageSizeName(letter)/PageSize[612 792]/ImagingBBox null>>setpagedevice"
*PageRegion legal/Legal: "<</CNPageSizeName(legal)/PageSize[612 1008]/ImagingBBox null>>setpagedevice"
*PageRegion envelope10p/Comm. Env. #10: "<</CNPageSizeName(envelope10p)/PageSize[297 684]/ImageingBBox null>>setpagedevice"
*PageRegion envelopedlp/DL Env.: "<</CNPageSizeName(envelopedlp)/PageSize[312 624]/ImageingBBox null>>setpagedevice"
*PageRegion 4X6/4x6in 101.6x152.4mm: "<</CNPageSizeName(4X6)/PageSize[288 432]/ImagingBBox null>>setpagedevice"
*PageRegion 5X7/5x7in 127.0x177.8mm: "<</CNPageSizeName(5X7)/PageSize[360 504]/ImagingBBox null>>setpagedevice"
*CloseUI: *PageRegion

*OpenUI *MediaType/Media Type: PickOne
*DefaultMediaType: plain
*MediaType plain/Plain Paper: "<</MediaType(plain)>>setpagedevice"
*MediaType prophoto/Photo Paper Pro: "<</MediaType(prophoto)>>setpagedevice"
*MediaType superphoto/Photo Paper Plus Glossy: "<</MediaType(superphoto)>>setpagedevice"
*MediaType doublesidephoto/Photo Paper Plus Double Sided: "<</MediaType(doublesidephoto)>>setpagedevice"
*MediaType matte/Matte Photo Paper: "<</MediaType(matte)>>setpagedevice"
*MediaType glossypaper/Glossy Photo Paper: "<</MediaType(glossypaper)>>setpagedevice"
*MediaType highres/High Resolution Paper: "<</MediaType(highres)>>setpagedevice"
*MediaType tshirt/T-Shirt Transfer: "<</MediaType(tshirt)>>setpagedevice"
*MediaType ohp/Transparency: "<</MediaType(ohp)>>setpagedevice"
*MediaType envelope/Envelope: "<</MediaType(envelope)>>setpagedevice"
*MediaType otherphoto/Other Photo Paper: "<</MediaType(otherphoto)>>setpagedevice"
*CloseUI: *MediaType

*OpenUI *InputSlot/Paper Feed: PickOne
*DefaultInputSlot: asf
*InputSlot asf/Auto Feeder: "<</cupsMediaPosition 1>>setpagedevice"
*CloseUI: *InputSlot

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 150
*Resolution 150/150 dpi: "<</HWResolution[150 150]>>setpagedevice"
*Resolution 300/300 dpi: "<</HWResolution[300 300]>>setpagedevice"
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*CloseUI: *Resolution

*OpenUI *ColorModel/Color Model: PickOne
*DefaultColorModel: rgb
*ColorModel rgb/RGB: "<</cupsColorOrder 0/cupsColorSpace 1/cupsCompression 0/cupsBitsPerColor 8>>setpagedevice"
*CloseUI: *ColorModel

*DefaultImageableArea: letter
*ImageableArea a5: "9.64 14.17 409.89 586.77"
*ImageableArea a4: "9.64 14.17 585.64 833.39"
*ImageableArea b5: "9.64 14.17 506.27 720.00"
*ImageableArea letter: "18.14 14.17 594.14 783.50"
*ImageableArea legal: "18.14 14.17 594.14 999.50"
*ImageableArea envelope10p: "9.64 75.12 287.35 611.32"
*ImageableArea envelopedlp: "9.64 75.12 302.17 600.94"
*ImageableArea 4X6: "9.64 14.17 278.36 423,50"
*ImageableArea 5X7: "9.64 14.17 350.36 495.50"

*DefaultPaperDimension: letter
*PaperDimension a5: "420 595"
*PaperDimension a4: "595 842"
*PaperDimension b5: "516 729"
*PaperDimension letter: "612 792"
*PaperDimension legal: "612 1008"
*PaperDimension envelope10p: "297 684"
*PaperDimension envelopedlp: "312 624"
*PaperDimension 4X6: "288 432"
*PaperDimension 5X7: "360 504"

*%CNPpdToOptKey PageSize       --papersize
*%CNPpdToOptKey MediaType      --media
*%CNPpdToOptKey InputSlot      --paperload
*%CNPpdToOptKey CNCartridge    --cartridge
*%CNPpdToOptKey CNQuality      --quality
*%CNPpdToOptKey CNHalftoning   --halftoning
*%CNPpdToOptKey CNRenderIntent --renderintent
*%CNPpdToOptKey CNGamma        --gamma
*%CNPpdToOptKey CNBalanceC     --balance_c
*%CNPpdToOptKey CNBalanceM     --balance_m
*%CNPpdToOptKey CNBalanceY     --balance_y
*%CNPpdToOptKey CNBalanceK     --balance_k
*%CNPpdToOptKey CNDensity      --density
*%CNPpdToOptKey CNGrayscale    --grayscale
*%CNPpdToOptKey CNLocation     --location
*%CNPpdToOptKey CNPercent      --percent
*%CNPpdToOptKey CNCopies       --copies
*%CNPpdToOptKey CNPaperGap     --papergap

If any body can help I will be very grateful.

I've attached a copy of the file.

(sorry about my english!)

---

### Post by silvanus2005 on 2008-05-25
[http://software.canon-europe.com/software/0022415.asp?model=](http://software.canon-europe.com/software/0022415.asp?model=)
Try to install the drivers provided by Canon, and convert them to .deb using alien application. let me know if it`s working.:)

---

### Post by salvador_luna on 2008-05-26
Hey thanks for the reply!

Well i did what you say:

1) Downloaded the file.

2) Uncompressed the file and ran:
> sudo alien --scripts *.rpm
    Everything ok.

3) Then:
> sudo dpkg -i *.deb

4) After all was installed, i plugged in my printer an cups detected it, but it says something like this: Printer <<iP1500>>: <<cups-missing-filter>>.

5) Tried to print and no go. I checked the options in cups and it gives me the same before i edited the ppd file.


Something interesting: I downloaded the manual and there i found some options about printing in "greyscale" and "halftoning" (maybe this is what i'm looking for, but i'm not sure) in the CLI... can i add this things to the gui in cups?

Any idea?

Thanks in advance.

---

### Post by silvanus2005 on 2008-05-26
I don`t know, my expertise is limited in this domain. Have you tried to wrote to Canon, maybe they will offer an answer for your problem?
I had problems printing in Ubuntu with a Canon LBP 3000; I swithced to Kubuntu 8.04 (KDE 3.5.9) and my printer it`s working.You may try Kubuntu, maybe it will solve your problem.

---

### Post by salvador_luna on 2008-05-26
Thanks!

Saddly Canon does not support linux in any way so i can get help from them, so I will try Kubuntu then :)

Do i have to install the driver like you described?

Do you have any guides to help me do the swithing to kubuntu? I have a creative zen micro so i don know if it will work ok with amarok.

I will let open this this thread so maybe someone can help us with this file :)

Again, thank you :)

---

### Post by silvanus2005 on 2008-06-02
Go to kubuntu.org, you will find there everything you need.

---

