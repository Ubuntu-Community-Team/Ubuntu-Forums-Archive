---
title: "Where's my modem?"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by schmildo on 2008-03-07
I have a Toshiba Satellite Pro P200 PSPB7A-02300W laptop.

It is alledged to have a modem inbuilt, I can see the port on the right hand side of the devcie.

I'd like to attempt to use it in linux, but i'm having problems finding out what /dev/ttySx port it is on?

I've checked out this website here: [http://linux.toshiba-dme.co.jp/linux/eng/reference.htm](http://linux.toshiba-dme.co.jp/linux/eng/reference.htm)
Which indicates that toshiba laptops have three types of internal modems;

hardware
software (DSP-type)
software (sound chip type)

I know software modems can be a pain in the butt, but this site indicates that if it was a DSP type modem that I could get it working.

```

ubuntu@ubuntu:/etc/minicom$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Unknown device [1002:9581]
01:00.1 Audio device [0403]: ATI Technologies Inc Unknown device [1002:aa08]
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection [8086:4229] (rev 61)
06:00.0 Multimedia controller [0480]: Broadcom Corporation Unknown device [14e4:1612] (rev 01)
0c:04.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
0c:04.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
0c:04.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
0c:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]


```

But i'm not sure which one of these is my modem... I know that broadcom make modem thingys, but they do other things also....

If I had a sound-chip type of software modem I presume it'd appear as an unkown audio device which i have here also. I know that sound in my laptop works fine in linux.

I want to identify all the unkown devices listed here, but I wanted to start with the modem first.

pppconfig fails to find a modem, and i've tried using minicom to communicate with ttyS0,1,2, & 3. I've even tried:

echo atdt 1234567890 > /dev/ttyS0

with the phone line plugged in to no avail.

I've had alot of trouble finding any linux info on this particualr laptop, i suppose because it is quite new.

Someone said that you can see your modem initialise on boot-up, but i've not seen it, and the syslog doesnt seem to contain anything useful.

Does anyone know anything about modems on these laptops or are you aware of something that might help?

---

