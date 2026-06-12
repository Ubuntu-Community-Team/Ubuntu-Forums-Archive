---
title: "intermittent sound on toshiba satellite a70, gutsy (7.10)"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by alex008 on 2007-12-08
Hi,

I started having weird problems with my sound after upgrading to ubuntu 7.10
* When playing videos in totem player, the video would sometimes freeze and the cpu utilization would jump to 100% until i kill totem. The same happens when I play flash videos in firefox.
* If i start playing realplayer, the sound works fine until I switch applications, then the sound disappears and player starts reloading buffer frequently complaining about congestion

does anyone know what's going on and how to fix it? everything seemed to work fine on 6.06.

My system:
-----------------------------------------
Ubuntu 7.10 
toshiba satellite A70-S256

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


$ lspci
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
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller
02:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
02:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller
02:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc:

---

### Post by Speckay on 2008-01-29
*bump*

Mine does the same thing and I have the same system setup. I haven't tried with 6.06 though...

---

### Post by pecenac on 2008-06-15
get rid of the alsa and install oss4. It works perfect. See here: [http://ge.ubuntuforums.com/showthread.php?t=780961]("http://ge.ubuntuforums.com/showthread.php?t=780961")

---

