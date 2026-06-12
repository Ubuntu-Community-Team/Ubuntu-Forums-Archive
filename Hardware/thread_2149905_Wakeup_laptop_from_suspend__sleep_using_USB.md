---
title: "Wakeup laptop from suspend / sleep using USB"
date: 2013-05-30
forum: Hardware
---

### Post by KingOfTheNothing on 2013-05-30
I have ubuntu 13.04 64 bit x86 on my laptop and I am trying to make it possible to wakeup using my wireless keyboard, thus I need to enable wakeup on USB. I have read several guides but it simply does not work. I need to enable USBX below. Please make the guide very easy to follow. Thanks! When I use windows I can wake the computer from sleep using the same keyboard.

Device    S-state      Status   Sysfs node
P0P1      S4    *disabled
PEG0      S4    *disabled
PEG1      S4    *disabled
PEG2      S4    *disabled
PEG3      S4    *disabled
XHC1      S3    *enabled   pci:0000:00:14.0
EHC1      S3    *enabled   pci:0000:00:1d.0
USB1      S3    *disabled
USB2      S3    *disabled
USB3      S3    *disabled
USB4      S3    *disabled
EHC2      S3    *enabled   pci:0000:00:1a.0
USB5      S3    *disabled
USB6      S3    *disabled
USB7      S3    *disabled
HDEF      S4    *disabled  pci:0000:00:1b.0
RP05      S4    *disabled
RP06      S4    *disabled
RP07      S4    *disabled
RP08      S4    *disabled
WLAN      S3    *disabled  pci:0000:02:00.0
RP03      S4    *disabled
XHCI      S3    *disabled
RP04      S4    *disabled  pci:0000:00:1c.3
GLAN      S4    *enabled   pci:0000:03:00.2
XHC      S4    *disabled
SLPB      S4    *disabled

---

### Post by KingOfTheNothing on 2013-05-31
Hi all!

I have some more information that might clarify some things. Look below in the list on the usb there are no pci connected and on these items that do not have a pci listed I cannot change disable to enable. i.e I manged to change disable to enable by using the command sudo sh -c "echo RP04 > /proc/acpi/wakeup" for the RP04 device and this is possible because there is a pci listed on this device. So how do I add a pci to the usb devices is this possible due to hardware??? If I purchase a usb card will this have a pci listed on it?? I am guessing that the usb are connected directly to the mother board.

Thanks!

 


P0P1      S4    *disabled
PEG0      S4    *disabled
PEG1      S4    *disabled
PEG2      S4    *disabled
PEG3      S4    *disabled
XHC1      S3    *enabled   pci:0000:00:14.0
EHC1      S3    *enabled   pci:0000:00:1d.0
USB1      S3    *disabled
USB2      S3    *disabled
USB3      S3    *disabled
USB4      S3    *disabled
EHC2      S3    *enabled   pci:0000:00:1a.0
USB5      S3    *disabled
USB6      S3    *disabled
USB7      S3    *disabled
HDEF      S4    *enabled   pci:0000:00:1b.0
RP05      S4    *disabled
RP06      S4    *disabled
RP07      S4    *disabled
RP08      S4    *disabled
WLAN      S3    *enabled   pci:0000:02:00.0
RP03      S4    *disabled
XHCI      S3    *disabled
RP04      S4    *enabled   pci:0000:00:1c.3
GLAN      S4    *enabled   pci:0000:03:00.2
XHC      S4    *disabled
SLPB      S4    *disabled

---

### Post by KingOfTheNothing on 2013-06-03
No answer on this?? I will now leave ubuntu and start to use windows again due to this problem. It is really sad. There should be a simple solution to this problem I guess there are alot that want to use Ubuntu on their htpc and to start it from a wireless keyboard is a base function that most people want.

---

