---
title: "problem: installation of the wlan usb adapter"
date: 2009-12-11
forum: Hardware
---

### Post by alfo982 on 2009-12-11
[COLOR=black][FONT=Verdana][SIZE=3]Hi everyone... I would say first of all that I’m a complete newbie in Linux: just yesterday I took an old Computer and I installed for the first time Ubuntu 9.10… just to try and see if I like it![/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=3]FIRST PROBLEM: installation of the USB wireless adapter!![/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=3]Now, I tried to fix the problem by surfing in internet… and I’ve done a step forward (I think): I installed ndiswrapper and ndisgtk. Then I mounted the .inf file from the win-driver cd of my pen and I waited the results.[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=3]No way: the program told me a thing that sounds like “unable to detect if the hardware is present” (I don’t remember the right words… I made it yesterday evening).[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=3]I’m afraid that from now on I will not be able to proceed without the help of an expert in this field.[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=3]What do you suggest me? To downgrade Ubuntu? To buy a new pen? What else[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=3]I hope you can help me… I really need it: in the Italian UBUNTU forum (I’m Italian…) no one answer me: I’m sure that here it will be easier to receive a support![/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=3]Bye and thanks in advice[/SIZE][/FONT][/COLOR]

---

### Post by Fafler on 2009-12-11
Open the .inf file i a editor and look for the USB device ID's. Open a terminal and type lsusb. It shows a list of connected USB devices and their vendor and device ID's. They should be the same. If not, you got the wrong driver. You might try changing the vendor and device ID's in the .inf file and try installing it again.

What's the wireless device called?

---

### Post by alfo982 on 2009-12-11
[COLOR=black][FONT=Verdana]Right, yesterday I used the command lsusb, and I've seen that the device is winbond wlan adapter (today afternoon I will see again, in order to give you the right name).[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]The problem is that in ndisgtk under the big name of the driver, it is written (in smaller fonts) that the hardware is present, but in the scroll menu of the connection devices (upper right of the desktop) there isn&#8217;t the wlan usb device, and there are no leds on, on the pen[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Why should be the drivers not right for him? The mini-CD was included in the packet.[/FONT][/COLOR]

---

### Post by Fafler on 2009-12-11
Sorry, didn't see you took the drivers from the CD. Every time i buy hardware, i usually throw the driver disc away as the first thing ;-)

Anyway, try googling the vendor and device ID's + ndiswrapper. Thats usually helpfull.

---

### Post by coffeecat on 2009-12-11
> **alfo982 said:**
> [COLOR=black][FONT=Verdana]Right, yesterday I used the command lsusb, and I've seen that the device is winbond wlan adapter (today afternoon I will see again, in order to give you the right name).[/FONT][/COLOR]

Please post the whole of the lsusb line for your wireless adapter. Depending on the actual chipset it contains, you may not even need to use ndiswrapper - there may be an easier way. If the lsusb line doesn't positively identify the actual chipset (this is often the case) there will be an ID number that can be googled.

---

### Post by alfo982 on 2009-12-11
OK...  here it is!

> all@Linux-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0416:0035 Winbond Electronics Corp. W89C35 802.11bg WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
all@Linux-desktop:~$ 

and the text of the .inf file is

> 
;=======================================================================================
; NETW35W.INF
;
; Information (INF) file for ISSC W89C35 802.11bg WLAN USB Adapters (Native Wifi driver)
;
; Copyright (C) Integrated System Solution Corp. All Rights Reserved
;=======================================================================================

[version]
Signature      = "$Windows NT$"
Class          = Net
ClassGUID      = {4D36E972-E325-11CE-BFC1-08002BE10318}
Provider       = %ISSC%
CatalogFile    = netw35w.cat                        ;; for WHQL certified
DriverVer      = 10/26/2006,4.0.46.5


[Manufacturer]
%ISSC%         = W89C35_Model, NTx86
%Q802%         = Q802UWG_Model, NTx86

[ControlFlags]
ExcludeFromSelect = *


[W89C35_Model.NTx86]
; DisplayName                   Section         DeviceID
; -----------                   -------         --------
%W89C35.DeviceDesc%  = W89C35.ndi, USB\VID_0416&PID_0035
%W89C35.DeviceDesc%  = W89C35.ndi, USB\VID_1131&PID_2035
%W89C35.DeviceDesc%  = W89C35.ndi, USB\VID_ffff&PID_ffff

