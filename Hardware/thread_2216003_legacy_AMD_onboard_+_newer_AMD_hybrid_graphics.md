---
title: "legacy AMD onboard + newer AMD hybrid graphics?"
date: 2014-04-09
forum: Hardware
---

### Post by guicho2-71828 on 2014-04-09
Hi,

I have installed my Radeon5770 (Juniper) graphics card into a system with Radeon HD3300 (RS780)
onboard graphics.

Before installing 5770, the open-source "radeon" driver and legacy "fglrx"
proprietary driver worked. Upon installation, I removed the legacy "fglrx",
configured the "primary video device" in BIOS so that it uses 5770, and then both
radeon and fglrx(latest beta) driver worked fine with the new card. Now I am using
the beta fglrx.

However, I want to run the 5770 as a computing card (for opencl dev) and to use the
internal graphics mainly. It is because the UI almost freezes when I run the
experiment program on the card. I don't care about the performance of the internal
graphics chip, but I like it if at least radeon driver is running.

I tried changing the "primary video device" option in BIOS configuration back to
the previous state. I reconnected the display cable into the internal graphics
connector and rebooted. Now the internal graphics card is used while
the beta fglrx driver still remains in the system.

After reboot, I run "lspci" and both "HD3300" and "HD5770" showed up as expected.
Then I checked the driver with lsmod.
I expected that both "fglrx" and "radeon" are listed
because I still have "radeon" driver installed on the system.
However, actually not, and I guess "vesafb" driver is used now (see below).
Why this happen and how do I fix this?
Also, is there any way to ensure "HD3300" is running on "vesafb"?

```

[guicho ~]$ lsmod                                                                                                                                 
Module                  Size  Used by
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69130  0 
bnep                   19704  2 
bluetooth             372041  10 bnep,rfcomm
vesafb                 13828  2 
binfmt_misc            17468  1 
fglrx                8081247  0 
kvm_amd                59987  0 
kvm                   431754  1 kvm_amd
sp5100_tco             13979  0 
snd_hda_codec_hdmi     41154  2 
snd_hda_codec_realtek    56475  1 
edac_core              62291  0 
i2c_piix4              22106  0 
amd_iommu_v2           19054  1 fglrx
shpchp                 37032  0 
serio_raw              13413  0 
wmi                    19070  0 
edac_mce_amd           22617  0 
k10temp                13126  0 
microcode              23656  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_intel          52267  9 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_rawmidi            30095  1 snd_seq_midi
mac_hid                13205  0 
snd_pcm               102033  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  28 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101762  2 hid_generic,usbhid
pata_acpi              13038  0 
r8169                  67581  0 
pata_atiixp            13271  4 
ahci                   25819  0 
mii                    13934  1 r8169
libahci                32009  1 ahci
floppy                 69370  0 
```

The motherboard is Jetway's MA3-79GDG.
([http://www.jetway.com.tw/jw/motherboard_view.asp?productid=593&proname=MA3-79GDG%20COMBO/MA3-79GDG%20COMBOD](http://www.jetway.com.tw/jw/motherboard_view.asp?productid=593&proname=MA3-79GDG%20COMBO/MA3-79GDG%20COMBOD))
(BTW, it has both DDR2 and DDR3 slots. abnormal in a sense)

---

### Post by Mark Phelps on 2014-04-09
What version of Ubuntu are you running?

Also, open a terminal and enter "lspci" and look for the line containing "VGA". Post that result back here.

Oh ... and welcome to the forums.

---

### Post by guicho2-71828 on 2014-04-09
Thank you for response. The system is running on normal Ubuntu 13.10.
The lspci result is here.

```

[guicho ~]$ uname -a
Linux guicho-desktop 3.11.0-19-generic #33-Ubuntu SMP Tue Mar 11 18:48:34 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
[guicho ~]$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] RS780 Host Bridge
...
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS780D [Radeon HD 3300]
01:05.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RS780 HDMI Audio [Radeon (HD) 3000 Series]
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Juniper XT [Radeon HD 5770]
02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Juniper HDMI Audio [Radeon HD 5700 Series]

```

Also, I noticed -v option in lspci. I once thought it would show the driver name and it does for 5770, but it doesn't for 3300.

```

[guicho ~]$ sudo lspci -v -s 01:05.0
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS780D [Radeon HD 3300] (prog-if 00 [VGA controller])
        Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device 0000
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at c000 [size=256]
        Memory at fe9f0000 (32-bit, non-prefetchable) [size=64K]
        Memory at fe800000 (32-bit, non-prefetchable) [size=1M]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: [50] Power Management version 3
        Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
[guicho ~]$ sudo lspci -v -s 02:00.0
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Juniper XT [Radeon HD 5770] (prog-if 00 [VGA controller])
        Subsystem: Hightech Information System Ltd. Device 200a
        Flags: bus master, fast devsel, latency 0, IRQ 44
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at feae0000 (64-bit, non-prefetchable) [size=128K]
        I/O ports at d000 [size=256]
        Expansion ROM at feac0000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Legacy Endpoint, MSI 00
        Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
        Capabilities: [150] Advanced Error Reporting
        Kernel driver in use: fglrx_pci

```

---

