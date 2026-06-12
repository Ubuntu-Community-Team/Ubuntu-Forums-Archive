---
title: "Jaunty fails to wake up from hibernate"
date: 2009-04-26
forum: Hardware
---

### Post by CornedBee on 2009-04-26
Hi,

I have a Lenovo 3000 N100 laptop. Until a few days ago, it ran Kubuntu 8.10, with no problems at all. Suspend-to-RAM and Suspend-to-disk both worked perfectly.

Now I've upgraded to 9.04, and while S-t-RAM still works, S-t-disk fails to wake up. It shows the splash screen ("Waking up, please wait"), then it shows a very weird messed-up screen for a few moments (mostly black, with a multi-colored blotch repeated every 50 pixels in both directions), and then it powers off. When I power it on  again, it does a clean boot. I couldn't find anyone with similar symptoms via Google.

The problem is, while I have enough experience to track down most problems that occur during normal running of the system, stuff that happens during the suspend cycle has me completely stumped. I don't know where to begin. So any guides to help me narrow down the problem (and perhaps even solve it) would be highly appreciated.

uname -a: Linux tuxtop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
05:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
05:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

lsmod:
```
aes_i586               15744  1                                                                                        
aes_generic            35880  1 aes_i586                                                                               
ppdev                  15620  0                                                                                        
bridge                 56340  0                                                                                        
stp                    10500  1 bridge                                                                                 
bnep                   20224  2                                                                                        
input_polldev          11912  0                                                                                        
joydev                 18368  0                                                                                        
sbp2                   30476  0                                                                                        
lp                     17156  0                                                                                        
parport                42220  2 ppdev,lp                                                                               
snd_hda_intel         435636  2                                                                                        
snd_pcm_oss            46336  0                                                                                        
snd_mixer_oss          22656  1 snd_pcm_oss                                                                            
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss                                                              
arc4                    9856  2                                                                                        
snd_seq_dummy          10756  0                                                                                        
ecb                    10752  2                                                                                        
snd_seq_oss            37760  0                                                                                        
snd_seq_midi           14336  0                                                                                        
snd_rawmidi            29696  1 snd_seq_midi                                                                           
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi                                                               
iwl3945                97912  0                                                                                        
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event                              
mac80211              217208  1 iwl3945
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 44748  0
iTCO_wdt               19108  0
iTCO_vendor_support    11652  1 iTCO_wdt
led_class              12036  1 iwl3945
psmouse                61972  0
snd                    62628  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
intel_agp              34108  0
nvidia               7233756  39
pcspkr                 10496  0
serio_raw              13316  0
yenta_socket           32396  1
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
ricoh_mmc              11904  0
sdhci_pci              15232  0
sdhci                  23940  1 sdhci_pci
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
cfg80211               38032  2 iwl3945,mac80211
video                  25360  5
btusb                  19608  2
agpgart                42696  2 intel_agp,nvidia
output                 11008  1 video
ohci1394               38576  0
ieee1394               94660  2 sbp2,ohci1394
8139too                32128  0
8139cp                 27776  0
mii                    13312  2 8139too,8139cp
fbcon                  46112  0
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```

---

### Post by CornedBee on 2009-04-26
Heh, found the problem. I configured the power manager to suspend to disk on pressing the power button, and used that.

Apparently, this doesn't prevent some lower-level component from **also** reacting to the power button - this one by shutting down.

So it woke up properly, then shut down hard in response to the power button press I used to put it to sleep.

---

### Post by ricnar456 on 2009-05-05
When I put my kubuntu jaunty on hibernation and wake up, pressing the power button, the system start and display "waking up",next a error message of the monitor appear, "the monitor is working in a unsupported frequency" and is needed press the power button again, and the system restart in a normal boot.

ricnar

---

