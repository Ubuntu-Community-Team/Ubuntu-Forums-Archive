---
title: "Modprobe DRM: &quot;Cannot Allocate Memory&quot;"
date: 2007-06-13
forum: Hardware &amp; Laptops
---

### Post by mbcook on 2007-06-13
OK. I think I have a good one for you guys. I'm familiar with Linux, but I've been out of it for a few years. I just got a new desktop at work made by Dell and I've put Ubuntu on it and I'm having trouble. I'm trying to get multiple monitors to work, but I'm running into issues.

Following other forum posts I installed the ATI driver and tried to configure it only to find that X didn't work. One monitor was blank, the other was off. Putting my X config back to the way the installer made it brought things back to running on clone mode.

I'm on a x86-64 system (Intel Xeon), and the graphics card in question is an ATI FireGL V3400. I'd like 3D, but at this point dual monitors is all that really matters. Here is the output of fglrx-info:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI FireGL V3400
OpenGL version string: 2.0.6334 (8.34.8)
```

Now in all my messing around, I'm pretty sure that this is a problem with the DRM module. Here are the modules currently loaded on my system:

```
Module                  Size  Used by
binfmt_misc            14604  1 
rfcomm                 45352  0 
l2cap                  28160  5 rfcomm
bluetooth              62468  4 rfcomm,l2cap
ppdev                  11272  0 
fglrx                 623096  11 
cpufreq_powersave       3072  0 
cpufreq_stats           8416  0 
cpufreq_conservative     9736  0 
cpufreq_ondemand       10640  0 
freq_table              6336  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       6176  0 
sony_acpi               7064  0 
pcc_acpi               15616  0 
dev_acpi               17028  0 
tc1100_wmi              9224  0 
video                  19080  0 
sbs                    17856  0 
i2c_ec                  6912  1 sbs
i2c_core               26496  1 i2c_ec
ac                      6920  0 
asus_acpi              19756  0 
button                 10016  0 
battery                12040  0 
container               6144  0 
dock                   11992  0 
backlight               8448  1 asus_acpi
ipv6                  307456  24 
lp                     15048  0 
fuse                   51888  0 
af_packet              27020  2 
snd_hda_intel          24224  1 
snd_hda_codec         262528  1 snd_hda_intel
snd_pcm_oss            49536  0 
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36608  0 
snd_seq_midi           11008  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               9092  0 
psmouse                43536  0 
parport_pc             40104  1 
parport                43404  3 ppdev,lp,parport_pc
pcspkr                  4736  0 
snd                    68904  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
shpchp                 37404  0 
pci_hotplug            36228  1 shpchp
snd_page_alloc         11792  2 snd_hda_intel,snd_pcm
tsdev                  10112  0 
evdev                  13056  3 
ext3                  143760  1 
jbd                    68208  1 ext3
mbcache                11400  1 ext3
sd_mod                 25092  3 
sg                     40616  0 
sr_mod                 18980  0 
cdrom                  40744  1 sr_mod
usbhid                 29088  0 
hid                    34048  1 usbhid
ata_piix               18308  0 
ata_generic            10628  0 
ahci                   25348  2 
ehci_hcd               37004  0 
libata                137000  3 ata_piix,ata_generic,ahci
scsi_mod              166968  4 sd_mod,sg,sr_mod,libata
generic                 6532  0 [permanent]
tg3                   114308  0 
uhci_hcd               28320  0 
usbcore               154416  4 usbhid,ehci_hcd,uhci_hcd
thermal                16912  0 
processor              34952  1 thermal
fan                     6536  0 
fbcon                  44416  0 
tileblit                4096  1 fbcon
font                    9856  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3712  1 bitblit
vesafb                 10376  0 
cfbcopyarea             5120  1 vesafb
cfbimgblt               4096  1 vesafb
cfbfillrect             5632  1 vesafb
capability              7048  0 
commoncap               9472  1 capability

```

Now you'll notice that radeon and DRM aren't listed. When I try to add the radeon driver, it won't load becuase it errors out loading the DRM driver and then can't find the right symbols. Here is what happens when I try to inster the DRM driver:

```
FATAL: Error inserting drm (/lib/modules/2.6.20-16-generic/kernel/drivers/char/drm/drm.ko): Cannot allocate memory

```

The output of dmesg contains this fun:

```
[   46.494957] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   46.496636] [fglrx] Maximum main memory to use for locked dma buffers: 1883 MBytes.
[   46.496817] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   46.510768] ACPI: PCI Interrupt 0000:07:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   46.667014] ppdev: user-space parallel port driver
[   47.925631] mtrr: type mismatch for c0000000,8000000 old: write-back new: write-combining
[   47.925636] [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
[   47.928440] [fglrx] total      GART = 130023424
[   47.928444] [fglrx] free       GART = 114032640
[   47.928446] [fglrx] max single GART = 114032640
[   47.928447] [fglrx] total      LFB  = 134086656
[   47.928450] [fglrx] free       LFB  = 116256768
[   47.928451] [fglrx] max single LFB  = 116256768
[   47.928453] [fglrx] total      Inv  = 0
[   47.928455] [fglrx] free       Inv  = 0
[   47.928456] [fglrx] max single Inv  = 0
[   47.928458] [fglrx] total      TIM  = 0
[   48.612173] Bluetooth: Core ver 2.11

```

I'm not sure at this point. My usual next step would be to recompile the kernel, but I'm trying to avoid and figure out why this isn't working. I could really use help from someone who knows this. I haven't setup a linux system in a few years, I've never used the ATI binary driver, and this is my first use of linux on an x86-64 so I'm not sure of what issues that will entail with the rest of this fun.

PS:

uname:

```
Linux mcook-desktop 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux

```

---

### Post by mbcook on 2007-06-13
OK, a local linux genius who knows more about me than this was able to get multi-monitor working by changing the Xorg.conf file to add screens, etc. So I suppose things seem fixed.

All that said, I would still love it if someone could explain what was causing the above out of memory thing to me. I'm curious now.

---

### Post by az on 2007-06-13
> **mbcook said:**
> 
All that said, I would still love it if someone could explain what was causing the above out of memory thing to me. I'm curious now.

I dunno, but I reckon X allocates memory as it starts.  To try to load a module that wants to manage that memory, I think you need to load it before X starts.

For example, if you run glx on an old video card with not a lot of ram, Ubuntu will automatically use the highest 2D resolution and color depth.  If there is no ram available for GLX, it will not work.  Switching your resolution down will not free up the memory either - in that case what you have to do is reconfigure X to use a lower resolution and color depth and then restart X.  That's the only way you can free up memory on such older cards.

---

