---
title: "no sound in ubuntu 9.04 acer travelmate 4601"
date: 2009-05-02
forum: Hardware
---

### Post by prafull on 2009-05-02
i using Acer Travelmate 4601 laptop. on ubuntu 9.04. all updated patch till 30apr09.

my problem is no sound .. i dont understand it is sound card proble or laptop speaker problem.

help me find out.
following link will tell you about my alsa config.
[http://www.alsa-project.org/db/?f=738f62407d0deab12ab584d909fbdb39ef4e29db](http://www.alsa-project.org/db/?f=738f62407d0deab12ab584d909fbdb39ef4e29db)

Linux prafull-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [Intel ICH6 Modem], device 0: Intel ICH - Modem [Intel ICH6 Modem - Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

lspci -v 
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0066
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: c8100000-c81fffff
    Prefetchable memory behind bridge: d0000000-d7ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 0066
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 0066
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 0066
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 0066
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04) (prog-if 20)
    Subsystem: Acer Incorporated [ALI] Device 0066
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at c8000000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=08, sec-latency=216
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: c8200000-c82fffff
    Prefetchable memory behind bridge: 0000000068000000-000000006bffffff
    Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 0066
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 1c00 [size=256]
    I/O ports at 1880 [size=64]
    Memory at c8000800 (32-bit, non-prefetchable) [size=512]
    Memory at c8000400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 0066
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 2400 [size=256]
    I/O ports at 2000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH Modem
    Kernel modules: snd-intel8x0m

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 0066
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04) (prog-if 8a [Master SecP PriP])
    Subsystem: Acer Incorporated [ALI] Device 0066
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 18c0 [size=16]
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 0066
    Flags: medium devsel, IRQ 11
    I/O ports at 20a0 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
    Subsystem: Acer Incorporated [ALI] Device 0066
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d0000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 3000 [size=256]
    Memory at c8100000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at c8120000 [disabled] [size=128K]
    Capabilities: <access denied>

06:01.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
    Subsystem: Acer Incorporated [ALI] Device 0066
    Flags: bus master, medium devsel, latency 168, IRQ 18
    Memory at c8216000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=06, secondary=07, subordinate=08, sec-latency=176
    Memory window 0: 68000000-6bfff000 (prefetchable)
    Memory window 1: 6c000000-6ffff000
    I/O window 0: 00004000-000040ff
    I/O window 1: 00004400-000044ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

06:01.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
    Subsystem: Acer Incorporated [ALI] Device 0066
    Flags: bus master, medium devsel, latency 32, IRQ 18
    Memory at c8217000 (32-bit, non-prefetchable) [size=2K]
    Memory at c8210000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

06:01.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
    Subsystem: Acer Incorporated [ALI] Device 0066
    Flags: bus master, medium devsel, latency 57, IRQ 18
    Memory at c8214000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1

06:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
    Subsystem: Intel Corporation Device 2701
    Flags: bus master, medium devsel, latency 32, IRQ 17
    Memory at c8218000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ipw2200
    Kernel modules: ipw2200

06:08.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0066
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
    Memory at c8200000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: tg3
    Kernel modules: tg3

prafull@prafull-laptop:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/2.6.28-11-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.28-11-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-als100.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-sc6000.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/opti9xx/snd-miro.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-azt2320.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-es18xx.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-sscape.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-dt019x.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-es968.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-sgalaxy.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/wss/snd-wss-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-adlib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/cs423x/snd-cs4236-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/cs423x/snd-cs4236.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/cs423x/snd-cs4232.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-sis7019.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.28-11-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.28-11-generic/kernel/sound/usb/snd-usb-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/2.6.28-11-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.28-11-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.28-11-generic/kernel/sound/oss/msnd_classic.ko
/lib/modules/2.6.28-11-generic/kernel/sound/oss/msnd_pinnacle.ko
/lib/modules/2.6.28-11-generic/kernel/sound/oss/msnd.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-ak4535.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8971.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-uda1380.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8900.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-ad73311.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8990.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/other/snd-ak4114.ko


dmesg

