---
title: "Webcam issues on Xubuntu 16.04 on Dell Inspiron 3437 with Microdia Integrated Webcam"
date: 2016-04-29
forum: Hardware
---

### Post by mar.esther23 on 2016-04-29
[COLOR=#000000]I'm trying to use Xubuntu 16.04 (64-bit) on a [Dell Inspiron 3437]("http://www.ubuntu.com/certification/hardware/201304-13210/") with a Microdia Integrated Webcam, however it does not recognize the webcam or the microphone. It used to work with [/COLOR][COLOR=#000000]Xubuntu 14.04 (32-bit).[/COLOR]

Cheese returns a "Device not found message" and I'm already using all the additional drivers my system can detect.

**lsusb** returns:
```
Bus 001 Device 007: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

**lsmod** returns:
```

Module                  Size  Used by
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
bnep                   20480  2
dell_led               16384  0
snd_hda_codec_hdmi     53248  1
arc4                   16384  2
intel_rapl             20480  0
ath9k                 143360  0
x86_pkg_temp_thermal    16384  0
ath9k_common           36864  1 ath9k
snd_hda_codec_realtek    81920  1
snd_soc_rt5640        114688  0
intel_powerclamp       16384  0
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_hda_intel          36864  7
ath9k_hw              466944  2 ath9k_common,ath9k
snd_soc_core          212992  1 snd_soc_rt5640
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_compress           20480  1 snd_soc_core
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
ac97_bus               16384  1 snd_soc_core
coretemp               16384  0
snd_pcm_dmaengine      16384  1 snd_soc_core
kvm_intel             172032  0
mac80211              737280  1 ath9k
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
kvm                   536576  1 kvm_intel
ath3k                  20480  0
btusb                  45056  0
cfg80211              565248  4 ath,ath9k_common,ath9k,mac80211
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
irqbypass              16384  1 kvm
snd_pcm               106496  8 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
btintel                16384  1 btusb
bluetooth             520192  25 bnep,ath3k,btbcm,btrtl,btusb,btintel
snd_seq_midi           16384  0
dell_wmi               16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
dell_laptop            20480  0
sparse_keymap          16384  1 dell_wmi
snd_rawmidi            32768  1 snd_seq_midi
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
aesni_intel           167936  2
aes_x86_64             20480  1 aesni_intel
dcdbas                 16384  1 dell_laptop
lrw                    16384  1 aesni_intel
dell_smm_hwmon         16384  0
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
joydev                 20480  0
input_leds             16384  0
serio_raw              16384  0
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  26 snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
soundcore              16384  1 snd
dw_dmac                16384  0
dw_dmac_core           24576  1 dw_dmac
elan_i2c               36864  0
mei_me                 36864  0
shpchp                 36864  0
dell_rbtn              16384  0
snd_soc_sst_acpi       16384  0
8250_dw                16384  0
i2c_designware_platform    16384  0
spi_pxa2xx_platform    24576  0
mei                    98304  1 mei_me
i2c_designware_core    20480  1 i2c_designware_platform
lpc_ich                24576  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
i915                 1208320  4
i2c_algo_bit           16384  1 i915
drm_kms_helper        139264  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   360448  5 i915,drm_kms_helper
ahci                   36864  3
psmouse               126976  0
r8169                  81920  0
libahci                32768  1 ahci
mii                    16384  1 r8169
wmi                    20480  2 dell_led,dell_wmi
video                  40960  3 i915,dell_wmi,dell_laptop
sdhci_acpi             16384  0
sdhci                  45056  1 sdhci_acpi
i2c_hid                20480  0
hid                   118784  1 i2c_hid
fjes                   28672  0

```

Thanks for your help.

---

### Post by DuckHook on 2016-04-29
I have edited your post replacing the *QUOTE* tags with *CODE* tags for easier reading.

Re: Your issue.

Many users are reporting breakage on peripherals with a new Xenial install. The fact of the matter is that Xenial will not grow out of its teething pains until the first point release (16.04.1) in about three month's time. Since this is a new install for you (necessary in going from 32-bit to 64-bit), I recommend that you go back to Trusty (14.04) as a known stable quantity until the first point release has been issued.

---

### Post by jay_bowles2 on 2016-04-29
To be honest I wonder why this is happening. Ubuntu is not a new player now and releasing something that clearly still has a lot of issues is bad for it's image. Why release? Sticking to the regular upgrade cycle, especially on a LTS really isn't working. IMHO this should still be a beta release....

---

### Post by DuckHook on 2016-04-29
I'm just a regular user like you and no apologist for Canonical. The wisdom of sticking to their preset release schedule is a hotly debated recurring topic that is best discussed in the *Cafe* area of this forum.

For your issue, it may help to post some additional data. Neither lsusb nor lsmod shows anything useful. So please do:```
sudo lshw -sanitize
```...and post back results between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by jay_bowles2 on 2016-04-29
I noticed this bug which may or may not be related:[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1574079](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1574079)

I mention it only as it affects usb soundcards and could be relevant.

My USB soundcard is affected by this bug and I noticed that Kubuntu had no problem although the driver manager in setting just hung?! Maybe this was disabled by default on release because of this bug?? I am only surmising... but it is strange that Kubuntu was the only *buntu I have tried that plays nicely.

---

### Post by mar.esther23 on 2016-04-29
Thanks for your replies. ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo lshw -sanitize[/FONT][/COLOR]
```[COLOR=#000000] returns:[/COLOR]

```

computer                  
    description: Computer
    width: 64 bits
    capabilities: smbios-2.7 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 5875MiB
     *-cpu
          product: Intel(R) Core(TM) i5-4200U CPU @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1600MHz
          capacity: 2600MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts cpufreq
     *-display
          description: VGA compatible controller
          product: Haswell-ULT Integrated Graphics Controller
          vendor: Intel Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: 09
          width: 64 bits
          clock: 33MHz
          capabilities: msi pm vga_controller bus_master cap_list rom
          configuration: driver=i915 latency=0
          resources: irq:43 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
     *-multimedia:0
          description: Audio device
          product: Haswell-ULT HD Audio Controller
          vendor: Intel Corporation
          physical id: 3
          bus info: pci@0000:00:03.0
          version: 09
          width: 64 bits
          clock: 33MHz
          capabilities: pm msi pciexpress bus_master cap_list
          configuration: driver=snd_hda_intel latency=0
          resources: irq:44 memory:f7e14000-f7e17fff
     *-usb:0
          description: USB controller
          product: 8 Series USB xHCI HC
          vendor: Intel Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          version: 04
          width: 64 bits
          clock: 33MHz
          capabilities: pm msi xhci bus_master cap_list
          configuration: driver=xhci_hcd latency=0
          resources: irq:40 memory:f7e00000-f7e0ffff
        *-usbhost:0
             product: xHCI Host Controller
             vendor: Linux 4.4.0-21-generic xhci-hcd
             physical id: 0
             bus info: usb@3
             logical name: usb3
             version: 4.04
             capabilities: usb-3.00
             configuration: driver=hub slots=4 speed=5000Mbit/s
        *-usbhost:1
             product: xHCI Host Controller
             vendor: Linux 4.4.0-21-generic xhci-hcd
             physical id: 1
             bus info: usb@2
             logical name: usb2
             version: 4.04
             capabilities: usb-2.00
             configuration: driver=hub slots=9 speed=480Mbit/s
     *-communication
          description: Communication controller
          product: 8 Series HECI #0
          vendor: Intel Corporation
          physical id: 16
          bus info: pci@0000:00:16.0
          version: 04
          width: 64 bits
          clock: 33MHz
          capabilities: pm msi bus_master cap_list
          configuration: driver=mei_me latency=0
          resources: irq:45 memory:f7e1d000-f7e1d01f
     *-multimedia:1
          description: Audio device
          product: 8 Series HD Audio Controller
          vendor: Intel Corporation
          physical id: 1b
          bus info: pci@0000:00:1b.0
          version: 04
          width: 64 bits
          clock: 33MHz
          capabilities: pm msi pciexpress bus_master cap_list
          configuration: driver=snd_hda_intel latency=0
          resources: irq:46 memory:f7e10000-f7e13fff
     *-pci:0
          description: PCI bridge
          product: 8 Series PCI Express Root Port 1
          vendor: Intel Corporation
          physical id: 1c
          bus info: pci@0000:00:1c.0
          version: e4
          width: 32 bits
          clock: 33MHz
          capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:16 ioport:2000(size=4096) memory:df200000-df3fffff ioport:df400000(size=2097152)
     *-pci:1
          description: PCI bridge
          product: 8 Series PCI Express Root Port 3
          vendor: Intel Corporation
          physical id: 1c.2
          bus info: pci@0000:00:1c.2
          version: e4
          width: 32 bits
          clock: 33MHz
          capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:18 ioport:3000(size=4096) memory:f7d00000-f7dfffff ioport:df600000(size=2097152)
        *-network
             description: Wireless interface
             product: QCA9565 / AR9565 Wireless Network Adapter
             vendor: Qualcomm Atheros
             physical id: 0
             bus info: pci@0000:06:00.0
             logical name: wlp6s0
             version: 01
             serial: [REMOVED]
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
             configuration: broadcast=yes driver=ath9k driverversion=4.4.0-21-generic firmware=N/A ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
             resources: irq:18 memory:f7d00000-f7d7ffff memory:f7d80000-f7d8ffff
     *-pci:2
          description: PCI bridge
          product: 8 Series PCI Express Root Port 4
          vendor: Intel Corporation
          physical id: 1c.3
          bus info: pci@0000:00:1c.3
          version: e4
          width: 32 bits
          clock: 33MHz
          capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:19 ioport:e000(size=4096) memory:f7c00000-f7cfffff ioport:df800000(size=2097152)
        *-network
             description: Ethernet interface
             product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 0
             bus info: pci@0000:07:00.0
             logical name: enp7s0
             version: 08
             serial: [REMOVED]
             size: 10Mbit/s
             capacity: 100Mbit/s
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-2_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
             resources: irq:42 ioport:e000(size=256) memory:f7c04000-f7c04fff memory:f7c00000-f7c03fff
     *-usb:1
          description: USB controller
          product: 8 Series USB EHCI #1
          vendor: Intel Corporation
          physical id: 1d
          bus info: pci@0000:00:1d.0
          version: 04
          width: 32 bits
          clock: 33MHz
          capabilities: pm debug ehci bus_master cap_list
          configuration: driver=ehci-pci latency=0
          resources: irq:23 memory:f7e1b000-f7e1b3ff
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 4.4.0-21-generic ehci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 4.04
             capabilities: usb-2.00
             configuration: driver=hub slots=2 speed=480Mbit/s
           *-usb
                description: USB hub
                vendor: Intel Corp.
                physical id: 1
                bus info: usb@1:1
                version: 0.04
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480Mbit/s
              *-usb
                   description: Bluetooth wireless interface
                   vendor: Atheros Communications, Inc.
                   physical id: 6
                   bus info: usb@1:1.6
                   version: 0.02
                   capabilities: bluetooth usb-1.10
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
     *-isa
          description: ISA bridge
          product: 8 Series LPC Controller
          vendor: Intel Corporation
          physical id: 1f
          bus info: pci@0000:00:1f.0
          version: 04
          width: 32 bits
          clock: 33MHz
          capabilities: isa bus_master cap_list
          configuration: driver=lpc_ich latency=0
          resources: irq:0
     *-storage
          description: SATA controller
          product: 8 Series SATA Controller 1 [AHCI mode]
          vendor: Intel Corporation
          physical id: 1f.2
          bus info: pci@0000:00:1f.2
          version: 04
          width: 32 bits
          clock: 66MHz
          capabilities: storage msi pm ahci_1.0 bus_master cap_list
          configuration: driver=ahci latency=0
          resources: irq:41 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7e1a000-f7e1a7ff
     *-serial UNCLAIMED
          description: SMBus
          product: 8 Series SMBus Controller
          vendor: Intel Corporation
          physical id: 1f.3
          bus info: pci@0000:00:1f.3
          version: 04
          width: 64 bits
          clock: 33MHz
          configuration: latency=0
          resources: memory:f7e19000-f7e190ff ioport:f040(size=32)
     *-scsi:0
          physical id: 4
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST1000LM024 HN-M
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0004
             serial: [REMOVED]
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=55840a5a
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 111GiB
                capacity: 111GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2016-04-28 08:19:15 filesystem=ext4 lastmountpoint=/ modified=2016-04-28 23:38:42 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-04-28 10:21:03 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 12GiB
                capacity: 12GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 12GiB
                   capabilities: nofs
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                logical name: /home
                version: 1.0
                serial: [REMOVED]
                size: 807GiB
                capacity: 807GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-05-29 00:00:14 filesystem=ext4 lastmountpoint=/home modified=2016-04-28 23:38:53 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2016-04-28 23:38:53 state=mounted
     *-scsi:1
          physical id: 5
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD+-RW GU70N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: A104
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc

```

---

### Post by DuckHook on 2016-04-30
It's not a driver issue. Your system simply does not see your camera.

My 16.04 expertise is shallow, not least because I have only started my own explorations of Xenial. You can bump this thread every 24 hrs to attract the attention of a guru, but I'm out of ideas, with the exception of the one already given: reinstalling 14.04. Trusty is stable and proven, and you know that it works for your equipment. You can try out Xenial again when it reaches its first point release and then on a LiveUSB first, to make sure everything works, before actually installing it.

The best of luck either way you decide to go.

---

### Post by gordintoronto on 2016-04-30
It's also possible that your webcam stopped working about the same time as you tried 16.04. Unlikely coincidence, but I have seen such things many times in the forums.

---

### Post by mar.esther23 on 2016-04-30
Thanks for your help. I think I will wait for the first point update and hope that improves my situation.

---

