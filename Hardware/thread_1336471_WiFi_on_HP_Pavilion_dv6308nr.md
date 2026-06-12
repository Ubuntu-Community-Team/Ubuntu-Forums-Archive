---
title: "WiFi on HP Pavilion dv6308nr"
date: 2009-11-24
forum: Hardware
---

### Post by ADyingSoul on 2009-11-24
My WiFi used to work just fine, and then I upgraded Ubuntu to the new distro and after a few days of having that it stopped working. Then one day it randomly worked again... and then stopped. And now it doesn't work at all. Any help would be GREATLY appreciated. I kind of NEED my wireless as having to be tied down by an Ethernet cable is really inconvenient.

---

### Post by pi4r0n on 2009-11-24
OK so lets start with some basics OK

1. Wifi card model :confused:
2. Drivers info :confused:
3. Wifi setup informations :confused: (Security, Chanel etc...)

After that I think we can start helping you.

Sorry mate for being pain in the *** but we are not magicians and don't know what hardware you got there :(

Ta

pi4r0n

---

### Post by ADyingSoul on 2009-11-24
It's alright. I understand completely. I'm a bit of a noob, though. How do I find that stuff out?

---

### Post by pi4r0n on 2009-11-24
> **ADyingSoul said:**
> How do I find that stuff out?

Man don't tell me you don't know you WIFI/hardware model **LOL**

For build in one

> lspci -nn

For USB onc

> lsusb

also let me know what PC or laptop do you have.

---

### Post by ADyingSoul on 2009-11-24
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce Go 6150] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
07:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
07:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 0a)
07:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 05)
07:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)

That's what "lspci -nn" returned.

My computer? It's a HP Pavilion dv6308nr Notebook PC.

---

### Post by pi4r0n on 2009-11-24
Really strange its only recognizing you Ethernet card and not WIFI ?

> **ADyingSoul said:**
> 
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)

Can you try this 

> lsmod

and that

> ifconfig

and tell me what WIFI card mode do you have.

---

### Post by ADyingSoul on 2009-11-24
From: lsmod 			 		

Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_atiixp_modem       11940  0 
snd_via82xx_modem      11204  0 
snd_intel8x0m          13896  0 
snd_ac97_codec        101216  3 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m
ac97_bus                1532  1 snd_ac97_codec
snd_hda_codec_conexant    20060  1 
snd_hda_intel          26920  3 
snd_hda_codec          75708  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  1 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  7 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
sdhci_pci               7100  0 
snd_timer              22276  2 snd_pcm,snd_seq
sdhci                  17472  1 sdhci_pci
k8temp                  4188  0 
joydev                 10272  0 
led_class               4096  1 sdhci
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               9586440  39 
agpgart                34988  1 nvidia
iptable_filter          3100  0 
ricoh_mmc               3676  0 
snd                    59204  21 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  2 snd
snd_page_alloc          9156  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_hda_intel,snd_pcm
psmouse                56500  0 
serio_raw               5280  0 
i2c_nforce2             6784  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
usbhid                 38208  0 
ohci1394               29900  0 
forcedeth              54152  0 
ieee1394               86596  1 ohci1394
video                  19380  0 
output                  2780  1 video

From:  			 				ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1e:68:12:04:e8  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe12:4e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6797 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6685 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2697785 (2.6 MB)  TX bytes:1060387 (1.0 MB)
          Interrupt:20 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:928 (928.0 B)  TX bytes:928 (928.0 B)

I have a Broadcom built-in wireless card.

---

