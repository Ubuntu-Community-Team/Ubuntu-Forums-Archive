---
title: "Problems with sound card and dvd-writer"
date: 2005-08-15
forum: Hardware &amp; Laptops
---

### Post by Eagle32 on 2005-08-15
Hi, i'm sorry about my english mistakes, i can't speak english very well... :)
I'm using Kubuntu 5.04 with kernel 2.6.10-5-386 and i have 2 problems:

1- my sound card doesn't work, it is a realtek high definition audio integrated on the motherboard. Some time ago i solved this problem with this wiki: [https://wiki.ubuntu.com//ForPeopleWithRealtekHighDefinitionAudioAlsoKnownAsALC880AndReferredAsHDAIntelByAlsa](https://wiki.ubuntu.com//ForPeopleWithRealtekHighDefinitionAudioAlsoKnownAsALC880AndReferredAsHDAIntelByAlsa) but now i can't find it anymore.
My motherboard is a Gigabyte GA-8I915P-MF

2- my dvd-writer doesn't write. It works on reading, but not on writing. It is a LG GSA-4120B with A116 firmware. I think that the reason is because DMA is not enabled. How can i enable it?
This is the cdrecord error:
write track data: error after 253952 bytes
cdrecord: The current problem looks like a buffer underrun.
cdrecord: Try to use 'driveropts=burnfree'.
cdrecord: Make sure that you are root, enable DMA and check your HW/OS set up.

I tried to use driveropts=burnfree but it doesn't work equally.
This dvd-writer is the only optical drive on my pc.

Can anyone help me, please?

Thanks in advance.

---

### Post by Eagle32 on 2005-08-16
Noone?

Come on guys, if i not solve this problem i must return on windows :(

I have read many thread of other people wich had the same problems, but i'm a bit noob in linux and i can't recompile the kernel for example, or i can't add my chipset module (ICH6 family) to /etc/modules because i not understand what line i must add.

This is my lspci output:
```
$ lspci
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
0000:00:1f.2 IDE interface: Intel Corp. 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 3e50
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 3e70
0000:02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
0000:02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

And this is my lsmod output:
```
$ lsmod
Module                  Size  Used by
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  9
ipt_state               2048  20
ipt_REJECT              6528  4
ipt_limit               2688  6
ipt_LOG                 6656  6
ip_conntrack_ftp       72624  0
ip_conntrack           43668  2 ipt_state,ip_conntrack_ftp
iptable_filter          3840  1
ip_tables              17408  5 ipt_state,ipt_REJECT,ipt_limit,ipt_LOG,iptable_filter
ohci1394               31876  0
r8169                  17928  0
i2c_i801                8076  0
i2c_core               21264  1 i2c_i801
ehci_hcd               29444  0
uhci_hcd               30224  0
snd_hda_intel          16384  1
snd_hda_codec          64512  1 snd_hda_intel
snd_pcm_oss            47776  0
snd_mixer_oss          16896  1 snd_pcm_oss
snd_pcm                81416  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              23428  1 snd_pcm
snd                    52228  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  2 snd_hda_intel,snd_pcm
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
intel_agp              20636  1
agpgart                31784  1 intel_agp
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
fglrx                 229568  7
sbp2                   22408  0
ieee1394              100408  2 ohci1394,sbp2
evdev                   9088  0
ide_generic             1664  0
tsdev                   7488  0
ide_disk               18176  0
ide_cd                 38532  0
piix                    9988  0
mousedev               11160  1
psmouse                19336  0
ext3                  120968  3
jbd                    54168  1 ext3
sr_mod                 16036  0
cdrom                  36508  2 ide_cd,sr_mod
sd_mod                 16784  4
usb_storage            64064  0
usbcore               107384  4 ehci_hcd,uhci_hcd,usb_storage
ide_core              118988  5 ide_generic,ide_disk,ide_cd,piix,usb_storage
sg                     35360  0
ata_piix                8836  6
libata                 44548  1 ata_piix
scsi_mod              119936  6 sbp2,sr_mod,sd_mod,usb_storage,sg,libata
unix                   26164  434
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

```

When i try to enable dma with "sudo hdparm /dev/scd0" i get this output:
```
$ sudo hdparm /dev/scd0

/dev/scd0:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

```

Is there the possibility to resolve?  ](*,)

---

