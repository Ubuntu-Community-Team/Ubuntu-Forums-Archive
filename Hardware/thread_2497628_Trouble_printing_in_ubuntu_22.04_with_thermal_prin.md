---
title: "Trouble printing in ubuntu 22.04 with thermal printers"
date: 2024-05-13
forum: Hardware
---

### Post by chibioni on 2024-05-13
I have tested this in two thermal printers STAR TSP 700II and Partnertech RP700 for receipt types 80mm x (infinite). 

I am trying to print a postscript file via cups (I have setup the ppd) and I am getting a large amount of blank space to the top of the receipt. I am using the same code in ubuntu 16.04 and 20.04 and they print correctly (same code, same printers) so the only thing that changes is the version of the cups components (and possibly any new configuration I am not aware of).

Is there any new update switch/command that cups / cups-filters / ghostscript filters use and disrupt this functionality?

My ppd (rp700.ppd) is:

```

$ cat rp700.ppd 
*PPD-Adobe:             "4.3"
*FormatVersion:         "4.3"
*FileVersion:           "1.0"
*LanguageVersion:       English
*LanguageEncoding:      ISOLatin1
*PCFileName:            "rp700.ppd"
*Manufacturer:          "PTT"
*Product:               "(CUPS v1.0)"
*1284DeviceID:          "MFG:PTT;CMD:PTT;MDL:RP-700;CLS:PTT;"
*cupsVersion:           1.1
*cupsManualCopies:      True
*cupsModelNumber:       RP-700
*cupsFilter:            "application/vnd.cups-raster 0 rastertorp700"
*ModelName:             "RP-700"
*ShortNickName:         "RP-700"
*NickName:              "PTT RP-700 CUPS v3.10"
*PSVersion:             "(3010.000) 550"
*LanguageLevel:         "3"
*ColorDevice:           False
*DefaultColorSpace:     Gray
*FileSystem:            False
*Throughput:            "1"
*LandscapeOrientation:  Plus90
*VariablePaperSize:     True
*TTRasterizer:          Type42




*OpenUI *PageSize/Media Size: PickOne
*OrderDependency: 10 AnySetup *PageSize
*DefaultPageSize: Paper297
*PageSize Paper297:    "<</PageSize[204 893]/ImagingBBox null>>setpagedevice"
*PageSize Paper210:    "<</PageSize[204 646]/ImagingBBox null>>setpagedevice"
*CloseUI: *PageSize


*OpenUI *PageRegion: PickOne
*OrderDependency: 10 AnySetup *PageRegion
*DefaultPageRegion: Paper297
*PageSize Paper297:    "<</PageSize[204 893]/ImagingBBox null>>setpagedevice"
*PageSize Paper210:    "<</PageSize[204 646]/ImagingBBox null>>setpagedevice"
*CloseUI: *PageRegion


*DefaultImageableArea: Paper297 
*ImageableArea Paper297:  "0.0 0.0 204.0 891.0"
*ImageableArea Paper210:  "0.0 0.0 204.0 644.0"


*DefaultPaperDimension: Paper297
*PaperDimension Paper297:    "204 893"
*PaperDimension Paper210:    "204 646"


*MaxMediaWidth: "204"
*MaxMediaHeight: "9286"
*HWmargins:      0 0 0 0 
*CustomPageSize True: "pop pop pop <</PageSize [ 5 -2 roll ]/ImagingBBox null>>setpagedevice"
*CenterRegistered: False
*ParamCustomPageSize Width:         1 points 0 204
*ParamCustomPageSize Height:        2 points 0 9286
*ParamCustomPageSize WidthOffset:   3 points 0 0
*ParamCustomPageSize HeightOffset:  4 points 0 0
*ParamCustomPageSize Orientation:   5 int 0 0


*OpenUI *Resolution/Resolution: PickOne
*OrderDependency: 20 AnySetup *Resolution
*DefaultResolution: 203x203dpi
*Resolution 203x203dpi/203x203DPI: "<</HWResolution[203 203]>>setpagedevice"
*CloseUI: *Resolution




*OpenUI *Buzzer/Beep: PickOne
*DefaultBuzzer: 0Off
*Buzzer 0Off/BeepOff: ""
*Buzzer 1One/Beep200milliseconds: ""
*Buzzer 2Three/Beep600milliseconds: ""
*Buzzer 3Five/Beep one Second: ""
*Buzzer 4Ten/Beep two Second: ""
*Buzzer 5Twenty/Beep four Second: ""
*CloseUI: *Buzzer




*OpenUI *Darkness/Darkness: PickOne
*DefaultDarkness: 6
*Darkness 0/Density0: ""
*Darkness 1/Density1: ""
*Darkness 2/Density2: ""
*Darkness 3/Density3: ""
*Darkness 4/Density4: ""
*Darkness 5/Density5: ""
*Darkness 6/Density6: "" 
*Darkness 7/Density7: ""
*Darkness 8/Density8: ""
*Darkness 9/Density9: ""
*Darkness 10/Density10: ""
*Darkness 11/Density11: ""
*Darkness 12/Density12: ""
*Darkness 13/Density13: ""
*Darkness 14/Density14: ""
*Darkness 15/Density15: ""
*Darkness 16/Density16: ""
*CloseUI: *Darkness


*OpenUI *PrintLogo/PrintLogo: PickOne
*DefaultPrintLogo: 0logo
*PrintLogo 0logo/NotPrintLogo: ""
*PrintLogo 1logo/PrintLogo1: ""
*PrintLogo 2logo/PrintLogo2: ""
*PrintLogo 3logo/PrintLogo3: ""
*PrintLogo 4logo/PrintLogo4: ""
*PrintLogo 5logo/PrintLogo5: ""
*PrintLogo 6logo/PrintLogo6: ""
*PrintLogo 7logo/PrintLogo7: ""
*PrintLogo 8logo/PrintLogo8: ""
*PrintLogo 9logo/PrintLogo9: ""
*CloseUI: *PrintLogo




*OpenGroup: CutGroup/Cut Options
*OpenUI *DocCutType/1. Document Cut Type: PickOne
*DefaultDocCutType: 1PartialCutDoc
*DocCutType 0NoCutDoc/No Cut: ""
*DocCutType 1PartialCutDoc/Partial Cut: ""
*DocCutType 2FullCutDoc/Full Cut: ""
*CloseUI: *DocCutType
*CloseGroup: CutGroup


*OpenGroup: CashDrawerGroup/Cash Drawer Control
*OpenUI *CashDrawer/1. Cash Drawer: PickOne
*DefaultCashDrawer: 0DoNotOpenDrawers
*CashDrawer 0DoNotOpenDrawers/Do Not Open Drawers: ""
*CashDrawer 1OpenDrawer1/Open Drawer 1: ""
*CashDrawer 2OpenDrawer2/Open Drawer 2: ""
*CashDrawer 3OpenDrawer3/Open Drawers 1 and 2: ""
*CashDrawer 4OpenDrawer4/Open Herald: ""
*CloseUI: *CashDrawer


*OpenUI *CashDrawer1PulseWidth/2. Cash Drawer Pulse Width: PickOne
*DefaultCashDrawer1PulseWidth: 3Millis60
*CashDrawer1PulseWidth 0Millis10/10 milliseconds: ""
*CashDrawer1PulseWidth 1Millis20/20 milliseconds: ""
*CashDrawer1PulseWidth 2Millis40/40 milliseconds: ""
*CashDrawer1PulseWidth 3Millis60/60 milliseconds: ""
*CloseUI: *CashDrawer1PulseWidth
*CloseGroup: CashDrawerGroup


*% End

```

