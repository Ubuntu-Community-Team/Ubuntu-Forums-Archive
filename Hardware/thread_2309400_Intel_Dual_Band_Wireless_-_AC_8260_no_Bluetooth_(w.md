---
title: "Intel Dual Band Wireless - AC 8260: no Bluetooth (wifi works)"
date: 2016-01-10
forum: Hardware
---

### Post by chrishelma on 2016-01-10
Hello dear forum-members!

I run the latest ubuntu 15.10 on my Dell Precision workstation.

```
uname -a
Linux  4.2.0-23-generic #28-Ubuntu SMP Sun Dec 27 17:47:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux 
```

 I'd like to get the built-in Bluetooth (intel 8260 Bt + Wifi) working, but it doesn't even recognize the bluetooth module.

```
rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no 
```

"hciconfig" doesn't produce any output.

```
lspci -nn | grep -i net 
00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-LM [8086:15b7] (rev 31)
03:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a) 
```

According to this thread [http://ubuntuforums.org/showthread.php?t=2298368](http://ubuntuforums.org/showthread.php?t=2298368) the wifi-bt-card should work with ubuntu 15.10
So what's wrong with my configuration?

I appreciate any help.
Thank you in advance!
Chrissie

**EDIT: It was the PCIexpress to M.2 adapter card which caused the problem, not the wifi-card or ubuntu.**

---

### Post by weatherman2 on 2016-01-10
On my Intel 7260, I can't use WiFi and bluetooth at the same time by default. ("rfkill list" shows no bluetooth device in that state.)  Instead, I have to cycle through different wireless modes using the Fn + F2 key.  (Depending on your configuration, maybe just F2).  Each time I press it, the mode changes from say Wifi to (disabled) to Bluetooth Only to (disabled) to WiFi + Bluetooth.  I think, at least with my card, I can't do 2x2 WiFI (dual channel) and bluetooth at the same time, so when I'm using bluetooth I'm using WiFi at half speed, though I haven't tested this to confirm.  I'm not sure why else bluetooth would not be enabled automatically.

Anyway, try pressing Fn+F2 once and see what happens (or maybe not F2 - but it is on my Dell laptop to toggle the wireless mode).

---

### Post by chrishelma on 2016-01-10
Thank you very much! 
Unfortunately the F2-solution doesn't work for me. Is there another option to switch between wifi and bluetooth, perhaps via the terminal? I don't care about wifi as the computer is stationary.

---

### Post by jeremy31 on 2016-01-10
Post the result of ```
lsusb; dmesg | egrep -i 'blue|firm'
```

---

### Post by chrishelma on 2016-01-11
Thank you for the reply, here's the requested output:

```
lsusb; dmesg | egrep -i 'blue|firm'
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 05ac:0250 Apple, Inc. Aluminium Keyboard (ISO)
Bus 001 Device 004: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 001 Device 003: ID 13fd:2040 Initio Corporation 
Bus 001 Device 002: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.136723] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.703625] GHES: APEI firmware first mode is enabled by APEI bit.
[    2.460536] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-8000C-15.ucode failed with error -2
[    2.460816] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-8000C-14.ucode failed with error -2
[    2.470134] iwlwifi 0000:03:00.0: loaded firmware version 25.30.13.0 op_mode iwlmvm

```

It seems there's really something wrong with the driver. How can I fix this?

---

### Post by jeremy31 on 2016-01-11
The kernel isn't detecting any bluetooth of any kind as it should appear in lsusb results.  I have a Toshiba that was like that with some wifi+bt cards, the bluetooth wasn't detected in Linux or in Windows

---

### Post by chrishelma on 2016-01-11
> **jeremy31 said:**
> The kernel isn't detecting any bluetooth of any kind 
Oh no. This sounds bad.

Is the any possibility to somehow advise the kernel to detect the bluetooth? 
As I have the newest firmware installed, what's the reason for not detecting bluetooth?
([https://launchpad.net/ubuntu/wily/+source/linux-firmware/+changelog](https://launchpad.net/ubuntu/wily/+source/linux-firmware/+changelog))

Or is this a general problem e.g. of hardware compatibility?

---

### Post by chrishelma on 2016-01-11
I made a fresh install of 15.10.
At least I get some "Bluetooth messages" with dmesg:

```
[  125.555194] Bluetooth: Core ver 2.20
[  125.555221] Bluetooth: HCI device and connection manager initialized
[  125.555359] Bluetooth: HCI socket layer initialized
[  125.555364] Bluetooth: L2CAP socket layer initialized
[  125.555373] Bluetooth: SCO socket layer initialized

```

The rest remained the same as above described.

---

### Post by weatherman2 on 2016-01-11
> **chrishelma said:**
> Thank you very much! 
Unfortunately the F2-solution doesn't work for me. Is there another option to switch between wifi and bluetooth, perhaps via the terminal? I don't care about wifi as the computer is stationary.

What happens when you hit this key just once?  Is it indeed disabling your WiFi the first time then re-enabling it upon another press?  If that isn't the right key, try to find the correct one.

I do suspect your wireless card, like mine, may need to be toggled into the right mode.  I don't know how to do that with a terminal command.

---

### Post by chrishelma on 2016-01-11
> **weatherman2 said:**
> What happens when you hit this key just once?

None of the F-Keys has any influence on the wifi. With and without fn.   :(
I guess this is a laptop-specific feature.

> I do suspect your wireless card, like mine, may need to be toggled into the right mode.
That's also my suspection.

---

### Post by jeremy31 on 2016-01-11
Can you remove a panel on the computer to look at the wireless card?  I am not sure all 8260 wireless cards have bluetooth also but if you can look at the card, it should have WFM and BDM on the sticker followed by the MAC address for the wifi and bluetooth, if it only has WFM, there is no bluetooth

Can you check the BIOS to see if bluetooth might be disabled?

---

### Post by chrishelma on 2016-01-11
[ATTACH=CONFIG]266667[/ATTACH]

This is a photo of the card. I hope it helps.

edit: In the BIOS there's just the option "media card enabled". It is enabled.
edit: after this closer look I can specify: it's the model 8260 NGW   M.2-card
[http://www.intel.com/content/dam/www/public/us/en/documents/product-briefs/dual-band-wireless-ac-8260-brief.pdf](http://www.intel.com/content/dam/www/public/us/en/documents/product-briefs/dual-band-wireless-ac-8260-brief.pdf)

---

### Post by jeremy31 on 2016-01-11
Did the bluetooth work previously?  Possibly in windows?

---

### Post by chrishelma on 2016-01-11
No. It's a new machine, delivered with a special ubuntu 14.04 LTS. I had the same results there and "system error detected"-messages with every boot. The dell service left me with the link in the first post ;)

---

### Post by weatherman2 on 2016-01-11
> **chrishelma said:**
> None of the F-Keys has any influence on the wifi. With and without fn.   :(
I guess this is a laptop-specific feature.

Could be.  I would inquire with Dell about this, then.  There may be a service manual on their website that describes how to enable/disable the wireless card through a hardware switch, not software.

---

### Post by chrishelma on 2016-01-11
That's the manual:
[https://premiumstation.pl/files/Dell-Precision-3420-SFF-Podrecznik-EN.pdf](https://premiumstation.pl/files/Dell-Precision-3420-SFF-Podrecznik-EN.pdf)
The card is mounted on a PCI-Card, sticking in the PCI Express x4 slot (2. on p.24), outside there's the optiplex antenna


EDIT: Can it be? Is the card just in the wrong slot? At the PCI Express x16 slot (1.) 3rd Gen is mentioned. So, where it sticks it cannot be read? Perhaps?

---

### Post by weatherman2 on 2016-01-11
Oh bad news: I stumbled upon this:

[http://www.ubuntu.com/certification/hardware/201507-18620/](http://www.ubuntu.com/certification/hardware/201507-18620/)

> 
Certification notes
Bluetooth is not supported
Although the wireless card for this system is a WiFi/BT combo card, BT hasn't been enabled and it is not available on this platform.


So you might need to go with a USB bluetooth card.

---

### Post by chrishelma on 2016-01-12
> **weatherman2 said:**
> So you might need to go with a USB bluetooth card.
But why should they sell this card with pre-installed ubuntu then?
If you buy a car with pre-installed Hifi you can expect that the radio works, isn't it?


EDIT:
weatherman2 is right:
> **weatherman2 said:**
> BT hasn't been enabled and it is not available on this platform.
It's the pci-express to M.2 adapter card which doesn't support bluetooth.

---

### Post by weatherman2 on 2016-01-12
The card itself probably does support bluetooth.  It's the motherboard that doesn't support it.  Intel may not sell wireless cards anymore that don't include bluetooth, but supporting bluetooth may require additional hardware support.  I think there is a channel to USB devices from the PCI-e slot, and it may not exist in every motherboard.

---

### Post by chrishelma on 2016-01-12
> **weatherman2 said:**
> The card itself probably does support bluetooth.  It's the motherboard that doesn't support it. ...  I think there is a channel to USB devices from the PCI-e slot, and it may not exist in every motherboard.
Yes. It was definitely neither the card nor the driver. Now the technicians told me it's the "bridge" on which the card is installed to fit in the PCIe-slot. 
So I need another bluetooth-solution...

Thank you both weatherman2 and jeremy31 for your advice!!!!
:D

I just wonder why this workstation doesn't have this problem with windows...
EDIT: Got a refund, so it turned out OK.

---

### Post by omid7 on 2016-02-05
did you refund the whole machine or just the bluetooth + wifi. I have a similar problem .

---

### Post by chrishelma on 2016-02-06
> **omid7 said:**
> did you refund the whole machine or just the bluetooth + wifi. I have a similar problem .
I had the the choice to send the machine back and get a whole refund,  but I decided to keep it, so I got some money back for the  malfunctioning card.

---

