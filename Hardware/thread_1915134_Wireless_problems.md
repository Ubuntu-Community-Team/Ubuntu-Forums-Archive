---
title: "Wireless problems"
date: 2012-01-25
forum: Hardware
---

### Post by Talva720 on 2012-01-25
hy im having a hard time to put my wireless card to work my laptop is a hp tx2020eo, iv inserted these commands in the terminal and these wore the outputs of each on in order lspci and lsusb

talva@torgnyMercuryNotebook:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce Go 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

talva@torgnyMercuryNotebook:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 001 Device 004: ID 04f2:b015 Chicony Electronics Co., Ltd VGA 24fps UVC Webcam
Bus 001 Device 005: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 001 Device 006: ID 056a:0093 Wacom Co., Ltd TPC93


and i dont know if its installed or configured yet!
I would apreciate some assistance in this matter thanks!

---

### Post by madvinegar on 2012-01-26
I cannot even see your wireless card in the results of lspci.

I suspect that you should be having a broadcom adapter for your wireless (given that you have an HP) so do the following:

First of all plug your laptop with an ethernet cable (to get internet), open "synaptics package manager" and click "reload".

Then click on "mark all upgrades" and then "apply".


Wait for it to load and install all the necessary drivers/packages and then reboot.

I hope that after that, if you write again lspci in terminal, your card will show up. (please re-post the results)

After that, go again in "synaptics package manager" and make sure that the following two packages are installed.

"b43-fwcutter"
"firmware-b43-installer"

If one of them is missing (probably the 2nd one), right click on it - mark for installation - apply.

After that I hope that you will see the blue light of the wifi...


P.S.: Ofcourse, there is a chance that a set of other packages should be installed (probably the b43-fwcutter together with the firmware-b43-ipphy-installer, but this will depend on the exact model of your broadcom card (which we will see if we can get it to show up in lscpi).

---

### Post by nipunshakya on 2012-01-26
> **Talva720 said:**
> hy im having a hard time to put my wireless card to work my laptop is a hp tx2020eo, iv inserted these commands in the terminal and these wore the outputs of each on in order lspci and lsusb

talva@torgnyMercuryNotebook:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce Go 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

talva@torgnyMercuryNotebook:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 001 Device 004: ID 04f2:b015 Chicony Electronics Co., Ltd VGA 24fps UVC Webcam
Bus 001 Device 005: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 001 Device 006: ID 056a:0093 Wacom Co., Ltd TPC93


and i dont know if its installed or configured yet!
I would apreciate some assistance in this matter thanks!

Do you have a software called "Additional Drivers" installed in your ubuntu?
Goto Software Center and type "Additional Drivers". Select the software, install it. After installation, run the software. The software will automatically identify your additional drivers needed...wireless module might also be detected. Select them, click activate and restart after done...Check if this fixes your issue..Goodluck

Regards,WinuxUser

---

### Post by madvinegar on 2012-01-26
> **WinuxUser said:**
> Do you have a software called "Additional Drivers" installed in your ubuntu?
Goto Software Center and type "Additional Drivers". Select the software, install it. After installation, run the software. The software will automatically identify your additional drivers needed...wireless module might also be detected. Select them, click activate and restart after done...Check if this fixes your issue..Goodluck

Regards,WinuxUser

Broadcom is e very peculiar card.
I say this because I have a broadcom card in my HP.
I had to install the packages I write above but **de**-activate the recommended driver from the "additional drivers" in order to get it to work.
So, lets wait first to see how things will go without activating the recomended driver...

---

### Post by nipunshakya on 2012-01-26
@madvinegar: i too have had a problem with wireless module of my Dell laptop and its Broadcom too... Worked out for me with the additional drivers stuff at once...maybe the recommended driver might help him out as well.. ;)

---

### Post by madvinegar on 2012-01-26
True.

He can try both options.

But, in any case he has first to plug his laptop with ethernet cable and get internet and then update the packages in Synaptic as I explain above.

---

