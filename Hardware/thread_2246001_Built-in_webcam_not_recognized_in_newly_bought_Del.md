---
title: "Built-in webcam not recognized in newly bought Dell Latitude laptop"
date: 2014-09-27
forum: Hardware
---

### Post by MajinSaha on 2014-09-27
Hi all!
Basically, the title says it all. I have bought Latitude E-6440 by Dell recently with preinstalled Ubuntu 12.04 LTS on it. The webcam is not seen by Ubuntu at all. I checked with Dell support website, and I found only one large file with pack of drivers for my model. Webcam was not listed there. I installed it anyways, and nothing changed. Cheese, Kamoso and Skype are not showing anything, no flash lights near camera spot (there should be some, according to the manual that came with laptop ).
I am planning to contact Dell, since there is still active warranty. But do you guys think there is something we can do ourselves to make it work?
I fear the driver for this webcam just hasn't been written yet at all in the world.

Thanks to all who can help!

---

### Post by weatherman2 on 2014-09-27
Start by giving the output of the terminal commands "lsusb" and "lspci" .  The camera should show up on one of them, so at least you can see what kind of camera it is.

You might also look at the tail end of your /var/log/syslog file.

Does Cheese show any webcam Devices at all in Preferences?

---

### Post by Vladlenin5000 on 2014-09-27
The status LED should indicate whether or not the camera is on; there should be a keyboard switch (FN+somekey) for the camera.

---

### Post by MajinSaha on 2014-09-27
Thanks for your reply, guys!

The output for lsusb is
```
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

```
The output for lspci is
```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-LM (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d4)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d4)
00:1c.5 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #6 (rev d4)
00:1c.6 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #7 (rev d4)
00:1c.7 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #8 (rev d4)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM87 Express LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
0e:00.0 SD Host controller: O2 Micro, Inc. Device 8520 (rev 01)

```
The tail of /var/log/syslog corresponding to the last boot (as far as I understood what it means) has more than 200 lines there. Should I still post them?
The problem with Cheese is that Preferences line is inactive ( I can't select it ). The only lines clickable are Quit and two Move to Trash lines.

Vladlenin5000,
sorry I don't know what "status LED" is. 
I googled that there might be a key switch in some cases, but manual says nothing about it. Don't know how to find the combination. All of the F* keys on top of the keyboard do nothing to webcam.

---

### Post by Vladlenin5000 on 2014-09-28
Dell usually implement either a physical switch or the FN+F2 keyboard switch, or both.
Yours has a "wireless switch" that's most certainly switched off thus preventing the device to be listed.
The status LED is near the actual webcam and _if you don't see it the webcam is OFF_.

Please refer to your user's manual before anything else or check here: [ftp://ftp.dell.com/Manuals/all-products/esuprt_laptop/esuprt_latitude_laptop/latitude-e6440-laptop_Setup%20Guide_en-us.pdf](ftp://ftp.dell.com/Manuals/all-products/esuprt_laptop/esuprt_latitude_laptop/latitude-e6440-laptop_Setup%20Guide_en-us.pdf)

---

### Post by Vladlenin5000 on 2014-09-28
Also check whether or not the webcam is enabled at BIOS. Look for "miscellaneous devices".

---

### Post by MajinSaha on 2014-09-28
Uhm, which of the two does a wireless switch belong to, physical or keyboard?
I tried FN+F2 combination, doesn't work.
The manual you gave is precisely the one I have, only in paper copy. As I said, manual says nothing about the switch (as far as I looked).
During the boot, what button should I press to enter BIOS? Start up screen shows nothing except DELL logo.

---

### Post by weatherman2 on 2014-09-28
None of my Dell laptops has ever had a Fn key to enable/disable the webcam - though there are keys to do other things like enable/disable wireless, touchpad, volume, etc.

I didn't see any webcam devices listed in your output.

To enter BIOS Setup, restart the computer and tap the F2 key (maybe two or three times until it "takes" - tap it, don't hold the key down).  The webcam may indeed be disabled there, though I've never seen a Webcam control in a Dell BIOS, either.  But this is a business-class laptop so there may be extra controls for example to protect your privacy.  A webcam that can be disabled in the BIOS is impossible to hack remotely to let someone spy on you.

---

### Post by MajinSaha on 2014-09-28
I just found a physical switch on the side of the laptop. All it does is turn on/off wireless card.

---

### Post by MajinSaha on 2014-09-28
I got into BIOS, thanks. There was indeed System Configuration -> Miscellaneous Devices. But the camera was checked there already (  as the rest of the devices ).
Still nothing works.

---

### Post by Vladlenin5000 on 2014-09-28
> **Vladlenin5000 said:**
> Also check whether or not the webcam is enabled at BIOS. Look for "miscellaneous devices". The feature in mentioned in the manual. The factory default is enabled.

It may appear as enabled or grayed out -> disconnected and/or faulty
If disabled then enable it and hopefully it'll be installed automatically (generic USB2.0 webcam) and available.

---

### Post by MajinSaha on 2014-09-28
> The feature in mentioned in the manual. The factory default is enabled.

I checked that 6 page pdf, I didn't find any mention of that feature. Do you mean going to Dell.com/support and search there? 
> It may appear as enabled or grayed out -> disconnected and/or faulty
If disabled then enable it and hopefully it'll be installed automatically (generic USB2.0 webcam) and available. 
The option choosing camera was already checked in the "Miscellaneous Devices" in BIOS. I rechecked it again and pressed "Apply", but that didn't make my camera work.

---

### Post by MajinSaha on 2014-09-30
Bump, please.
Is it something not solvable?

---

### Post by Vladlenin5000 on 2014-09-30
You need to contact Dell customer support. You can and should check online beforehand, using your "service tag",  the warranty details so you know what to expect.

EDIT: The probabilities are almost 100% hardware issue with perhaps less than 0,01% of probabilities for a rare situation where a device is disabled by software in Windows and then, when dual-booting and irrespective of BIOS settings, such device just don't show up. There are a few reports of internal WiFi cards acting up like that, never heard of webcams but it's possible, a 0,01% chance is still possible. 
Life anywhere in the universe is much more improbable and yet here we are.

---

### Post by Lexdysia on 2014-10-10
Not sure if this is the same problem, but I have had an old HP mini (110-1081) experience the same symptoms with a fresh install of default 14.04. 
lsusb & lspci didn't bring up anything that I recognised as camera related. 
Both Skype & Cheese didn't recognise any camera hardware.

I installed guvcview (& all the dependencies that came with it) and all now works correctly. (Mind you, I still don't recognise anything in lsusb or lspci that looks like a camera).

---

### Post by gordintoronto on 2014-10-10
It's generally a bad idea to use an older OS than your hardware. Have you tried 14.04.1?

---

