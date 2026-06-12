---
title: "is my sound car broken or something????"
date: 2009-12-02
forum: Hardware
---

### Post by Daltonn0810 on 2009-12-02
well ............... first i installed 9.10 and the audio worked fine , but scince i broke my system and had to reinstall 9.10 there has been no sound , i uninstalled pulseaudio and reinstalled it  , i uninstalled ALSA and installed OSS but my graphics card still wasent coming up so i switched back to ALSA 


i installed alsa via 
```

apt-get install alsa
```

and it successfully installed but when i rn ALSAMIXER I GET
```
alsamixer: function snd_ctl_open failed for default: No such file or directory
```

when i open pulse audio , the hardware tab is empty and its set on dummy out put


when i run lscpi i get no graphics cards
```
dalton@dalton-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

when i type aplay -l i get 
```
aplay: device_list:223: no soundcards found...
```

when i open the GNOME ALSA MIXER its blank




i have no ida what to do , i need audio really bad , its very important to what im doing


my graphics card is 
Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)

---

### Post by PariahVayne on 2009-12-02
x

---

### Post by Daltonn0810 on 2009-12-02
> **PariahVayne said:**
> Ugh, try;

```
sudo aptitude install alsa
```




nope ,  it didn't help

---

### Post by Megafag on 2009-12-02
> **Daltonn0810 said:**
> nope ,  it didn't help

Maybe

```
sudo aptitude remove alsa
```

THEN

```
sudo aptitude install alsa
```

---

### Post by Daltonn0810 on 2009-12-02
> **Megafag said:**
> Maybe

```
sudo aptitude remove alsa
```THEN

```
sudo aptitude install alsa
```





nope , didn't help :icon_frown:


now when i try to run "alsamix" i get

```
 function snd_ctl_open failed for default: No such file or directory
```so i download the alsa drive.tar.gz and ran the snddevices and then when i ran alsamixer i get 

```
alsamixer: function snd_ctl_open failed for default: No such device
```

so i am assuming its a bad alsa configuration or something and not my audio card , we need to come up with a simple audio architecture like windows , at least for the newbs(me)



are there any type of log files i can look at like events or maybe a log for the boot or something??

---

### Post by Daltonn0810 on 2009-12-02
ok no this is ridiculous , i spent two hours uninstalling alsa and reinstalling from source and still no hope



MY SOUND CARD WORKS when i boot 9.04 it makes that system beep from my speakers although pulseaudio cannot control the volume, it seems somehow something is screwing with alsa

---

### Post by edmonds on 2010-01-28
hi
did you  fix this?
i have a similar problem.
tried many many suggestions over last couple of days.
still got the same problem.
pulse works - when i plat a tune Pulse Volume controller recognises it and has a sound graphic bouncing up and down. (but dummy output)
i have an Envy/ice driver installed. (but Envy 24 controller blank)

But i have no sound card?:
aplay -l: aplay: device_list:223: no soundcards found...

---