These are my lpoptions on ubuntu 16.04:

```

$ lpoptions -p PTech-RP700 -l
PageSize/Media Size: *Paper297 Paper210 Custom.WIDTHxHEIGHT
Resolution/Resolution: *203x203dpi
Buzzer/Beep: *0Off 1One 2Three 3Five 4Ten 5Twenty
Darkness/Darkness: 0 1 2 3 4 5 *6 7 8 9 10 11 12 13 14 15 16
PrintLogo/PrintLogo: *0logo 1logo 2logo 3logo 4logo 5logo 6logo 7logo 8logo 9logo
DocCutType/1. Document Cut Type: 0NoCutDoc *1PartialCutDoc 2FullCutDoc
CashDrawer/1. Cash Drawer: *0DoNotOpenDrawers 1OpenDrawer1 2OpenDrawer2 3OpenDrawer3 4OpenDrawer4
CashDrawer1PulseWidth/2. Cash Drawer Pulse Width: 0Millis10 1Millis20 2Millis40 *3Millis60

$ lpoptions -p PTech-RP700
copies=1 device-uri=usb://PTT/RP-700(U)1 finishings=3 job-cancel-after=10800 job-hold-until=no-hold job-priority=50 job-sheets=none,none marker-change-time=0 number-up=1 printer-commands=none printer-info=PTech-RP700 printer-is-accepting-jobs=true printer-is-shared=true printer-location printer-make-and-model='PTT RP-700 CUPS v3.10' printer-state=3 printer-state-change-time=1578926825 printer-state-reasons=none printer-type=167940 printer-uri-supported=ipp://localhost/printers/PTech-RP700

```