[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005fe80000 (usable)
[    0.000000]  BIOS-e820: 000000005fe80000 - 000000005fe89000 (ACPI data)
[    0.000000]  BIOS-e820: 000000005fe89000 - 000000005ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005ff00000 - 0000000060000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x5fe80 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000005fe80000 (usable)
[    0.000000]  modified: 000000005fe80000 - 000000005fe89000 (ACPI data)
[    0.000000]  modified: 000000005fe89000 - 000000005ff00000 (ACPI NVS)
[    0.000000]  modified: 000000005ff00000 - 0000000060000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  modified: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 37885000 - 37fef765
[    0.000000] Allocated new RAMDISK: 00881000 - 00feb765
[    0.000000] Move RAMDISK from 0000000037885000 - 0000000037fef764 to 00881000 - 00feb764
[    0.000000] ACPI: RSDP 000F69F0, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 5FE81054, 0044 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 5FE88E8A, 0074 (r1 INTEL  ALVISO    6040000 LOHR       5F)
[    0.000000] ACPI: DSDT 5FE818CE, 75BC (r1 INTEL  ALVISO    6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 5FE99FC0, 0040
[    0.000000] ACPI: APIC 5FE88EFE, 0066 (r1 INTEL  ALVISO    6040000 LOHR       5F)
[    0.000000] ACPI: HPET 5FE88F64, 0038 (r1 INTEL  ALVISO    6040000 LOHR       5F)
[    0.000000] ACPI: MCFG 5FE88F9C, 003C (r1 INTEL  ALVISO    6040000 LOHR       5F)
[    0.000000] ACPI: BOOT 5FE88FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 5FE81489, 0235 (r1  PmRef  Cpu0Ist     3000 INTL 20030224)
[    0.000000] ACPI: SSDT 5FE812B1, 01D8 (r1  PmRef  Cpu0Cst     3001 INTL 20030224)
[    0.000000] ACPI: SSDT 5FE81098, 0219 (r1  PmRef    CpuPm     3000 INTL 20030224)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 650MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000881000 - 0000feb765]      NEW RAMDISK ==> [0000881000 - 0000feb765]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0005fe80
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0005fe80
[    0.000000] On node 0 totalpages: 392709
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1302 pages used for memmap
[    0.000000]   HighMem zone: 165228 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec20000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 2, version 255, address 0xfec20000, GSI 24-279
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0x0 is invalid
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
[    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 68000000 (gap: 60000000:80000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 389639
[    0.000000] Kernel command line: root=UUID=92ef8699-8685-4884-8309-1c0c59a0532a ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1596.131 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 7856640 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1533796k/1571328k available (4126k kernel code, 36144k reserved, 2208k data, 532k init, 666120k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004016] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.26 BogoMIPS (lpj=6384524)
[    0.004041] Security Framework initialized
[    0.004053] SELinux:  Disabled at boot.
[    0.004082] AppArmor: AppArmor initialized
[    0.004093] Mount-cache hash table entries: 512
[    0.004271] Initializing cgroup subsys ns
[    0.004278] Initializing cgroup subsys cpuacct
[    0.004281] Initializing cgroup subsys memory
[    0.004286] Initializing cgroup subsys freezer
[    0.004305] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004309] CPU: L2 cache: 2048K
[    0.004326] Checking 'hlt' instruction... OK.
[    0.020755] SMP alternatives: switching to UP code
[    0.140480] Freeing SMP alternatives: 18k freed
[    0.140484] ACPI: Core revision 20080926
[    0.146499] ACPI: Checking initramfs for custom DSDT
[    0.534335] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.574034] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 08
[    0.576002] Brought up 1 CPUs
[    0.576002] Total of 1 processors activated (3192.26 BogoMIPS).
[    0.576002] CPU0 attaching NULL sched-domain.
[    0.576002] net_namespace: 776 bytes
[    0.576002] Booting paravirtualized kernel on bare hardware
[    0.576002] Time:  3:46:15  Date: 05/02/09
[    0.576002] regulator: core version 0.5
[    0.576002] NET: Registered protocol family 16
[    0.576002] EISA bus registered
[    0.576002] ACPI: bus type pci registered
[    0.576002] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.576002] PCI: MCFG area at e0000000 reserved in E820
[    0.576002] PCI: Using MMCONFIG for extended config space
[    0.576002] PCI: Using configuration type 1 for base access
[    0.576002] ACPI: EC: Look up EC in DSDT
[    0.880666] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.880923] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.919683] ACPI: Interpreter enabled
[    0.919688] ACPI: (supports S0 S3 S4 S5)
[    0.919708] ACPI: Using IOAPIC for interrupt routing
[    0.925475] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    0.925478] ACPI: EC: driver started in interrupt mode
[    0.926202] ACPI: ACPI Dock Station Driver: 2 docks/bays found
[    0.926213] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.926301] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.926305] pci 0000:00:01.0: PME# disabled
[    0.926396] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.926401] pci 0000:00:1c.0: PME# disabled
[    0.926468] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.926473] pci 0000:00:1c.1: PME# disabled
[    0.926537] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.926542] pci 0000:00:1c.2: PME# disabled
[    0.926605] pci 0000:00:1d.0: reg 20 io port: [0x1800-0x181f]
[    0.926665] pci 0000:00:1d.1: reg 20 io port: [0x1820-0x183f]
[    0.926724] pci 0000:00:1d.2: reg 20 io port: [0x1840-0x185f]
[    0.926783] pci 0000:00:1d.3: reg 20 io port: [0x1860-0x187f]
[    0.926846] pci 0000:00:1d.7: reg 10 32bit mmio: [0xc8000000-0xc80003ff]
[    0.926891] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.926897] pci 0000:00:1d.7: PME# disabled
[    0.926990] pci 0000:00:1e.2: reg 10 io port: [0x1c00-0x1cff]
[    0.926997] pci 0000:00:1e.2: reg 14 io port: [0x1880-0x18bf]
[    0.927006] pci 0000:00:1e.2: reg 18 32bit mmio: [0xc8000800-0xc80009ff]
[    0.927014] pci 0000:00:1e.2: reg 1c 32bit mmio: [0xc8000400-0xc80004ff]
[    0.927042] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.927047] pci 0000:00:1e.2: PME# disabled
[    0.927084] pci 0000:00:1e.3: reg 10 io port: [0x2400-0x24ff]
[    0.927092] pci 0000:00:1e.3: reg 14 io port: [0x2000-0x207f]
[    0.927131] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
[    0.927136] pci 0000:00:1e.3: PME# disabled
[    0.927227] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.927234] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.927239] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.927263] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.927271] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.927279] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.927287] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.927295] pci 0000:00:1f.1: reg 20 io port: [0x18c0-0x18cf]
[    0.927369] pci 0000:00:1f.3: reg 20 io port: [0x20a0-0x20bf]
[    0.927422] pci 0000:01:00.0: reg 10 32bit mmio: [0xd0000000-0xd7ffffff]
[    0.927428] pci 0000:01:00.0: reg 14 io port: [0x3000-0x30ff]
[    0.927434] pci 0000:01:00.0: reg 18 32bit mmio: [0xc8100000-0xc810ffff]
[    0.927450] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.927457] pci 0000:01:00.0: supports D1 D2
[    0.927510] pci 0000:00:01.0: bridge io port: [0x3000-0x3fff]
[    0.927514] pci 0000:00:01.0: bridge 32bit mmio: [0xc8100000-0xc81fffff]
[    0.927518] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xd7ffffff]
[    0.927572] pci 0000:00:1c.0: bridge io port: [0x00-0xfff]
[    0.927578] pci 0000:00:1c.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.927586] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.927642] pci 0000:00:1c.1: bridge io port: [0x00-0xfff]
[    0.927647] pci 0000:00:1c.1: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.927655] pci 0000:00:1c.1: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.927710] pci 0000:00:1c.2: bridge io port: [0x00-0xfff]
[    0.927715] pci 0000:00:1c.2: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.927723] pci 0000:00:1c.2: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.927773] pci 0000:06:01.0: reg 10 32bit mmio: [0xc8216000-0xc8216fff]
[    0.927786] pci 0000:06:01.0: supports D1 D2
[    0.927789] pci 0000:06:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.927795] pci 0000:06:01.0: PME# disabled
[    0.927844] pci 0000:06:01.2: reg 10 32bit mmio: [0xc8217000-0xc82177ff]
[    0.927854] pci 0000:06:01.2: reg 14 32bit mmio: [0xc8210000-0xc8213fff]
[    0.927904] pci 0000:06:01.2: supports D1 D2
[    0.927906] pci 0000:06:01.2: PME# supported from D0 D1 D2 D3hot
[    0.927912] pci 0000:06:01.2: PME# disabled
[    0.927958] pci 0000:06:01.3: reg 10 32bit mmio: [0xc8214000-0xc8215fff]
[    0.928019] pci 0000:06:01.3: supports D1 D2
[    0.928021] pci 0000:06:01.3: PME# supported from D0 D1 D2 D3hot
[    0.928027] pci 0000:06:01.3: PME# disabled
[    0.928082] pci 0000:06:03.0: reg 10 32bit mmio: [0xc8218000-0xc8218fff]
[    0.928137] pci 0000:06:03.0: PME# supported from D0 D3hot D3cold
[    0.928143] pci 0000:06:03.0: PME# disabled
[    0.928221] pci 0000:06:08.0: reg 10 32bit mmio: [0xc8200000-0xc820ffff]
[    0.928278] pci 0000:06:08.0: PME# supported from D3hot D3cold
[    0.928284] pci 0000:06:08.0: PME# disabled
[    0.928335] pci 0000:00:1e.0: transparent bridge
[    0.928344] pci 0000:00:1e.0: bridge 32bit mmio: [0xc8200000-0xc82fffff]
[    0.928399] bus 00 -> node 0
[    0.928407] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.928838] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.929010] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.929178] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.929364] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.934626] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.934763] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.934898] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.935033] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.935166] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.935300] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.935435] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.935570] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.935790] ACPI: WMI: Mapper loaded
[    0.935961] SCSI subsystem initialized
[    0.936009] libata version 3.00 loaded.
[    0.936058] usbcore: registered new interface driver usbfs
[    0.936076] usbcore: registered new interface driver hub
[    0.936103] usbcore: registered new device driver usb
[    0.936229] PCI: Using ACPI for IRQ routing
[    0.936235] pci 0000:00:1c.0: BAR 7: can't allocate resource
[    0.936237] pci 0000:00:1c.0: BAR 8: can't allocate resource
[    0.936240] pci 0000:00:1c.0: BAR 9: can't allocate resource
[    0.936242] pci 0000:00:1c.1: BAR 7: can't allocate resource
[    0.936245] pci 0000:00:1c.1: BAR 8: can't allocate resource
[    0.936247] pci 0000:00:1c.1: BAR 9: can't allocate resource
[    0.936250] pci 0000:00:1c.2: BAR 7: can't allocate resource
[    0.936252] pci 0000:00:1c.2: BAR 8: can't allocate resource
[    0.936254] pci 0000:00:1c.2: BAR 9: can't allocate resource
[    0.936374] Bluetooth: Core ver 2.13
[    0.936374] NET: Registered protocol family 31
[    0.936374] Bluetooth: HCI device and connection manager initialized
[    0.936374] Bluetooth: HCI socket layer initialized
[    0.936374] NET: Registered protocol family 8
[    0.936374] NET: Registered protocol family 20
[    0.936374] NetLabel: Initializing
[    0.936374] NetLabel:  domain hash size = 128
[    0.936374] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.936374] NetLabel:  unlabeled traffic allowed by default
[    0.936374] hpet clockevent registered
[    0.936374] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.936374] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.936374] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.940066] AppArmor: AppArmor Filesystem Enabled
[    0.940073] pnp: PnP ACPI init
[    0.940073] ACPI: bus type pnp registered
[    0.943470] pnp: PnP ACPI: found 11 devices
[    0.943472] ACPI: ACPI bus type pnp unregistered
[    0.943476] PnPBIOS: Disabled by ACPI PNP
[    0.943487] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.943491] system 00:01: iomem range 0xf0000000-0xf0003fff has been reserved
[    0.943494] system 00:01: iomem range 0xf0004000-0xf0004fff has been reserved
[    0.943497] system 00:01: iomem range 0xf0005000-0xf0005fff has been reserved
[    0.943500] system 00:01: iomem range 0xf0008000-0xf000bfff has been reserved
[    0.943504] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.943512] system 00:04: ioport range 0x680-0x6ff has been reserved
[    0.943515] system 00:04: ioport range 0x800-0x80f has been reserved
[    0.943518] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.943521] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    0.943524] system 00:04: ioport range 0x1600-0x167f has been reserved
[    0.978360] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.978364] pci 0000:00:01.0:   IO window: 0x3000-0x3fff
[    0.978368] pci 0000:00:01.0:   MEM window: 0xc8100000-0xc81fffff
[    0.978372] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000d7ffffff
[    0.978377] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:09
[    0.978380] pci 0000:00:1c.0:   IO window: disabled
[    0.978386] pci 0000:00:1c.0:   MEM window: disabled
[    0.978391] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.978398] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0a
[    0.978401] pci 0000:00:1c.1:   IO window: disabled
[    0.978407] pci 0000:00:1c.1:   MEM window: disabled
[    0.978412] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.978420] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:02
[    0.978422] pci 0000:00:1c.2:   IO window: disabled
[    0.978428] pci 0000:00:1c.2:   MEM window: disabled
[    0.978433] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.978444] pci 0000:06:01.0: CardBus bridge, secondary bus 0000:07
[    0.978446] pci 0000:06:01.0:   IO window: 0x004000-0x0040ff
[    0.978452] pci 0000:06:01.0:   IO window: 0x004400-0x0044ff
[    0.978458] pci 0000:06:01.0:   PREFETCH window: 0x68000000-0x6bffffff
[    0.978464] pci 0000:06:01.0:   MEM window: 0x6c000000-0x6fffffff
[    0.978470] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.978474] pci 0000:00:1e.0:   IO window: 0x4000-0x4fff
[    0.978481] pci 0000:00:1e.0:   MEM window: 0xc8200000-0xc82fffff
[    0.978486] pci 0000:00:1e.0:   PREFETCH window: 0x00000068000000-0x0000006bffffff
[    0.978502] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.978506] pci 0000:00:01.0: setting latency timer to 64
[    0.978515] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.978522] pci 0000:00:1c.0: setting latency timer to 64
[    0.978531] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.978537] pci 0000:00:1c.1: setting latency timer to 64
[    0.978547] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.978553] pci 0000:00:1c.2: setting latency timer to 64
[    0.978562] pci 0000:00:1e.0: setting latency timer to 64
[    0.978572] pci 0000:06:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.978579] bus: 00 index 0 io port: [0x00-0xffff]
[    0.978581] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.978584] bus: 01 index 0 io port: [0x3000-0x3fff]
[    0.978587] bus: 01 index 1 mmio: [0xc8100000-0xc81fffff]
[    0.978590] bus: 01 index 2 mmio: [0xd0000000-0xd7ffffff]
[    0.978592] bus: 01 index 3 mmio: [0x0-0x0]
[    0.978595] bus: 09 index 0 mmio: [0x0-0xfff]
[    0.978597] bus: 09 index 1 mmio: [0x0-0xfffff]
[    0.978599] bus: 09 index 2 mmio: [0x0-0xfffff]
[    0.978601] bus: 09 index 3 mmio: [0x0-0x0]
[    0.978604] bus: 0a index 0 mmio: [0x0-0xfff]
[    0.978606] bus: 0a index 1 mmio: [0x0-0xfffff]
[    0.978608] bus: 0a index 2 mmio: [0x0-0xfffff]
[    0.978610] bus: 0a index 3 mmio: [0x0-0x0]
[    0.978613] bus: 02 index 0 mmio: [0x0-0xfff]
[    0.978615] bus: 02 index 1 mmio: [0x0-0xfffff]
[    0.978617] bus: 02 index 2 mmio: [0x0-0xfffff]
[    0.978620] bus: 02 index 3 mmio: [0x0-0x0]
[    0.978622] bus: 06 index 0 io port: [0x4000-0x4fff]
[    0.978625] bus: 06 index 1 mmio: [0xc8200000-0xc82fffff]
[    0.978627] bus: 06 index 2 mmio: [0x68000000-0x6bffffff]
[    0.978630] bus: 06 index 3 io port: [0x00-0xffff]
[    0.978632] bus: 06 index 4 mmio: [0x000000-0xffffffff]
[    0.978635] bus: 07 index 0 io port: [0x4000-0x40ff]
[    0.978638] bus: 07 index 1 io port: [0x4400-0x44ff]
[    0.978640] bus: 07 index 2 mmio: [0x68000000-0x6bffffff]
[    0.978643] bus: 07 index 3 mmio: [0x6c000000-0x6fffffff]
[    0.978652] NET: Registered protocol family 2
[    0.978769] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.979043] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.979751] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.980214] TCP: Hash tables configured (established 131072 bind 65536)
[    0.980218] TCP reno registered
[    0.980351] NET: Registered protocol family 1
[    0.980504] checking if image is initramfs... it is
[    1.440005] Switched to high resolution mode on CPU 0
[    1.764134] Freeing initrd memory: 7593k freed
[    1.764189] Simple Boot Flag at 0x36 set to 0x1
[    1.764227] cpufreq: No nForce2 chipset.
[    1.764417] audit: initializing netlink socket (disabled)
[    1.764440] type=2000 audit(1241235976.764:1): initialized
[    1.773675] highmem bounce pool size: 64 pages
[    1.773682] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.775167] VFS: Disk quotas dquot_6.5.1
[    1.775237] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.775952] fuse init (API version 7.10)
[    1.776059] msgmni has been set to 1711
[    1.776259] alg: No test for stdrng (krng)
[    1.776273] io scheduler noop registered
[    1.776275] io scheduler anticipatory registered
[    1.776278] io scheduler deadline registered
[    1.776294] io scheduler cfq registered (default)
[    1.776510] pci 0000:01:00.0: Boot video device
[    1.780451] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.780483] pcieport-driver 0000:00:01.0: found MSI capability
[    1.780507] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.780516] pci_express 0000:00:01.0cie00: allocate port service
[    1.780533] pci_express 0000:00:01.0cie03: allocate port service
[    1.780579] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.780624] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.780655] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.780671] pci_express 0000:00:1c.0cie00: allocate port service
[    1.780686] pci_express 0000:00:1c.0cie02: allocate port service
[    1.780701] pci_express 0000:00:1c.0cie03: allocate port service
[    1.780770] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.780815] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.780846] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[    1.780861] pci_express 0000:00:1c.1cie00: allocate port service
[    1.780875] pci_express 0000:00:1c.1cie02: allocate port service
[    1.780889] pci_express 0000:00:1c.1cie03: allocate port service
[    1.780959] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.781004] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.781035] pcieport-driver 0000:00:1c.2: irq 2300 for MSI/MSI-X
[    1.781050] pci_express 0000:00:1c.2cie00: allocate port service
[    1.781065] pci_express 0000:00:1c.2cie02: allocate port service
[    1.781083] pci_express 0000:00:1c.2cie03: allocate port service
[    1.781167] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.781460] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.784526] ACPI: AC Adapter [ACAD] (on-line)
[    1.784602] ACPI: Battery Slot [BAT1] (battery absent)
[    1.784653] ACPI: Battery Slot [BAT2] (battery absent)
[    1.784730] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.784733] ACPI: Power Button (FF) [PWRF]
[    1.784796] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.784869] ACPI: Lid Switch [LID]
[    1.784918] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    1.784921] ACPI: Power Button (CM) [PWRB]
[    1.784976] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    1.784979] ACPI: Sleep Button (CM) [SLPB]
[    1.785427] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[    1.785455] processor ACPI_CPU:00: registered as cooling_device0
[    1.785459] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.790960] thermal LNXTHERM:01: registered as thermal_zone0
[    1.796657] ACPI: Thermal Zone [THRM] (47 C)
[    1.796755] isapnp: Scanning for PnP cards...
[    2.150546] isapnp: No Plug & Play device found
[    2.152068] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.152200] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[    2.153230] serial 00:07: activated
[    2.153354] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.153496] serial 0000:00:1e.3: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    2.153503] serial 0000:00:1e.3: PCI INT B disabled
[    2.154223] brd: module loaded
[    2.154565] loop: module loaded
[    2.154637] Fixed MDIO Bus: probed
[    2.154644] PPP generic driver version 2.4.2
[    2.154712] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.154744] Driver 'sd' needs updating - please use bus_type methods
[    2.154755] Driver 'sr' needs updating - please use bus_type methods
[    2.154836] ata_piix 0000:00:1f.1: version 2.12
[    2.154844] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.154884] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.154972] scsi0 : ata_piix
[    2.155056] scsi1 : ata_piix
[    2.155350] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18c0 irq 14
[    2.155353] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18c8 irq 15
[    2.324549] ata1.00: ATA-6: TOSHIBA MK6025GAS, KA200A, max UDMA/100
[    2.324552] ata1.00: 117210240 sectors, multi 16: LBA 
[    2.324596] ata1.01: ATAPI: MATSHITAUJ-840D, 1.00, max UDMA/33
[    2.332492] ata1.00: configured for UDMA/100
[    2.348541] ata1.01: configured for UDMA/33
[    2.348910] ata2: port disabled. ignoring.
[    2.349035] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6025GA KA20 PQ: 0 ANSI: 5
[    2.349138] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[    2.349157] sd 0:0:0:0: [sda] Write Protect is off
[    2.349160] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.349189] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.349251] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[    2.349267] sd 0:0:0:0: [sda] Write Protect is off
[    2.349270] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.349297] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.349301]  sda: sda1 sda2 < sda5 >
[    2.433114] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.433158] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.434873] scsi 0:0:1:0: CD-ROM            MATSHITA UJ-840D          1.00 PQ: 0 ANSI: 5
[    2.436466] sr0: scsi3-mmc drive: 62x/62x writer cd/rw xa/form2 cdda tray
[    2.436470] Uniform CD-ROM driver Revision: 3.20
[    2.436556] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    2.436599] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    2.437288] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.437309] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.437333] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.437337] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.437405] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.441326] ehci_hcd 0000:00:1d.7: debug port 1
[    2.441334] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.441360] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xc8000000
[    2.465898] ACPI: \_SB_.PCI0.DOCK - undocking
[    2.466112] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.466183] usb usb1: configuration #1 chosen from 1 choice
[    2.466216] hub 1-0:1.0: USB hub found
[    2.466226] hub 1-0:1.0: 8 ports detected
[    2.466348] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.466366] uhci_hcd: USB Universal Host Controller Interface driver
[    2.466389] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.466396] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.466400] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.466450] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.466476] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001800
[    2.466555] usb usb2: configuration #1 chosen from 1 choice
[    2.466582] hub 2-0:1.0: USB hub found
[    2.466590] hub 2-0:1.0: 2 ports detected
[    2.466681] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.466689] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.466693] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.466736] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.466769] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001820
[    2.466846] usb usb3: configuration #1 chosen from 1 choice
[    2.466873] hub 3-0:1.0: USB hub found
[    2.466880] hub 3-0:1.0: 2 ports detected
[    2.466968] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.466976] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.466980] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.467023] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.467055] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[    2.467136] usb usb4: configuration #1 chosen from 1 choice
[    2.467164] hub 4-0:1.0: USB hub found
[    2.467171] hub 4-0:1.0: 2 ports detected
[    2.467255] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.467263] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.467267] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.467322] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.467355] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[    2.467436] usb usb5: configuration #1 chosen from 1 choice
[    2.467464] hub 5-0:1.0: USB hub found
[    2.467471] hub 5-0:1.0: 2 ports detected
[    2.467614] usbcore: registered new interface driver libusual
[    2.467648] usbcore: registered new interface driver usbserial
[    2.467660] USB Serial support registered for generic
[    2.467676] usbcore: registered new interface driver usbserial_generic
[    2.467679] usbserial: USB Serial Driver core
[    2.467731] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.469940] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.469946] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.470070] mice: PS/2 mouse device common for all mice
[    2.470270] rtc_cmos 00:05: RTC can wake from S4
[    2.470308] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.470340] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.470409] device-mapper: uevent: version 1.0.3
[    2.470520] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    2.470568] device-mapper: multipath: version 1.0.5 loaded
[    2.470571] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.470652] EISA: Probing bus 0 at eisa.0
[    2.470659] Cannot allocate resource for EISA slot 1
[    2.470662] Cannot allocate resource for EISA slot 2
[    2.470665] Cannot allocate resource for EISA slot 3
[    2.470668] Cannot allocate resource for EISA slot 4
[    2.470686] EISA: Detected 0 cards.
[    2.470765] cpuidle: using governor ladder
[    2.470850] cpuidle: using governor menu
[    2.471391] TCP cubic registered
[    2.471501] NET: Registered protocol family 10
[    2.471937] lo: Disabled Privacy Extensions
[    2.472279] NET: Registered protocol family 17
[    2.472298] Bluetooth: L2CAP ver 2.11
[    2.472300] Bluetooth: L2CAP socket layer initialized
[    2.472304] Bluetooth: SCO (Voice Link) ver 0.6
[    2.472306] Bluetooth: SCO socket layer initialized
[    2.472330] Bluetooth: RFCOMM socket layer initialized
[    2.472336] Bluetooth: RFCOMM TTY layer initialized
[    2.472338] Bluetooth: RFCOMM ver 1.10
[    2.472621] Using IPI No-Shortcut mode
[    2.472692] registered taskstats version 1
[    2.472811]   Magic number: 9:692:764
[    2.472888] rtc_cmos 00:05: setting system clock to 2009-05-02 03:46:17 UTC (1241235977)
[    2.472891] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.472893] EDD information not available.
[    2.473188] Freeing unused kernel memory: 532k freed
[    2.473330] Write protecting the kernel text: 4128k
[    2.473375] Write protecting the kernel read-only data: 1532k
[    2.516756] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    2.550575] compcache: Compressed swap size set to: 385712 KB
[    2.550996] TLSF: pool: f7d82000, init_size=16384, max_size=0, grow_size=16384
[    3.355137] ohci1394 0000:06:01.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.404928] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[c8217000-c82177ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.418538] tg3.c:v3.94 (August 14, 200
[    3.418559] tg3 0000:06:08.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.460972] eth0: Tigon3 [partno(BCM95705A50) rev 3003 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:c0:9f:98:20:9d
[    3.460978] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[1]
[    3.460982] eth0: dma_rwctrl[763f0000] dma_mask[32-bit]
[    3.659198] Adding 385708k swap on /dev/ramzswap0.  Priority:100 extents:1 across:385708k
[    3.720702] Marking TSC unstable due to TSC halts in idle
[    3.749506] PM: Starting manual resume from disk
[    3.749510] PM: Resume from partition 8:5
[    3.749512] PM: Checking hibernation image.
[    3.749692] PM: Resume from disk failed.
[    3.801299] kjournald starting.  Commit interval 5 seconds
[    3.801309] EXT3-fs: mounted filesystem with ordered data mode.
[    3.936027] Clocksource tsc unstable (delta = -178972275 ns)
[    4.688153] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f00004e0df2]
[   12.950641] udev: starting version 141
[   13.177964] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input6
[   13.180613] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   13.234048] parport_pc 00:08: activated
[   13.234053] parport_pc 00:08: reported by Plug and Play ACPI
[   13.234185] parport0: PC-style at 0x378 (0x77, irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   13.279621] irda_init()
[   13.279636] NET: Registered protocol family 23
[   13.344295] ppdev: user-space parallel port driver
[   13.365684] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   13.365716] nsc-ircc, chip->init
[   13.365728] nsc-ircc, Found chip at base=0x164e
[   13.365764] nsc-ircc, driver loaded (Dag Brattli)
[   13.365769] nsc_ircc_open(), can't get iobase of 0x2f8
[   13.365808] nsc-ircc, Found chip at base=0x164e
[   13.365844] nsc-ircc, driver loaded (Dag Brattli)
[   13.365847] nsc_ircc_open(), can't get iobase of 0x2f8
[   13.366189] nsc-ircc 00:06: disabled
[   13.484170] ACPI: EC: missing confirmations, switch off interrupt mode.
[   13.579382] Linux agpgart interface v0.103
[   16.388343] intel_rng: FWH not detected
[   16.391445] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   16.408941] ieee80211_crypt: registered algorithm 'NULL'
[   16.439426] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   16.439430] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.751901] acer-wmi: Acer Laptop ACPI-WMI Extras
[   16.751920] acer-wmi: No or unsupported WMI interface, unable to load
[   16.866754] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   16.866759] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   16.866932] ipw2200 0000:06:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.867557] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   16.867612] ipw2200 0000:06:03.0: firmware: requesting ipw2200-bss.fw
[   17.193843] ipw2200: Radio Frequency Kill Switch is On:
[   17.193845] Kill switch must be turned off for wireless networking to work.
[   17.195492] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   17.195595] yenta_cardbus 0000:06:01.0: CardBus bridge found [1025:0066]
[   17.195618] yenta_cardbus 0000:06:01.0: Enabling burst memory read transactions
[   17.195625] yenta_cardbus 0000:06:01.0: Using CSCINT to route CSC interrupts to PCI
[   17.195628] yenta_cardbus 0000:06:01.0: Routing CardBus interrupts to PCI
[   17.195634] yenta_cardbus 0000:06:01.0: TI: mfunc 0x01c21b22, devctl 0x64
[   17.215548] iTCO_vendor_support: vendor-support=0
[   17.217672] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   17.217813] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   17.217909] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.238528] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   17.368992] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.369097] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   17.429153] yenta_cardbus 0000:06:01.0: ISA IRQ mask 0x0c78, PCI irq 18
[   17.429158] yenta_cardbus 0000:06:01.0: Socket status: 30000006
[   17.429163] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #07 to #08
[   17.429172] yenta_cardbus 0000:06:01.0: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[   17.429176] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x4fff: clean.
[   17.429446] yenta_cardbus 0000:06:01.0: pcmcia: parent PCI bridge Memory window: 0xc8200000 - 0xc82fffff
[   17.429450] yenta_cardbus 0000:06:01.0: pcmcia: parent PCI bridge Memory window: 0x68000000 - 0x6bffffff
[   17.430316] tifm_7xx1 0000:06:01.3: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   17.688034] intel8x0_measure_ac97_clock: measured 53932 usecs
[   17.688038] intel8x0: clocking to 48000
[   17.837498] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   17.839187] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   17.839898] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   17.840516] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   17.841301] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   17.946312] lp0: using parport0 (interrupt-driven).
[   18.057905] Adding 2441840k swap on /dev/sda5.  Priority:-1 extents:1 across:2441840k
[   18.118066] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[   18.155267] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   18.699984] EXT3 FS on sda1, internal journal
[   19.834144] type=1505 audit(1241235994.859:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2057
[   19.894105] type=1505 audit(1241235994.919:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2061
[   19.894231] type=1505 audit(1241235994.919:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2061
[   19.894283] type=1505 audit(1241235994.919:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2061
[   19.894329] type=1505 audit(1241235994.919:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2061
[   20.071256] type=1505 audit(1241235995.095:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2066
[   20.071512] type=1505 audit(1241235995.095:: operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2066
[   20.105147] type=1505 audit(1241235995.131:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2070
[   21.906829] Intel ICH Modem 0000:00:1e.3: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[   21.906858] Intel ICH Modem 0000:00:1e.3: setting latency timer to 64
[   22.260201] MC'97 0 converters and GPIO not ready (0x1)
[   31.667630] ttyS1: LSR safety check engaged!
[   31.915772] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.915777] Bluetooth: BNEP filters: protocol multicast
[   31.954033] Bridge firewalling registered
[   33.868567] pci 0000:01:00.0: power state changed by ACPI to D0
[   33.868580] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   34.070323] [drm] Initialized drm 1.1.0 20060810
[   34.173649] pci 0000:01:00.0: setting latency timer to 64
[   34.173844] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   35.024042] [drm] Setting GART location based on new memory map
[   35.025795] [drm] Loading R400 Microcode
[   35.025837] [drm] Num pipes: 2
[   35.025844] [drm] writeback test succeeded in 1 usecs
[   38.248093] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.249882] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   39.862940] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   39.862945] tg3: eth0: Flow control is on for TX and on for RX.
[   39.863192] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   50.520019] eth0: no IPv6 routers present
[   84.325528] [drm] Num pipes: 2
[   87.927360] [drm] Loading R400 Microcode
[   87.927400] [drm] Num pipes: 2
[   97.147279] synaptics: using relaxed packet validation
[  164.344376] UDF-fs: Partition marked readonly; forcing readonly mount
[  164.390128] UDF-fs INFO UDF: Mounting volume 'DVD_VIDEO_RECORDER', timestamp 2006/07/07 00:04 (1000)
[  369.283277] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[  716.068592] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  716.068600] ata1.00: BMDMA stat 0x64
[  716.068614] ata1.00: cmd c8/00:40:4f:78:1f/00:00:00:00:00/e2 tag 0 dma 32768 in
[  716.068617]          res 51/84:01:8e:78:1f/00:00:00:00:00/e2 Emask 0x10 (ATA bus error)
[  716.068624] ata1.00: status: { DRDY ERR }
[  716.068629] ata1.00: error: { ICRC ABRT }
[  716.068671] ata1: soft resetting link
[  716.248730] ata1.00: configured for UDMA/100
[  716.264742] ata1.01: configured for UDMA/33
[  716.265301] ata1: EH complete
[  716.291880] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[  716.292526] sd 0:0:0:0: [sda] Write Protect is off
[  716.292533] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  716.311742] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  716.318489] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[  716.335847] sd 0:0:0:0: [sda] Write Protect is off
[  716.335854] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  716.374861] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1571.165810] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[ 1571.165818] ata1.00: BMDMA stat 0x64
[ 1571.165832] ata1.00: cmd ca/00:00:df:64:34/00:00:00:00:00/e6 tag 0 dma 131072 out
[ 1571.165835]          res 51/84:00:de:65:34/00:00:00:00:00/e6 Emask 0x10 (ATA bus error)
[ 1571.165842] ata1.00: status: { DRDY ERR }
[ 1571.165847] ata1.00: error: { ICRC ABRT }
[ 1571.165890] ata1: soft resetting link
[ 1571.344879] ata1.00: configured for UDMA/100
[ 1571.360747] ata1.01: configured for UDMA/33
[ 1571.361327] ata1: EH complete
[ 1571.368388] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[ 1571.371604] sd 0:0:0:0: [sda] Write Protect is off
[ 1571.371610] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1571.374877] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1571.376808] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[ 1571.377472] sd 0:0:0:0: [sda] Write Protect is off
[ 1571.377478] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1571.378086] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 3582.641487] ttyS1: LSR safety check engaged!
[ 3582.641507] type=1503 audit(1241239559.439:10): operation="capable" name="sys_admin" pid=7992 profile="/usr/sbin/cupsd"
[ 3583.008339] ppdev0: registered pardevice
[ 3583.056452] ppdev0: unregistered pardevice
[ 3584.043075] ppdev0: registered pardevice
[ 3584.092217] ppdev0: unregistered pardevice
[ 3584.184186] ppdev0: registered pardevice
[ 3584.232059] ppdev0: unregistered pardevice
[ 3674.352719] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[ 3674.352728] ata1.00: BMDMA stat 0x64
[ 3674.352742] ata1.00: cmd ca/00:10:87:4b:9f/00:00:00:00:00/e2 tag 0 dma 8192 out
[ 3674.352745]          res 11/84:00:67:4a:9f/00:00:00:00:00/e2 Emask 0x3 (HSM violation)
[ 3674.352752] ata1.00: status: { ERR }
[ 3674.352757] ata1.00: error: { ICRC ABRT }
[ 3674.352800] ata1: soft resetting link
[ 3674.532610] ata1.00: configured for UDMA/100
[ 3674.548606] ata1.01: configured for UDMA/33
[ 3674.549039] ata1: EH complete
[ 3674.550438] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[ 3674.553117] sd 0:0:0:0: [sda] Write Protect is off
[ 3674.553125] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 3674.554153] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 3674.555015] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[ 3674.555050] sd 0:0:0:0: [sda] Write Protect is off
[ 3674.555055] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 3674.555110] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

i have provided information which will help you support me.

---

