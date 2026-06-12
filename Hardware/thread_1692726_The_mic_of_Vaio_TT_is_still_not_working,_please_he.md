---
title: "The mic of Vaio TT is still not working, please help"
date: 2011-02-21
forum: Hardware
---

### Post by ilcontegis on 2011-02-21
Guys 2 years ago I started a thread in this forum with the aim to support people having my same laptop: a vaio tt.
After 2 years everything works on my vaio tt except the internal microphone.
I am begging you....is there someone who succeeded to make it work? 

```
teo@teo-vaio:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation WiFi Link 5100
0b:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
0b:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
0b:04.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
0b:04.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)

```

```
teo@teo-vaio:~$ aplay -l
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: Intel [HDA Intel], dispositivo 0: ALC889 Analog [ALC889 Analog]
  Sottoperiferiche: 0/1
  Sottoperiferica #0: subdevice #0
scheda 0: Intel [HDA Intel], dispositivo 3: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0

```

```
teo@teo-vaio:~$ cat /proc/asound/card*/codec* | grep -i codec
Codec: Realtek ALC889
Codec: Intel Cantiga HDMI

```

Now I use alsa 1.0.23 and I updated to the latest kernel 2.6.38-4 (hoping in some improvement....


I hope you can help me.
Thank you

---

### Post by ilcontegis on 2011-02-27
I guess after 3 year nobody still has the microphone working...
I will say UP once just hoping in some answer...

---

### Post by ilcontegis on 2011-07-07
Anyone?

---

