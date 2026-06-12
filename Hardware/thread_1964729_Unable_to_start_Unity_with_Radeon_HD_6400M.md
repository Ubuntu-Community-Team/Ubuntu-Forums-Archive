---
title: "Unable to start Unity with Radeon HD 6400M"
date: 2012-04-24
forum: Hardware
---

### Post by cosborn72 on 2012-04-24
Hopefully it is not too early to ask about Unbuntu 12.04?

I am running Ubuntu on a HP laptop with a Radeon HD 6400M card.  The card has 1gb of memory. The computer as 4gb of memory and an i3 processor.

When I log into unity, it defaults to unity-2d.  I would even had known this, except that MyUnity won't work.  It seems like my ATI card should be able to run the Unity (3d), but I don't know what to do to get it to work.

Here is the information I have.

```
chris@chris-laptop:~$ echo $DESKTOP_SESSION
ubuntu-2d
```

```
chris@chris-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:01.2 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series]
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
05:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
```

According to the additional drivers system setting, I am running the propietary ATI/AMD FGLRX driver.  When I try to install the post-release driver, I get an error.

---

### Post by MonkeyPaw on 2012-04-24
Are you going through "Additional drivers" or straight from AMD.com?

You might try downloading the latest Catalyst 12.3's from AMD and following their install instructions. It's pretty simple. Just make sure any old drivers are removed first.

---

### Post by cosborn72 on 2012-05-01
Thanks Monkey Paw.  I tried downloading the catalyst driver, but had issues complying it.  I will try again and let you know how it works.

---

### Post by bloodymind on 2012-06-22
> **cosborn72 said:**
> Thanks Monkey Paw.  I tried downloading the catalyst driver, but had issues complying it.  I will try again and let you know how it works.
I've got the same problem! How did it go ?

Thank you

---

### Post by TheRoot on 2012-06-24
I have the exact same laptop with the exact problem.

I tried installing the Open Source driver, and the proprietary one but nothing works. 

Installation succeeds but after a reboot I get the BLACK SCREEN..

How did you overcome the problem?

---

