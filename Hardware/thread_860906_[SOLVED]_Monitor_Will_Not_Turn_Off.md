---
title: "[SOLVED] Monitor Will Not Turn Off"
date: 2008-07-16
forum: Hardware
---

### Post by sstusick on 2008-07-16
I've been having this problem ever since I upgraded to Hardy. The monitor will not turn off, regardless of what the settings are. Right now the laptop monitor is set to shut off after 8 minutes of inactivity. I leave the computer for 20 minutes and the monitor is still on as if I never left the machine. 

This has been bugging me for a long time now, and the only solution I have found is running > xset dpms force off via the terminal when I leave the computer for several hours. I know someone is going to say "Oh just turn the laptop off" well that is not an option, as I have the computer completing tasks while I am away. I could shut the screen, but that would cause the machine to heat up more than necessary - and regardless, the monitor **should** turn off when it's supposed to.

What's going on here? It worked in Feisty and it worked in Gutsy but now it's not working in Hardy. I have tried re-installing the OS and I've searched the forums to no avail. 

I would file a bug report, but that seems to be a waste of time, because once I filed a bug report in Gutsy, they came back and told me it was fixed but the same issue existed in Hardy.

Specs: Toshiba Laptop A105-S4004 Ubuntu Hardy 8.04.1 

Output of lspci:
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)


If anyone has a solution, I'd like to hear it. Thanks.

---

### Post by ModelM on 2008-07-16
When I had this problem it was because I had the screensaver turned off. Turning on the screensaver then enabled the screensaver after the proper time, and turned the monitor off at the proper time, also.

I didn't want the screensaver, I just wanted to turn the monitor off. However this is the only way I could get it to work...

---

### Post by sstusick on 2008-07-16
Hmm isn't that strange. Well I will try that! Thank you for your response :)

---

