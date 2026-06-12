---
title: "Intel High Def soundcard not working"
date: 2004-12-14
forum: Hardware &amp; Laptops
---

### Post by cacofonix on 2004-12-14
Im having trouble getting my sound card to work. I have an intel 82801FB high def soundcard. I have tried getting it to work in Warty and again with Hoary and it have had no luck. I have tried searching high and low for anyone with my problem and so far have come up with nada. I have modprobed the intel8x0 module and I have recieved no error lsmod states that it has been loaded but the sound card still wont work. Is my soundcard too new and I just need to wait for the drivers for it or is it something else entirely?


lspci output:
```

ubuntu:~ $ lspci
0000:00:00.0 Host bridge: Intel Corp. 915G/P/GV Processor to I/O Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 915G/P/GV PCI Express Root Port (rev 04)
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5b60
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5b70
0000:02:01.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
0000:02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

```

ubuntu:~ $ cat /proc/asound/cards
--- no soundcards ---

```

```

ubuntu:~ $ lsmod
Module                  Size  Used by
snd_intel8x0           31820  0
snd_ac97_codec         61520  1 snd_intel8x0
snd_pcm_oss            47400  0
snd_mixer_oss          16640  1 snd_pcm_oss
snd_pcm                85256  2 snd_intel8x0,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc          9608  2 snd_intel8x0,snd_pcm
gameport                4608  1 snd_intel8x0
snd_mpu401_uart         7168  1 snd_intel8x0
snd_rawmidi            22948  1 snd_mpu401_uart
snd_seq_device          7816  1 snd_rawmidi
snd                    50276  9 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9696  1 snd
proc_intf               3972  0
freq_table              4100  0
cpufreq_userspace       5208  0
cpufreq_ondemand        6044  0
cpufreq_powersave       1920  0
button                  6800  0
ac                      4996  0
battery                 9476  0
ipv6                  228224  8
af_packet              20744  2
usbhid                 29248  0
8139cp                 19072  0
8139too                24064  0
mii                     4736  2 8139cp,8139too
crc32                   4480  2 8139cp,8139too
piix                   12320  1
ehci_hcd               28036  0
uhci_hcd               29200  0
pciehp                 83684  0
shpchp                 87140  0
pci_hotplug            30512  2 pciehp,shpchp
intel_agp              20512  1
agpgart                31656  1 intel_agp
floppy                 54864  0
pcspkr                  3688  0
rtc                    12216  0
md                     43852  0
dm_mod                 51580  1
capability              4744  0
commoncap               7040  1 capability
parport_pc             33732  1
lp                     10280  0
parport                37192  2 parport_pc,lp
ide_generic             1536  0
ide_disk               17792  0
ide_cd                 38304  0
tsdev                   7360  0
evdev                   9088  0
cdrom                  36124  1 ide_cd
mousedev               11032  1
psmouse                22028  0
ext3                  108520  3
jbd                    55704  1 ext3
sd_mod                 16656  6
usb_storage            59840  0
usbcore               104804  6 usbhid,ehci_hcd,uhci_hcd,usb_storage
ide_core              128240  5 piix,ide_generic,ide_disk,ide_cd,usb_storage
ata_piix                8580  13
libata                 39684  1 ata_piix
scsi_mod              115660  3 sd_mod,usb_storage,libata
unix                   25908  645
thermal                13320  0
processor              17576  1 thermal
fan                     4100  0
fbcon                  35136  0
font                    8448  1 fbcon
vesafb                  6816  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

```


cacofonix

---