[Q802UWG_Model.NTx86]
; Display Name           Section        Device ID
%Q802UWG.DeviceDesc%  = W89C35.ndi, USB\VID_18E8&PID_6201
%Q802UWG.DeviceDesc%  = W89C35.ndi, USB\VID_18E8&PID_6206
%Q802UWG.DeviceDesc%  = W89C35.ndi, USB\VID_18E8&PID_6217
%Q802UWG.DeviceDesc%  = W89C35.ndi, USB\VID_18E8&PID_6230
%Q802UWG.DeviceDesc%  = W89C35.ndi, USB\VID_18E8&PID_6233


[W89C35.ndi.NTx86]
Characteristics = 0x84
BusType         = 15
AddReg          = W89C35.reg
CopyFiles       = W89C35.CopyFiles
*IfType         = 71        ; IF_TYPE_IEEE80211
*MediaType      = 16        ; NdisMediumNative802_11
*PhysicalMediaType = 9        ; NdisPhysicalMediumNative802_11

[W89C35.ndi.NTx86.Services]
AddService = W35UNDW, 2, W35UNDW.Service, W35UNDW.EventLog


[W89C35.reg]
HKR, Ndi,                         Service,    0, "W35UNDW"

HKR, Ndi\Interfaces,              UpperRange, 0, "ndis5"
HKR, Ndi\Interfaces,              LowerRange, 0, "wlan,ethernet"

;PLT
HKR, Ndi\params\PLT,                ParamDesc,  0, "PLT"
HKR, Ndi\params\PLT,                default,    0, "0"
HKR, Ndi\params\PLT,                type,       0, "enum"
HKR, Ndi\params\PLT\enum,           "0",        0, "Disable"
HKR, Ndi\params\PLT\enum,           "1",        0, "Enable"

;RATE POLICY
HKR, Ndi\params\RatePolicy,         ParamDesc,  0, "RatePolicy"
HKR, Ndi\params\RatePolicy,         default,    0, "2"
HKR, Ndi\params\RatePolicy,         type,       0, "enum"
HKR, Ndi\params\RatePolicy\enum,    "0",        0, "Default"
HKR, Ndi\params\RatePolicy\enum,    "1",        0, "Up speed"
HKR, Ndi\params\RatePolicy\enum,    "2",        0, "Down speed"

;REGION
HKR, Ndi\params\Region,                ParamDesc,  0, "Region"
HKR, Ndi\params\Region,                default,    0, "0"
HKR, Ndi\params\Region,                type,       0, "enum"
HKR, Ndi\params\Region\enum,           "3",        0, "Channel 1-11"
HKR, Ndi\params\Region\enum,           "1",        0, "Channel 1-13"
HKR, Ndi\params\Region\enum,           "2",        0, "Channel 1-14"
HKR, Ndi\params\Region\enum,           "4",        0, "Channel 10-13"
HKR, Ndi\params\Region\enum,           "5",        0, "Channel 10-11"
HKR, Ndi\params\Region\enum,           "6",        0, "Channel 3-9"
HKR, Ndi\params\Region\enum,           "0",        0, "Reg_Unknown"

;RADIO
HKR, Ndi\params\Radio,                 ParamDesc,  0, "Radio"
HKR, Ndi\params\Radio,                 default,    0, "0"
HKR, Ndi\params\Radio,                 type,       0, "enum"
HKR, Ndi\params\Radio\enum,            "0",        0, "ON"
HKR, Ndi\params\Radio\enum,            "1",        0, "OFF"