### Post by nipunshakya on 2012-01-26
Agreed to that too... ;)

---

### Post by Talva720 on 2012-01-27
thanks for the help so far guys i dont know really if there is something difrente in the list by that i mean if the card shows up now. but hope you can help me out thanks so far.

talva@torgnyMercuryNotebook:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce Go 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control


talva@torgnyMercuryNotebook:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 002 Device 002: ID 1bcf:08d8 Sunplus Innovation Technology Inc. 
Bus 002 Device 003: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 001 Device 005: ID 04f2:b015 Chicony Electronics Co., Ltd VGA 24fps UVC Webcam
Bus 001 Device 006: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 001 Device 007: ID 056a:0093 Wacom Co., Ltd TPC93


PS:yes this is an HP 2020eo model as think i mentioned in my last post.

---

### Post by nipunshakya on 2012-01-27
> **Talva720 said:**
> 
Bus 002 Device 002: ID 1bcf:08d8 Sunplus Innovation Techology Inc. 
this has been found new in your system. would u mind what did u do in your machine and generated that output? did u go via additional driver installation or go with madvinegar's option?? lets know that first.

Regards,WinuxUser

---

### Post by Talva720 on 2012-01-27
well what i did was to follow the first porcedure that is open "synaptics package manager" and click "reload".

Then click on "mark all upgrades" and then "apply".


Wait for it to load and install all the necessary drivers/packages and then reboot.


After that, i went in "synaptics package manager" and maked sure that the following two packages ***** installed.

"b43-fwcutter"
"firmware-b43-installer"

---

### Post by nipunshakya on 2012-01-27
okay...if that even doesn't help you out, why don't you try the procedure i suggested you in above post of mine....if u need details, ask me...Goodluck

---

### Post by madvinegar on 2012-01-28
First of all lets clarify something.

I see this in lsusb

```
Bus 002 Device 003: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
```


Is your card internal or external (plugged in a USB slot)????

---

### Post by nipunshakya on 2012-01-28
It says integrated module...so obviously its a built in feature..:D

---

### Post by nipunshakya on 2012-01-28
let him try as i suggested....if that doesn't help him out, we are here...isn't it madvinegar?

---

### Post by madvinegar on 2012-01-30
True!
It is juts very strange that his card appears in lsusb...

---

### Post by rgreener25 on 2012-01-30
> **Talva720 said:**
> 
Bus 002 Device 003: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module] Surely That is the wifi device

---

### Post by nipunshakya on 2012-01-31
> **rgreener25 said:**
> Surely That is the wifi device

Is is really?? or is it a built-in module?

---

### Post by Talva720 on 2012-02-01
if there is something else that i missed plz help me out i can only see it in the lsusb list:

talva@LNX-Mercury:~$ lsusb
Bus 002 Device 003: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 056a:0093 Wacom Co., Ltd 
Bus 001 Device 005: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 001 Device 004: ID 04f2:b015 Chicony Electronics Co., Ltd VGA 24fps UVC Webcam
Bus 001 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Talva720 on 2012-02-01
this is a built in the laptop thats why i think its also strange to see it apear on lsusb! hope it helps!

---

### Post by Talva720 on 2012-02-01
sorry i dont know if this is important i have the linux 10.4 and in the first procedure where i hade to go to synaptic package manager i can mark all it dosent show to apply i think it dosent iven sellect the packages,and in the second procedure i tried the hardware drivers and in the list it only displayes the NVIDIA acelarator graphics dirver versions 173,96 and current version and recommended and the last option is the software modem 
hope this helps you out guys thanks for que help so far!!

---

### Post by nipunshakya on 2012-02-03
You don't have any packages selected because you already might have latest updates in your machine.....
in second case, you should select one of the uninstalled drivers and install them.The uninstalled driver has a grey solid sphere before its name while the installed driver has a green solid sphere. Just select the uninstalled driver, and on bottom right is a button named 'Activate'. Click on that and you will be asked for password and the driver will take few minutes to download...restart it and see if it helps...

Regards,WinuxUser

---

