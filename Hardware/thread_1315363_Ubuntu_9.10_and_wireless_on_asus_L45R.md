---
title: "Ubuntu 9.10 and wireless on asus L45R"
date: 2009-11-05
forum: Hardware
---

### Post by pigna on 2009-11-05
Hello everyone, I just insall Ubuntu 9.10 on my Asus laptop L4500RBP.

Everything went fine except the wireless.

The steps I have done are:
1) Install Ubuntu 9.10
2) Download the latest updates
3) Run hardware drivers and installed the drivers for Broadcom wireless card b43legacy

Now the wireless card sees but does not connect properly and not allow me to create new wireless networks.
If I click with right button on the network manager the "Enable wireless network" is in light gray and not selectable.
But if I click with the left button to select a network wireless networks do not appear to me (I had created previously and I have 2 imported).

With the command dmesg I appear the following messages:
```

[ 3335.472536] b43legacy-phy1: Broadcom 4301 WLAN found
[ 3335.496040] b43legacy-phy1 debug: Found PHY: Analog 0, Type 1, Revision 4
[ 3335.496071] b43legacy-phy1 debug: Found Radio: Manuf 0x17F, Version 0x2053, Revision 2
[ 3335.520048] b43legacy-phy1 debug: Radio initialized
[ 3335.608072] b43legacy ssb0:0: firmware: requesting b43legacy/ucode2.fw
[ 3335.653785] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
[ 3335.665766] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
[ 3335.772056] b43legacy-phy1: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[ 3335.829928] b43legacy-phy1 debug: Chip initialized
[ 3335.830234] b43legacy-phy1 debug: 30-bit DMA initialized
[ 3335.830435] b43legacy-phy1 debug: Wireless interface started
[ 3335.830446] b43legacy-phy1 debug: Adding Interface type 2
[ 3335.841253] b43legacy-phy1: Radio hardware status changed to DISABLED
[ 3335.841262] b43legacy-phy1 debug: Radio initialized
[ 3335.841745] b43legacy-phy1 debug: Removing Interface type 2
[ 3335.842050] b43legacy-phy1 debug: Wireless interface stopped
[ 3335.842172] b43legacy-phy1 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[ 3335.842229] b43legacy-phy1 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[ 3335.842283] b43legacy-phy1 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[ 3335.848674] b43legacy-phy1 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[ 3335.859762] b43legacy-phy1 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[ 3335.864047] b43legacy-phy1 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[ 3335.872036] b43legacy-phy1 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[ 3335.880044] b43legacy-phy1 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[ 3335.888029] b43legacy-phy1 debug: Radio initialized
[ 3335.888048] b43legacy-phy1 debug: Radio initialized

```

On the laptop I have not found any button to activate / deactivate the wireless card, and the spy wifii is orange. If I start Windows XP, the card works properly.

Before I installed Ubuntu 9.04 and everything worked perfectly.

This is the output of lspci:

```

02:07.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)

```

This is the output of lshw -C network

```

  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: eth0
       version: 01
       serial: 00:0e:a6:aa:23:d0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.3.150 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:7 memory:fb200000-fb201fff
  *-network:1
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:02:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:5 memory:fb100000-fb101fff
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0e:a6:a8:ba:77
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b

```

And this is list of modules:

```

Module                  Size  Used by
b43legacy             117752  0 
mac80211              181236  1 b43legacy
cfg80211               93052  2 b43legacy,mac80211
b44                    28684  0 
ssb                    35300  2 b43legacy,b44
mii                     5212  1 b44
binfmt_misc             8356  1 
ppdev                   6688  0 
vboxnetadp             78344  0 
vboxnetflt             84840  0 
vboxdrv               121160  1 vboxnetflt
snd_atiixp             15720  2 
snd_atiixp_modem       11940  5 
snd_pcm_oss            37920  0 
snd_ac97_codec        101216  2 snd_atiixp,snd_atiixp_modem
snd_mixer_oss          16028  1 snd_pcm_oss
ac97_bus                1532  1 snd_ac97_codec
snd_seq_dummy           2656  0 
snd_pcm                75296  6 snd_atiixp,snd_atiixp_modem,snd_pcm_oss,snd_ac97_codec
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
arc4                    1660  2 
snd_timer              22276  2 snd_pcm,snd_seq
iptable_filter          3100  0 
pcmcia                 36808  0 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ecb                     2524  2 
ip_tables              11692  1 iptable_filter
snd                    59204  23 snd_atiixp,snd_atiixp_modem,snd_pcm_oss,snd_ac97_codec,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 10272  0 
yenta_socket           24200  1 
x_tables               16544  1 ip_tables
lp                      8964  0 
soundcore               7264  1 snd
rsrc_nonstatic         11644  1 yenta_socket
psmouse                56180  0 
parport                35340  2 ppdev,lp
shpchp                 32272  0 
snd_page_alloc          9156  3 snd_atiixp,snd_atiixp_modem,snd_pcm
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
serio_raw               5280  0 
i2c_piix4               9932  0 
asus_laptop            17400  0 
led_class               4096  2 b43legacy,asus_laptop
usbhid                 38208  0 
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
video                  19380  0 
output                  2780  1 video
ati_agp                 6760  1 
agpgart                34988  3 ttm,drm,ati_agp

```

Thx.

---

### Post by pigna on 2009-11-17
up

---

