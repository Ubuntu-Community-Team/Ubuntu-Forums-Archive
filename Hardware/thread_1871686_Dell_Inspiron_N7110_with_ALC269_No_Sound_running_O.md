---
title: "Dell Inspiron N7110 with ALC269 No Sound running Ocelot"
date: 2011-10-29
forum: Hardware
---

### Post by harrisoncohix on 2011-10-29
Dell Inspiron N7110 with a Realtek Audio ALC269, running Ocelot. Checked alsamixer, sound levels were good, changed outputs in gstreamer to alsa and got a beep on test, but nothing else.

lsmod:
```
Module                  Size  Used by
snd_intel8x0           33318  0 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
arc4                   12473  2 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
btusb                  18160  2 
bluetooth             148839  23 bnep,rfcomm,btusb
psmouse                63474  0 
serio_raw              12990  0 
snd_hda_intel          28358  1 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  5 snd_intel8x0,snd_ac97_codec,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  505143  3 
wmi                    18744  1 dell_wmi
iwlagn                273937  0 
drm_kms_helper         32889  1 i915
snd                    55902  14 snd_intel8x0,snd_ac97_codec,snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   196322  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
mac80211              393459  1 iwlagn
mei                    36466  0 
cfg80211              172392  2 iwlagn,mac80211
soundcore              12600  1 snd
snd_page_alloc         14108  3 snd_intel8x0,snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
usbhid                 41905  0 
uas                    17699  0 
hid                    77367  1 usbhid
ahci                   21634  4 
libahci                25761  1 ahci
r8169                  47200  0 
xhci_hcd               77080  0 
```lspci -v:

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    Subsystem: Dell Device 04d8
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 04d8
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Dell Device 04d8
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d1705000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
    Subsystem: Dell Device 04d8
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at d170a000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
    Subsystem: Dell Device 04d8
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at d1700000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: d1600000-d16fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: d1500000-d15fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Prefetchable memory behind bridge: 00000000d0400000-00000000d04fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=08, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d0d00000-d14fffff
    Prefetchable memory behind bridge: 00000000d0500000-00000000d0cfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
    Subsystem: Dell Device 04d8
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at d1709000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
    Subsystem: Dell Device 04d8
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
    Subsystem: Dell Device 04d8
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 46
    I/O ports at 4088 [size=8]
    I/O ports at 4094 [size=4]
    I/O ports at 4080 [size=8]
    I/O ports at 4090 [size=4]
    I/O ports at 4060 [size=32]
    Memory at d1708000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
    Subsystem: Dell Device 04d8
    Flags: medium devsel, IRQ 10
    Memory at d1704000 (64-bit, non-prefetchable) [size=256]
    I/O ports at efa0 [size=32]
    Kernel modules: i2c-i801

01:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
    Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at d1600000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: Dell Device 04d8
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at d1500000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci-hcd

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
    Subsystem: Dell Device 04d8
    Flags: bus master, fast devsel, latency 0, IRQ 45
    I/O ports at 3000 [size=256]
    Memory at d0404000 (64-bit, prefetchable) [size=4K]
    Memory at d0400000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

``` Tried this fix, didn't do a whole lot. Synaptic couldn't find the files anymore: [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

---

