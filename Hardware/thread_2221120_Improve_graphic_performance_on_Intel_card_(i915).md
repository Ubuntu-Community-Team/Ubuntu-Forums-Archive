---
title: "Improve graphic performance on Intel card (i915)"
date: 2014-04-30
forum: Hardware
---

### Post by komarx6 on 2014-04-30
Hello everyone!
My graphic card does not run as good as it could on linux. I'm using ubuntu 12.04 LTS, and I just realized that my graphic card runs munch better on Windows 7 with all visual effects and things like that. OpenArena looks way better, has right resolution and runs much smoother that on Ubuntu. Google Earth also runs on Windows, while on Ubuntu it gives me this error message:
> Unsupported Graphics Card Your graphics card does nor meet the minimum spec required to run Google  Earth,which is a 3D accelerated card with shader support.It is strongly  recommended that you try running Google Earth on a different machine or  in a different rendering mode or upgrade to a newer graphics card.You  may continue,but the application is unlikely to work.
And than it closes.

This is output of lshw -C display:
```
  *-display:0             
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:fd780000-fd7fffff ioport:cc00(size=8) memory:d0000000-dfffffff memory:fd740000-fd77ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:fd680000-fd6fffff


```

This is from lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: LSI Corporation ET-131x PCI-E Ethernet Controller (rev 03)
03:05.0 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
03:05.1 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
03:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
03:05.3 Bridge: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
03:05.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)


```

This is from lsmod:
```
pci_stub               12550  1 
vboxpci                22911  0 
vboxnetadp             13328  0 
vboxnetflt             27240  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158447  10 rfcomm,bnep
binfmt_misc            17292  1 
arc4                   12473  2 
joydev                 17393  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   174313  1 
ppdev                  12849  0 
rt73usb                27029  0 
rt2x00usb              20099  1 rt73usb
rt2x00lib              48923  2 rt73usb,rt2x00usb
mac80211              436493  2 rt2x00usb,rt2x00lib
cfg80211              178877  2 rt2x00lib,mac80211
pcmcia                 39826  0 
snd_hda_intel          32719  3 
snd_hda_codec         109562  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd_seq_midi           13132  0 
psmouse                86546  0 
serio_raw              13027  0 
snd_rawmidi            25424  1 snd_seq_midi
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq_midi_event     14475  1 snd_seq_midi
parport_pc             32114  1 
i915                  428317  3 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
et131x                 40590  0 
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  16 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
video                  19115  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
firewire_ohci          40172  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  2 rt73usb,firewire_core


```

What can I do to improve my graphic performance?
Any help would be much appretiated. Thank you.

---

### Post by dannyboy79 on 2014-05-01
i would suggest activating this ppa, it provides more up to date (better) intel graphics drivers. [https://launchpad.net/~pali/+archive/graphics-drivers/](https://launchpad.net/~pali/+archive/graphics-drivers/)

---

