---
title: "TV-out problems with NVidia FX5200"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by daengbo on 2008-01-23
I had a 6.06LTS installation with a working s-video out for a NVidia FX5200. There is no monitor for this setup, because the machine is a combination NAS and media center using MythTV. It was working very well.

When I updated to 7.04 -> 7.10, the TV-Out stopped working. Not only did it stop, the entire machine froze. I coulldn't CTRL-ALT-BACK. I couldn't SSH in. I could, however ALT-PRTSCRN-REISUB to reboot.

I tried every howto I could, but eventually gave up and used a Vesa driver, which worked fine with no TV-OUT configuration. I've been living with that for some time, even though the load spikes to 3.0 when playing videos full-screen.

Well, I started trying again, specifically because I want to replace the heavy MythTV with a lighter Elisa. Elisa needs OpenGL.

Envy doesn't work. The computer hangs up the same as before.

lspci
-----------------------------
00:00.0 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

current, working xorg.conf
---------------------------------
...
Section "Module"
    Load           "glx"
EndSection
...
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV34 [GeForce FX 5200]"
    Driver         "vesa"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34 [GeForce FX 5200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Problematic xorg.conf
-----------------------------------
...
Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

...
Section "Device"
        Identifier      "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
        Driver      "nvidia"
        VendorName  "Chaintech"
        BoardName   "nVidia GeForce 4 MX 440"
        Option      "RenderAccel" "1"
        # TV Out Setup
        Option      "TVStandard" "NTSC-M"
        Option      "TVOutFormat" "SVIDEO"
#       Option      "TVOverScan" "0.6"
        Option      "ConnectedMonitor" "TV" # Add this if you're having problems
        Option      "NoLogo" "True"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-68
        VertRefresh     50-120
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "720x480" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "648x486" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "648x486" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "648x486" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "648x486" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "648x486" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
...
Section "DRI"
        Mode    0666
EndSection

lsmod
---------------------
iptable_filter          3968  0 
ip_tables              13924  1 iptable_filter
x_tables               16260  1 ip_tables
nfsd                  220912  13 
exportfs                7040  1 nfsd
lockd                  67592  2 nfsd
sunrpc                172412  8 nfsd,lockd
ipv6                  273892  28 
xfs                   575192  2 
lp                     12580  0 
snd_via82xx            29336  1 
gameport               16776  1 snd_via82xx
snd_ac97_codec        100644  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_mpu401_uart         9600  1 snd_via82xx
snd_pcm_oss            44672  0 
snd_pcm                80388  4 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
psmouse                39952  0 
serio_raw               8068  0 
nvidia               7859584  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
parport_pc             37412  1 
parport                37448  2 lp,parport_pc
snd                    54660  12 snd_via82xx,snd_ac97_codec,snd_mpu401_uart,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_viapro             10004  0 
soundcore               8800  1 snd
i2c_core               26112  2 nvidia,i2c_viapro
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
af_packet              24840  2 
via_agp                11264  1 
agpgart                35016  2 nvidia,via_agp
evdev                  11136  1 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  6 
sg                     36764  0 
sd_mod                 30336  2 
floppy                 60004  0 
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  3 ehci_hcd,uhci_hcd
via82cxxx              10372  0 [permanent]
ide_core              116804  3 ide_cd,ide_disk,via82cxxx
sata_via               12548  1 
ata_generic             8452  0 
libata                125168  2 sata_via,ata_generic
scsi_mod              147084  3 sg,sd_mod,libata
8139too                27776  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
raid10                 26496  0 
raid456               128016  0 
xor                    16904  1 raid456
raid1                  25984  0 
raid0                   9728  0 
multipath               9984  0 
linear                  7552  0 
md_mod                 82324  7 raid10,raid456,raid1,raid0,multipath,linear
dm_mirror              24448  0 
dm_snapshot            18980  0 
dm_mod                 58816  2 dm_mirror,dm_snapshot
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

---

### Post by dmiller40 on 2008-02-02
daengbo 

sorry i am no help to your problem, but was hoping you could be to mine. I too have the fx5200 and am using the s-vid out to my tv. (hoping to get mythtv working soon) I have installed the nvidia restricted driver for the card and it is working.

the only problem i'm having is it's not using the full screen, there is a black frame all the way around my screen. I've got it set to the highest resolution 1024x768. any ideas?

thanks
dm

---

### Post by chammy on 2008-02-03
> **dmiller40 said:**
> daengbo 
the only problem i'm having is it's not using the full screen, there is a black frame all the way around my screen. I've got it set to the highest resolution 1024x768. any ideas?
dm

Try using overscan:
```
Option "TVOverScan" "0.6"
```

---

