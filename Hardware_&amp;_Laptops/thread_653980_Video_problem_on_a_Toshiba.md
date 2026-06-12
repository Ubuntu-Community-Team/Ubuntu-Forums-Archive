---
title: "Video problem on a Toshiba"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by Kip_Cathey on 2007-12-30
I have a toshiba satellite A75 with what looks like a video problem.  It refuses to come out of suspend, the screensaver NEVER works, just displays a black screen, and the display flickers quite a bit.  I picked it up used, and none of my comp tools work on Ubuntu, so I'll tell you the specs I know. 

P4 3.06 mobile
Intel Chipset (I think)
ATI video, sorry, I don't know what version, would be helpful if I did...
1.5 gigs of ram, all stable

The first distro I tried on this laptop was Ubuntu... 6.06.  Yea.  Never had this video issue with it, but it hated my wireless so I moved up.

Also, if anyone knows why my nic isn't working, that would be awesome.

And if any of you know any tools like CPU-Z that will work so I can tell you what this laptop really has in it, that would be beyond appreciated.

Lastly, if this is in the wrong section, please let me know... this is the best I could find.

New to linux,
Kip

---

### Post by Yellow Pasque on 2007-12-30
please run lspci and post the output.

---

### Post by Kip_Cathey on 2007-12-30
Awesomeness!  I learned something!

I assumed you meant in a terminal, heres what I got:
00:00.0 Host bridge: ATI Technologies Inc RS300 Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 18)
00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)

---

### Post by stealth1236 on 2008-01-09
Bump!!!!

---

