---
title: "Support for Intel 82845G/GL graphics"
date: 2014-10-22
forum: Hardware
---

### Post by ola on 2014-10-22
Hello,

I sometimes install Lubuntu 14.04 on old hardware that I then give away to people that can't buy they own computers. So far it's been working ok.

The last week I got an old Fujitsu-laptop that I'm having display problems with. I started by installing Ubuntu. That didn't work so I installed the package lubuntu-desktop. That didn't work either. The max resolution was stuck at 640x480 in both cases. 

I added the startup parameter VGA=792 to my grub config file and the computer now runs in VESA mode.  It works ok now but would it be better to try and get the Intel driver running? Or should I just use VESA? What do you think?

Thanks in advance!

My lspci-output:

```

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
01:03.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
01:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
01:0c.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller

```

---

### Post by mörgæs on 2014-10-22
Vesa is fine, but you could also try to add an xorg.conf.
More info in the link in my signature.

---

### Post by ola on 2014-10-23
Thanks a lot! I tried to use the Intel settings from your guidelines but it worked better with VESA so I'll stick with that.

The guidelines you wrote are really really good! Great work and thanks for your help!

---

### Post by mörgæs on 2014-10-23
You're welcome. 

What is native resolution for the old Fujitsu?

---

### Post by ola on 2014-10-27
Hi again,

I think it's 1024x768 on the Amilo L6820. I searched and that's what I found at least :)

---

### Post by mörgæs on 2014-10-28
If VGA=792 gives a resolution of 1024 * 768, as it is supposed to do, then you have reached the hardware limits. You won't be able to get any higher.

---

