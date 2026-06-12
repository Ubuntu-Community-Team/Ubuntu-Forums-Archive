---
title: "Lost sound on Toshiba A75"
date: 2008-05-04
forum: Hardware
---

### Post by Kip_Cathey on 2008-05-04
I lost all ability to hear anything on my Toshiba.  This actually happens in Windows as well, but I know thats because windows is a dork who expects me to put the blown as all heck speakers in my laptop again.

But I digress.  The ac'97 codec setup is all recognised by the laptop and Ubuntu... so I'm not to sure why I cannot hear anything.  lspci shows:

kip@Toby:~$ lspci
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

Not that it's much help to me.

This problem started recently.  I cannot even get a test beep, and when I try, I get this message:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

Is there something I can do to maybe patch this?  It worked fine when I first installed, it just randomly quit after I shut down one night.

---

