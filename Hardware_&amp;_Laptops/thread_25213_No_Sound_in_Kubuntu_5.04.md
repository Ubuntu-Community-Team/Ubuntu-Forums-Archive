---
title: "No Sound in Kubuntu 5.04"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by ralphdewitt on 2005-04-09
Hi all:
I have just done a install of Kubuntu 5.04 final on a Gigabyte GA-7N400 Pro2 
motherboard. I am using the on board soundchip. Info Center lists the 
Sound Driver as 3.8.1a980706 (ALSA v1.0.6 emulation code), 
Kernel is listed as 2.6.10-5-386, Config option: 0, 
Installed drivers: 
Type 10: ALSA emulation, 
Card config: NVidia nForce2 with ALC655 at 0xe0001000, irq22, 
Audio devices: 
0: NVidia nForce2 (DUPLEX) 
Synth and Midi devices are listed as NOT ENABLED IN CONFIG, 
Timers: 
7: system timer,
 Mixers: 
0: Realtek ALC655 rev0.

ralph@unkitty:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 
- IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

My lsmod is:

Module                  Size  Used by
nls_cp437               5888  0
msdos                   8320  0
fat                    37792  1 msdos
proc_intf               4100  0
cpufreq_powersave       1920  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
freq_table              4100  0
video                  16260  0
battery                10244  1
container               4608  0
button                  6800  0
pcc_acpi               11264  0
sony_acpi               6280  0
ac                      4996  0
ipv6                  229504  11
af_packet              20744  2
ohci1394               31876  0
r8169                  17928  0
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
snd_intel8x0           29984  1
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
usblp                  12032  0
ehci_hcd               29444  0
ohci_hcd               19848  0
usbcore               107384  4 usblp,ehci_hcd,ohci_hcd
i2c_nforce2             6400  0
i2c_core               21264  1 i2c_nforce2
nvidia_agp              7452  1
agpgart                31784  1 nvidia_agp
analog                 10784  0
gameport                4608  1 analog
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
tsdev                   7488  0
sr_mod                 16036  0
sbp2                   22408  0
evdev                   9088  0
scsi_mod              119936  2 sr_mod,sbp2
ieee1394              100408  2 ohci1394,sbp2
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  2 sr_mod,ide_cd
reiserfs              225616  7
ide_generic             1664  0
ide_disk               18176  11
amd74xx                13340  1
ide_core              118988  4 ide_cd,ide_generic,ide_disk,amd74xx
unix                   26164  596
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb
ralph@unkitty:~$ 

ralph@unkitty:~$ lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
0000:01:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
0000:02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev c1)
ralph@unkitty:~$ 

I have tried all sound config options in Kde control Center with no sound. All 
Kmix Input and Output sound sliders are at max. Switch settings seem to have 
had no effect. I am new to Debian Linux and 6 hours new to Kubuntu. This is 
really frustating me. Can someone help me trouble shoot and get sound 
working? Thanks for your help.

---

### Post by Martin Witte on 2005-04-09
I had a similiar problem when upgrading to hoary, although with different hardware, for me the solution was retrieved via this thread: 
[http://www.ubuntuforums.org/showthread.php?t=19617&highlight=sound+asrock](http://www.ubuntuforums.org/showthread.php?t=19617&highlight=sound+asrock)

it pannned down to start alsamixer, and mute item IEC958 Capture Monitor. Please be aware that alsamixer is keyboard driven - it uses arrow keys to switch items, and the 'm' to mute, 'ESC' to quit.

Hiope this helps

---

### Post by ralphdewitt on 2005-04-10
Sorry that tip did not work. Still without sound.

---

