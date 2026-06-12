---
title: "Can't get wireless to work on Hp laptop"
date: 2008-07-26
forum: Hardware
---

### Post by Mediciman on 2008-07-26
Hi,
I just put Ubuntu (8.04) on my Hp Ze2000 laptop.

I can't seem to turn the wireless on and when I try and download Broadcom
B43 wireless driver from Hardware drivers but, It keeps telling me to restart my computer Which, I have already done when it first asked me.

It's a Hp Ze2000.
Thanks, Just tell me if you need any more information.

---

### Post by Mediciman on 2008-07-27
Come On I really need some help. Please.

---

### Post by Mediciman on 2008-07-28
Come on people...I really need some help...Please?!?!

---

### Post by stchman on 2008-07-28
You need to install the ndiswrapper to use the Windows drivers for that card.

---

### Post by Mediciman on 2008-07-29
> **stchman said:**
> You need to install the ndiswrapper to use the Windows drivers for that card.

I did but, I didn't really understand how to do anything with.

This site says finding a .inf (Or something file) But, I don't know where to find it.

---

### Post by Kevbert on 2008-07-29
If you run
```
lspci 
```
in terminal what model and revision is your Broadcom wireless ?  In most cases you can download the firmware files straight to the /lib/firmware directory.  See [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13").

---

### Post by Mediciman on 2008-07-29
> **Kevbert said:**
> If you run
```
lspci 
```
in terminal what model and revision is your Broadcom wireless ?  In most cases you can download the firmware files straight to the /lib/firmware directory.  See [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13").

Okay I did the lspci thing and it showed this..

```
 00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller

```

---

### Post by Kevbert on 2008-07-29
OK. The hyperlink in my previous post should work.  You need to download the attached drivers in the post and put them in the firmware folder and then reboot the PC.  The linked post has all the information you need.

---