;MaxTxRate
HKR, Ndi\params\MaxTxRate,      ParamDesc,  0, "Data Rate"
HKR, Ndi\params\MaxTxRate,      default,    0, "0"
HKR, Ndi\params\MaxTxRate,      type,       0, "enum"
HKR, Ndi\params\MaxTxRate\enum, "0",        0, "Auto"
HKR, Ndi\params\MaxTxRate\enum, "2",        0, "1 Mbps"
HKR, Ndi\params\MaxTxRate\enum, "4",        0, "2 Mbps"
HKR, Ndi\params\MaxTxRate\enum, "11",       0, "5.5 Mbps"
HKR, Ndi\params\MaxTxRate\enum, "22",       0, "11 Mbps"
HKR, Ndi\params\MaxTxRate\enum, "12",       0, "6 Mbps"
HKR, Ndi\params\MaxTxRate\enum, "18",       0, "9 Mbps"
HKR, Ndi\params\MaxTxRate\enum, "24",       0, "12 Mbps"
HKR, Ndi\params\MaxTxRate\enum, "36",       0, "18 Mbps"
HKR, Ndi\params\MaxTxRate\enum, "48",       0, "24 Mbps"
HKR, Ndi\params\MaxTxRate\enum, "72",       0, "36 Mbps"
HKR, Ndi\params\MaxTxRate\enum, "96",       0, "48 Mbps"
HKR, Ndi\params\MaxTxRate\enum, "108",      0, "54 Mbps"
HKR, Ndi\params\MaxTxRate\enum, "255",      0, "Max"

;Preamble
HKR, Ndi\params\Preamble,           ParamDesc,  0, "Preamble Mode"
HKR, Ndi\params\Preamble,           default,    0, "0"
HKR, Ndi\params\Preamble,           type,       0, "enum"
HKR, Ndi\params\Preamble\enum,      "0",        0, "Auto Tx Preamble (Long/Short)"
HKR, Ndi\params\Preamble\enum,      "1",        0, "Long Tx Preamble"

;Channel
HKR, Ndi\params\Channel,            ParamDesc,  0, "IBSS Channel No."
HKR, Ndi\params\Channel,            default,    0, "0"
HKR, Ndi\params\Channel,            type,       0, "enum"
HKR, Ndi\params\Channel\enum,        "2412",        0, " 1"
HKR, Ndi\params\Channel\enum,        "2417",        0, " 2"
HKR, Ndi\params\Channel\enum,        "2422",        0, " 3"
HKR, Ndi\params\Channel\enum,        "2427",        0, " 4"
HKR, Ndi\params\Channel\enum,        "2432",        0, " 5"
HKR, Ndi\params\Channel\enum,        "2437",        0, " 6"
HKR, Ndi\params\Channel\enum,        "2442",        0, " 7"
HKR, Ndi\params\Channel\enum,        "2447",        0, " 8"
HKR, Ndi\params\Channel\enum,        "2452",        0, " 9"
HKR, Ndi\params\Channel\enum,        "2457",        0, "10"
HKR, Ndi\params\Channel\enum,        "2462",        0, "11"
HKR, Ndi\params\Channel\enum,        "2467",        0, "12"
HKR, Ndi\params\Channel\enum,        "2472",        0, "13"
HKR, Ndi\params\Channel\enum,        "2484",        0, "14"
HKR, Ndi\params\Channel\enum,        "0",        0, "Auto"

;RTSThreshold
HKR, Ndi\params\RTSThreshold,       ParamDesc,  0, "RTS Threshold"
HKR, Ndi\params\RTSThreshold,       default,    0, "2347"
HKR, Ndi\params\RTSThreshold,       type,       0, "int"
HKR, Ndi\params\RTSThreshold,       min,        0, "0"
HKR, Ndi\params\RTSThreshold,       max,        0, "2347"

;TxFragThreshold
HKR, Ndi\params\TxFragThreshold,    ParamDesc,  0, "Fragmentation Threshold"
HKR, Ndi\params\TxFragThreshold,    default,    0, "2346"
HKR, Ndi\params\TxFragThreshold,    type,       0, "int"
HKR, Ndi\params\TxFragThreshold,    min,        0, "256"
HKR, Ndi\params\TxFragThreshold,    max,        0, "2346"
HKR, Ndi\params\TxFragThreshold,    step,       0, "2"

;PowerSaveMode
HKR, Ndi\params\PowerSave,          ParamDesc,  0, "Power Save Mode"
HKR, Ndi\params\PowerSave,          default,    0, "0"
HKR, Ndi\params\PowerSave,          type,       0, "enum"
HKR, Ndi\params\PowerSave\enum,     "0",        0, "Disabled"
HKR, Ndi\params\PowerSave\enum,     "1",        0, "Enabled"

