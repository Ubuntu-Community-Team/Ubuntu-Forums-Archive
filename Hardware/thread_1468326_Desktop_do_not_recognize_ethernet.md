---
title: "Desktop do not recognize ethernet"
date: 2010-05-01
forum: Hardware
---

### Post by tosslove on 2010-05-01
Hi, i am pretty new in this because im a new user in ubuntu.

I have 2 Network Cards in my deskto, one is in a PCI port (that works fine) the other is that one what came with the mainboard and it is not recognized by Ubuntu.

I did a command lspci and gave to me this info:

00:00.0 Host bridge [0600]: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge [1106:0314]
00:00.1 Host bridge [0600]: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge [1106:1314]
00:00.2 Host bridge [0600]: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge [1106:2314]
00:00.3 Host bridge [0600]: VIA Technologies, Inc. PT890 Host Bridge [1106:3208]
00:00.4 Host bridge [0600]: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge [1106:4314]
00:00.7 Host bridge [0600]: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge [1106:7314]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237/VX700 PCI Bridge [1106:b198]
00:09.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
00:0f.0 IDE interface [0101]: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller [1106:3149] (rev 80)
00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] [1106:3227]
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV44A [GeForce 6200] [10de:0221] (rev a1)

I do not know how to read that info, but i guess it is only taken 1 network card, in windows XP both was working fine.

The Network card with the problem is [B]VIA Rhine II Fast Ethernet.

thanks a lot.
[/B]

---

### Post by P4man on 2010-05-01
I also have a Via Rhine II onboard nic and it works fine. Except, it stops working after a resume from standby, but that can be worked around. Ill post that later if we get there and you suffer the same issue.

here is what i get in lspci:
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)

Can you verify in your bios the onboard nic is enabled, and not set to auto or disabled?

---

### Post by tosslove on 2010-05-01
Yes i already did and i got PCI enabled for both. There is no more options in BIOS about it.

Let me explain better the situation for you.

The NIC in Mother Board is a Via Rhine II, it works fine with Karmic Koala.

Now, i installed a second Network Card, but when i restarted, only the new appears.

In a moment i had both cards working, but when i reboot Via Rhine always dissapear.

So im working atm whit the PCI (recently installed) and looking how to force the Via Rhine II to be recognized.

Thanks.

---

### Post by P4man on 2010-05-02
can you try this in a terminal:

```
lsmod
```

does it show the via_rhine driver?

If not, try

```
sudo modprobe via_rhine
```

If it does, try unloading it first, then reloading it:

```

sudo rmmod via_rhine
sudo modprobe via_rhine
```

Either way, I would file a bug report.

---

