---
title: "Nvidia GF 9400M G driver problem"
date: 2010-08-19
forum: Hardware
---

### Post by kszaq on 2010-08-19
Hi!

I had some problems with drivers for my video card (nVidia GeForce 9400M G) on Ubuntu 10.4. My first attempt of installing the driver was System->Administration->Hardware Drivers - I selected 'NVIDIA accelerated graphics driver (version current)' and clicked Activate. After reboot everything seemed to work fine - system booted properly, desktop effects worked, etc. But that was just a lucky shot, as it showed up during next systems boots - either system loaded properly (as I described), or nothing would display at all, or a prompt would show up, telling me that system was unable to load the driver and letting me restart xserver, use default driver, reboot system, turn of xserver. I guess the cause of this behavior was that I have both nvidia and some default driver activated.
I read a few threads on this forum and found out that adding nvidia line to /etc/modules would tell the system to load the nvidia driver on boot time. I did this and now system loads the proper driver, however, the load screen (purple background, ubuntu sign, several dots used as a progress bar) is displayed in low resolution. So I guess I only partially fixed the problem and a default driver is still somewhere, haunting me ;)

Here's my lspci

```

00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
01:07.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:07.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:07.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:07.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9400M G] (rev b1)
06:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

```and lsmod

```

Module                  Size  Used by
michael_mic             1732  0 
arc4                    1153  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_nvhdmi     3840  1 
snd_hda_codec_idt      51978  1 
snd_hda_intel          21941  2 
snd_hda_codec          74201  3 snd_hda_codec_nvhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
fbcon                  35102  71 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tileblit                2031  1 fbcon
font                    7557  1 fbcon
snd_timer              19098  2 snd_pcm,snd_seq
joydev                  8708  0 
lib80211_crypt_tkip     7596  0 
lp                      7028  0 
bitblit                 4707  1 fbcon
dell_wmi                1793  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               9961216  41 
wl                   1959598  0 
uvcvideo               56990  0 
softcursor              1189  1 bitblit
parport                32635  2 ppdev,lp
dell_laptop             6856  0 
sdhci_pci               5470  0 
videodev               34361  1 uvcvideo
usbhid                 36110  0 
snd                    54148  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hid                    67032  1 usbhid
psmouse                63245  0 
soundcore               6620  1 snd
sdhci                  15462  1 sdhci_pci
vga16fb                11385  1 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
serio_raw               3978  0 
video                  17375  0 
vgastate                8961  1 vga16fb
lib80211                5046  2 lib80211_crypt_tkip,wl
agpgart                31724  1 nvidia
dcdbas                  5422  1 dell_laptop
output                  1871  1 video
i2c_nforce2             5199  0 
v4l1_compat            13251  2 uvcvideo,videodev
shpchp                 28820  0 
led_class               2864  1 sdhci
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
forcedeth              49556  0 
ahci                   32200  2 

```

Any help will be appreciated!

---