;Background scan
HKR, Ndi\params\BScan,          ParamDesc,  0, "Background Scan"
HKR, Ndi\params\BScan,          default,    0, "1"
HKR, Ndi\params\BScan,          type,       0, "enum"
HKR, Ndi\params\BScan\enum,     "0",        0, "Disabled"
HKR, Ndi\params\BScan\enum,     "1",        0, "Enabled"

;ModulationType
HKR, Ndi\params\ModulationType,        ParamDesc,  0, "Modulation Type"
HKR, Ndi\params\ModulationType,     default,    0, "255"
HKR, Ndi\params\ModulationType,     type,       0, "enum"
HKR, Ndi\params\ModulationType\enum,"0",        0, "802.11b/g"
;HKR, Ndi\params\ModulationType\enum,"1",        0, "802.11a"
;HKR, Ndi\params\ModulationType\enum,"2",        0, "802.11a/b/g"
HKR, Ndi\params\ModulationType\enum,"3",        0, "802.11g-IBSS"
HKR, Ndi\params\ModulationType\enum,"255",    0, "AUTO"



[W35UNDW.Service]
DisplayName     = %W35UND.Service.DispName%
ServiceType     = 1         ;SERVICE_KERNEL_DRIVER
StartType       = 3         ;SERVICE_DEMAND_START
ErrorControl    = 1         ;SERVICE_ERROR_NORMAL
ServiceBinary   = %12%\W35UNDW.SYS
LoadOrderGroup  = NDIS



[W35UNDW.EventLog]
AddReg = W35UNDW.AddEventLog.reg

[W35UNDW.AddEventLog.reg]
HKR, , EventMessageFile, 0x00020000, "%%SystemRoot%%\System32\netevent.dll"
HKR, , TypesSupported,   0x00010001, 7


[W89C35.CopyFiles]
W35UNDW.SYS,,,2

[SourceDisksNames]
1              = %DiskName%,,,

[SourceDisksFiles]
W35UNDW.SYS     = 1

[DestinationDirs]
W89C35.CopyFiles          = 12
DefaultDestDirs            = 11


[Strings]
Q802                      = "802.11 b/g USB Wireless Adapter"
Q802UWG.DeviceDesc        = "802.11 b/g USB Wireless Adapter"

ISSC                      = "Integrated System Solution Corp."
W89C35.DeviceDesc         = "W89C35 802.11bg WLAN USB Adapter"
W35UND.Service.DispName    = "W89C35 802.11bg WLAN USB Adapter Driver"
W35UND.Service.Description = "W89C35 802.11bg WLAN USB Adapter Driver"

DiskName                     = "802.11bg WLAN USB Adapter Driver Disk"

do u need more infos?

what do you think?

thank you...

---

### Post by coffeecat on 2009-12-11
Unfortunately, googlng '0416:0035' (the ID number) was fairly unrewarding. Mostly a few threads on this forum none of which were posted as resolved.

It's possible that 'Winbond' is the chipset manufacturer. And searching for 'Winbond' in the Ubuntu Wiki and Ubuntu Community documentation sites was also unrewarding.

It seems that ndiswrapper is your only hope. Sorry. No further ideas. It's a pity because many USB wireless devices work quite well with the inbuilt drivers that come with the Ubuntu Linux kernel.

---

### Post by alfo982 on 2009-12-11
But why when I push the button "configure network" nothing happens?

---

### Post by alfo982 on 2009-12-11
I made a new trial: I found in internet another driver... now on the upper right side of the desktop a new device is appeared, but it is offline

let see the image...

does this mean anything?
Is it a step forward for you or not necessarily?

thx


PS: How can I see if the pen is installed well? And how can I understand if the problem depends on the network configuration, and not on the drivers?

---

### Post by Fafler on 2009-12-12
It seems like a step forward.

Try 

```
sudo iwconfig
sudo iwlist scanning
```

from a terminal. That should give some info about the interface and a scan for nearby accesspoints.

---

### Post by alfo982 on 2009-12-14
I have already given this command... and the pen cannot scan me nothing!
 
So I decided to downgrade the Karmic to the Jaunty... and now everything works well!
 
That was the only solution that I could find... now I wait that these incompatibilities will be solved, and then I will do the upgrade again...
 
However... thx everybody for the help...

---

