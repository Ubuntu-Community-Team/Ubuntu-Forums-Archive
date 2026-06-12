---
title: "USB port(s) stop working"
date: 2008-08-28
forum: General Help
---

### Post by 68pontiac on 2008-08-28
Hello all, first post and recent Ubuntu user. I have a fairly fresh install of Hardy on a machine that used to run Vista. I'm very happy to have made the switch, but I have a problem that is becoming really annoying. The OS seems to randomly stop some of my USB ports. Typically, my USB wireless adapter quits but occasionally my printer will stop. My keyboard and mouse are also USB but those have never stopped. It happens randomly and everything is fine after a restart. Any help would be very greatly appreciated.

And as a side note, I also have a internal PCI wireless adapter that I could use, but I've never been able to get it to work properly. It's a Netgear WG311v3 and I've used ndiswrapper, installed the driver successfully but it'll never connect to the access point when it asks for my WEP key.

Bear in mind that I'm pretty good with computers, but very new to Ubuntu so taking it slow would be awesome. And I'm not great with terminal commands, so if there's a GUI way to do something, I'd prefer it.

THANKS!

---

### Post by tamoneya on 2008-08-28
next time it happens type this into terminal and post the results:```
dmesg | tail
```
It will give us some debugging info to work with.

---

### Post by 68pontiac on 2008-08-30
Okay, so the problem happened this time after waking the machine from hibernation. Here's the results of dmesg | tail

```
[10387.098561] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3050 with error -19.
[10387.098564] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3050 with error -19.
[10387.111787] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -19.
[10387.111797] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -19.
[10387.111801] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[10387.111804] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3028 with error -19.
[10387.111808] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -19.
[10387.111811] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0c failed for offset 0x0000 with error -19.
[10387.462160] usb 5-5: new high speed USB device using ehci_hcd and address 8
[10402.812959] usb 5-5: new high speed USB device using ehci_hcd and address 9
```

---

### Post by tevildo on 2008-11-26
I have just had this start happening on my box. The card (an Edimax 7317UHg with the Zydas 1211b chipset) has been working fine for almost a year now, but after a recent power cut started exhibiting this same behaviour.

I'm running Gentoo, not Ubuntu, but I suspect the solution may be the same/similar for both, so if I find a solution, I'll post a link here.

---

### Post by Nathan110 on 2009-04-26
This is the same with me i just installed the new ubuntu 9.04 and my usb ports keep stop working i use my wireless through a usb adapter and when im using it the usb ports stop working then i unplug the apapter from the usb port and then plug it back in and it works for a wile then goes of again and this keeps repeating 
 
HELLPPP its very annoying

---

### Post by roger_1960 on 2009-04-26
Hi

I have an Acer Aspire 5101 which now has 2 (out of 3) USB ports which seem to have permanently stopped working.  I suspect its hardware failure.  Have posted the output from dmesg | tail below.  Can anyone confirm its likely to be hardware?

> roger@lesgetschalets3:~$ dmesg | tail
[ 4130.126443] usb 1-1: device descriptor read/64, error -62
[ 4130.410382] usb 1-1: device descriptor read/64, error -62
[ 4130.690338] usb 1-1: new low speed USB device using ohci_hcd and address 10
[ 4131.098253] usb 1-1: device not accepting address 10, error -62
[ 4131.274209] usb 1-1: new low speed USB device using ohci_hcd and address 11
[ 4131.682132] usb 1-1: device not accepting address 11, error -62
[ 4158.872643] usb 1-4: new low speed USB device using ohci_hcd and address 12
[ 4159.083868] usb 1-4: configuration #1 chosen from 1 choice
[ 4159.101914] input: Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0 as /devices/pci0000:00/0000:00:13.0/usb1/1-4/1-4:1.0/input/input12
[ 4159.128700] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0] on usb-0000:00:13.0-4
roger@lesgetschalets3:~$

---

### Post by Nathan110 on 2009-04-26
must be a software problem hope they get it fixed soon :(

---

### Post by Saxicide on 2009-06-27
I'm running an Acer Aspire 5641 and Ubuntu causes ALL of my USB ports to stop working--to the point where I cannot finish the install, as my keyboard and mouse are USB.

---

### Post by Triptol on 2009-11-01
This thing seems to be repeating itself. I used to have this problem with Hardy or Intrepid (can't remember) but things were fine with Jaunty.

Now on Karmic and the problem has occurred again. Wondering whether someone know how they fixed it for Jaunty.

```
$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 13b1:0020 Linksys WUSB54GC 802.11g Adapter [ralink rt73]
Bus 001 Device 003: ID 2040:7070 Hauppauge Nova-T Stick 3
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
Errors (endless repeats in syslog):
```
Nov  1 07:35:41 shire kernel: [25016.061968] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -108.
```
lsmod:
```
$ lsmod | grep rt
rt73usb                26336  0 
crc_itu_t               1852  1 rt73usb
rt2x00usb              11548  1 rt73usb
rt2x00lib              29756  2 rt73usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
parport                35340  2 ppdev,lp
mac80211              181236  2 rt2x00usb,rt2x00lib
cfg80211               93052  2 rt2x00lib,mac80211
exportfs                4412  2 nfsd,xfs
agpgart                34988  2 nvidia,amd64_agp
```

---

### Post by ericcart on 2010-09-24
It's annoying to be losing the mouse, and having to restart several times every day.

I've disabled ACPI from bios, and now It works flawless.

Thanks,
Eric

---

