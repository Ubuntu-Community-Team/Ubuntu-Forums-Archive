---
title: "Acer TravelMate 4072LCi - No Sound or Wireless"
date: 2006-09-05
forum: Hardware &amp; Laptops
---

### Post by Johenius on 2006-09-05
Hi.

I've just got a new Acer TravelMate 4072LCi, and my wireless and sound don't seem to be working. 
Googling for Acer TravelMate 4072LCi's in general seems to show me that they're only supplied here in South Africa, so it's believable that no documentation for Ubuntu problems has cropped up yet:

Here's my problem:
The laptop came with Windows XP installed, with working wireless and sound. Shortly after buying it, I installed Dapper for work purposes. Since then I've struggled with all the guides and advice I could lay my hands on to get sound and wireless working. 

Wireless: I've tried ipw2200 and ieee80211 drivers. I've tried ndiswrapper.  I've got NetworkManager applet up and running. I've tried another PCMCIA wireless card. I've installed and tried to get acerhk working - dmesg responds to events, as does xev, but I can't seem to get anything else to respond.

Sound: I've tried getting the bleeding edge ALSA drivers. I've tried switching my main audio from OSS to ALSA and back. I've tried unmuting with alsamixer.

Both: I've tried upgrading to the latest version of the linux kernel, compiling from source (former Gentoo kiddie :) ).

Present state of everything:
Wireless: Network Manager works and acknowledges the existence of my wireless card, it just doesn't see any wireless networks.

```

johenius@yggdrasil:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:4E:51:F8
          inet addr:146.231.10.136  Bcast:146.231.10.143  Mask:255.255.255.240
          inet6 addr: fe80::216:36ff:fe4e:51f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8082 errors:71 dropped:94 overruns:71 frame:0
          TX packets:5010 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7253586 (6.9 MiB)  TX bytes:761735 (743.8 KiB)
          Interrupt:177 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:16:6F:27:99:B7
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 Memory:b0101000-b0101fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)
```

Sound: Alsa runs fine. Alsamixer runs fine. I've modprobe'd what I'm told is the correct driver (snd_hda_intel). It's just that... no sound comes out. Volumes set to max and unmuted, rhythmbox clearly playing SOMETHING, just not audible.
```

johenius@yggdrasil:~$ lsmod | grep snd
snd_hda_intel          20468  1
snd_hda_codec         163088  1 snd_hda_intel
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
snd                    60004  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_hda_intel,snd_pcm
```

General:
```
johenius@yggdrasil:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
0000:00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:06:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
0000:06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
0000:06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

In terms of relevant hardware spec, here's what the (TravelMate 4070/4080 Series) manual for my laptop gives it as:

Wireless:
Intel PRO/Wireless 2200BG network connection
(dual-mode 802.11b/g) Wi-Fi CERTIFIED(tm) solution, supporting Acer SignalUp(tm) wireless technology

Audio:
Intel High-Definition audio support
Sound Blaster Pro and MS Sound compatible
S/PDIF2 (Sony/Philips Digital Interface) support for digital speakers

I'd post my dmesg also, but I don't want to waste space :) At least, this early in the diagnosis phase.

Anyone have a clue?

---

### Post by fak3r on 2007-10-11
For my sound issue on my Vostro 1500 I found this fix in the forums.  Add:

options snd-hda-intel model=5stack

to /etc/modprobe.d/alsa-base and reboot.  HTH

---