And in 22.04:

```

$ lpoptions -p PTech-RP700
copies=1 device-uri=usb://PTT/RP-700(U)1 finishings=3 job-cancel-after=10800 job-hold-until=no-hold job-priority=50 job-sheets=none,none marker-change-time=0 number-up=1 PageSize=A4 print-color-mode=monochrome printer-commands=none printer-info=PTech-RP700 printer-is-accepting-jobs=true printer-is-shared=true printer-is-temporary=false printer-location printer-make-and-model='PTT RP-700 CUPS v3.10' printer-state=3 printer-state-change-time=1715588054 printer-state-reasons=none printer-type=36868 printer-uri-supported=ipp://localhost/printers/PTech-RP700
$ lpoptions -p PTech-RP700 -l
PageSize/Media Size: *Paper297 Paper210 Custom.WIDTHxHEIGHT
Resolution/Resolution: *203x203dpi
Buzzer/Beep: *0Off 1One 2Three 3Five 4Ten 5Twenty
Darkness/Darkness: 0 1 2 3 4 5 *6 7 8 9 10 11 12 13 14 15 16
PrintLogo/PrintLogo: *0logo 1logo 2logo 3logo 4logo 5logo 6logo 7logo 8logo 9logo
DocCutType/1. Document Cut Type: 0NoCutDoc *1PartialCutDoc 2FullCutDoc
CashDrawer/1. Cash Drawer: *0DoNotOpenDrawers 1OpenDrawer1 2OpenDrawer2 3OpenDrawer3 4OpenDrawer4
CashDrawer1PulseWidth/2. Cash Drawer Pulse Width: 0Millis10 1Millis20 2Millis40 *3Millis60

```

I am puzzled with this because it is breaking the receipt printing in newer than 20.04 releases and I believe it's got something to do with pdftopdf cups filter and resizing. The order of the filters I am running are:

```

$ cupsfilter -d PTech-RP700 -c /etc/cups/cupsd.conf -p /usr/share/cups/model/rp700.ppd -m printer/foo -e --list-filters /etc/nsswitch.conf 
cupsfilter: File "/usr/lib/cups/filter/rastertorp700" permissions OK (0100755/uid=0/gid=0).
texttopdf
pdftopdf
gstoraster
rastertorp700

```

Is it possible it is related to pagesize=A4 ? How do I make this with custom variable?

---

