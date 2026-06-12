---
title: "Update Killed Broadcom 4321"
date: 2009-03-17
forum: Hardware
---

### Post by TSS on 2009-03-17
Previously I've used my broadcom wireless just fine with the restricted drivers.   With the most recent update to 8.10 my Broadcom card no longer works and the restricted driver does not show up in the drivers section. any ideas?  Also, it's no longer recognized in lspci:

lspci
```

tim@wall:~$ lspci 
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

```
lsmod
```

tim@wall:~$ lsmod
Module                  Size  Used by
vmnet                  48580  13 
vmci                   58964  0 
vmmon                  78064  0 
af_packet              25728  2 
binfmt_misc            16904  1 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  2 
l2cap                  30464  16 bnep,rfcomm
ipv6                  263972  21 
ppdev                  15620  0 
powernow_k8            22148  1 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
pci_slot               12680  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ext2                   72584  1 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
snd_hda_intel         384176  5 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
serio_raw              13444  0 
joydev                 18368  0 
psmouse                45200  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
uvcvideo               63624  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
usbtouchscreen         17540  0 
compat_ioctl32          9344  1 uvcvideo
evdev                  17696  13 
videodev               41344  1 uvcvideo
v4l1_compat            22404  2 uvcvideo,videodev
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
k8temp                 12416  0 
snd                    63268  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
isp1760                26120  0 
btusb                  19736  3 
bluetooth              61924  11 sco,bnep,rfcomm,l2cap,btusb
video                  25232  5 
output                 11008  1 video
nvidia               6909268  29 
wmi                    14504  0 
agpgart                42184  1 nvidia
battery                18436  0 
i2c_nforce2            14468  0 
ac                     12292  0 
button                 14224  0 
i2c_core               31892  2 nvidia,i2c_nforce2
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  2 ext2,ext3
sd_mod                 42392  4 
crc_t10dif              9984  1 sd_mod
usbhid                 35840  0 
hid                    50560  1 usbhid
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
pata_acpi              12160  0 
sata_nv                30600  3 
pata_amd               18692  0 
ata_generic            12932  0 
forcedeth              61328  0 
libata                178208  4 pata_acpi,sata_nv,pata_amd,ata_generic
scsi_mod              155212  4 sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
ohci_hcd               32016  0 
ehci_hcd               43788  0 
usbcore               149360  8 uvcvideo,usbtouchscreen,isp1760,btusb,usbhid,ohci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  2 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

```

Thanks for your time.

---

