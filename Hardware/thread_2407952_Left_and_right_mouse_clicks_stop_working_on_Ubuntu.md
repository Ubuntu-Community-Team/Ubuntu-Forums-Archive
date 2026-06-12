---
title: "Left and right mouse clicks stop working on Ubuntu 18.04"
date: 2018-12-11
forum: Hardware
---

### Post by ramseyrt on 2018-12-11
Hello,

My ability to mouse click (left, right, middle) stops working after attempting to click anything using the touchpad. So long as I don't attempt to click using the touchpad, my external USB mouse works fine.  Once I've attempted to click something with the touchpad, I loose the ability to click anything using either device.  The only way I've been able to recover is by rebooting the system (which is hard to do when you can't click on anything).

I'm running a fresh install of Ubuntu 18.04 on a Samsung Chromebook 3.  The OS install went well and I completed the OS update process without issue.

Thanks in advance,

Rob

**Kernel Info**
```

Linux chromebook 4.15.0-42-generic #45-Ubuntu SMP Thu Nov 15 19:32:57 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

**CPU Info**
```

Architecture:        x86_64CPU op-mode(s):      32-bit, 64-bit
Byte Order:          Little Endian
CPU(s):              2
On-line CPU(s) list: 0,1
Thread(s) per core:  1
Core(s) per socket:  2
Socket(s):           1
NUMA node(s):        1
Vendor ID:           GenuineIntel
CPU family:          6
Model:               76
Model name:          Intel(R) Celeron(R) CPU  N3060  @ 1.60GHz
Stepping:            4
CPU MHz:             1027.021
CPU max MHz:         2480.0000
CPU min MHz:         480.0000
BogoMIPS:            3200.00
Virtualization:      VT-x
L1d cache:           24K
L1i cache:           32K
L2 cache:            1024K
NUMA node0 CPU(s):   0,1
Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp
lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor
ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes rdrand lahf_lm 3dnowprefetch epb pti ibrs ibpb stibp
tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms dtherm ida arat

```

**Memory Info**
```

MemTotal:        3984432 kB
MemFree:         1452944 kB
MemAvailable:    2621216 kB
Buffers:           62636 kB
Cached:          1443064 kB
SwapCached:            0 kB
Active:          1522340 kB
Inactive:         827488 kB
Active(anon):     845368 kB
Inactive(anon):   158936 kB
Active(file):     676972 kB
Inactive(file):   668552 kB
Unevictable:          32 kB
Mlocked:              32 kB
SwapTotal:        688128 kB
SwapFree:         688128 kB
Dirty:                56 kB
Writeback:             0 kB
AnonPages:        844244 kB
Mapped:           217428 kB
Shmem:            160180 kB
Slab:              98340 kB
SReclaimable:      63340 kB
SUnreclaim:        35000 kB
KernelStack:        6624 kB
PageTables:        30248 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     2680344 kB
Committed_AS:    3483180 kB
VmallocTotal:   34359738367 kB
VmallocUsed:           0 kB
VmallocChunk:          0 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
ShmemHugePages:        0 kB
ShmemPmdMapped:        0 kB
CmaTotal:              0 kB
CmaFree:               0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      122580 kB
DirectMap2M:     4016128 kB

```

**PCI Info**
```

00:00.0 Host bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register (rev 35)
00:02.0 VGA compatible controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller (rev 35)
00:0b.0 Signal processing controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller (rev 35)
00:10.0 SD Host controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series MMC Controller (rev 35)
00:12.0 SD Host controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SD Controller (rev 35)
00:14.0 USB controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller (rev 35)
00:1b.0 Audio device: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series High Definition Audio Controller (rev 35)
00:1c.0 PCI bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #1 (rev 35)
00:1c.2 PCI bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #3 (rev 35)
00:1f.0 ISA bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU (rev 35)
02:00.0 Network controller: Intel Corporation Wireless 7265 (rev 59)

```

**USB Info**
```

Bus 002 Device 002: ID 13fe:6000 Kingston Technology Company Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:0a2a Intel Corp. 
Bus 001 Device 002: ID 2232:1073 Silicon Motion 
Bus 001 Device 004: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

**Module Info**
```

Module                  Size  Used by
uas                    24576  0
usb_storage            69632  2 uas
ccm                    20480  9
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 usbhid,hid_generic
rfcomm                 77824  4
cmac                   16384  1
bnep                   20480  2
snd_soc_sst_cht_bsw_rt5645    20480  0
nls_iso8859_1          16384  1
intel_rapl             20480  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             212992  0
joydev                 24576  0
kvm                   598016  1 kvm_intel
irqbypass              16384  1 kvm
punit_atom_debug       16384  0
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
arc4                   16384  2
aesni_intel           188416  8
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
iwlmvm                364544  0
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
mac80211              778240  1 iwlmvm
intel_cstate           20480  0
input_leds             16384  0
serio_raw              16384  0
snd_hda_codec_hdmi     49152  1
snd_intel_sst_acpi     16384  1
snd_soc_rt5645        143360  2 snd_soc_sst_cht_bsw_rt5645
snd_intel_sst_core     53248  1 snd_intel_sst_acpi
iwlwifi               282624  1 iwlmvm
snd_soc_rt5640        118784  0
btusb                  45056  0
snd_soc_sst_atom_hifi2_platform   102400  3 snd_intel_sst_core
snd_soc_acpi           16384  2 snd_intel_sst_acpi,snd_soc_sst_cht_bsw_rt5645
btrtl                  16384  1 btusb
snd_hda_intel          40960  1
snd_soc_rl6231         16384  2 snd_soc_rt5640,snd_soc_rt5645
btbcm                  16384  1 btusb
snd_soc_acpi_intel_match    20480  1 snd_intel_sst_acpi
btintel                16384  1 btusb
snd_hda_codec         126976  2 snd_hda_codec_hdmi,snd_hda_intel
bluetooth             548864  33 btrtl,btintel,btbcm,bnep,btusb,rfcomm
snd_hda_core           81920  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_soc_core          241664  4 snd_soc_rt5640,snd_soc_sst_atom_hifi2_platform,snd_soc_rt5645,snd_soc_sst_cht_bsw_rt5645
cfg80211              622592  3 iwlmvm,iwlwifi,mac80211
uvcvideo               86016  0
snd_compress           20480  1 snd_soc_core
snd_hwdep              20480  1 snd_hda_codec
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_seq_midi           16384  0
snd_pcm                98304  10 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_soc_rt5640,snd_soc_sst_atom_hifi2_platform,snd_soc_core,snd_soc_rt5645,snd_hda_core,snd_soc_sst_cht_bsw_rt5645,snd_pcm_dmaengine
ecdh_generic           24576  2 bluetooth
snd_seq_midi_event     16384  1 snd_seq_midi
shpchp                 36864  0
lpc_ich                24576  0
snd_rawmidi            32768  1 snd_seq_midi
processor_thermal_device    16384  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
atmel_mxt_ts           45056  0
videobuf2_vmalloc      16384  2 atmel_mxt_ts,uvcvideo
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_timer              32768  2 snd_seq,snd_pcm
cros_ec_core           16384  0
videobuf2_v4l2         24576  2 atmel_mxt_ts,uvcvideo
videobuf2_core         40960  3 atmel_mxt_ts,videobuf2_v4l2,uvcvideo
videodev              184320  4 videobuf2_core,atmel_mxt_ts,videobuf2_v4l2,uvcvideo
dw_dmac                16384  0
int3403_thermal        16384  0
dw_dmac_core           24576  1 dw_dmac
8250_dw                16384  0
snd                    81920  14 snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_compress,snd_soc_sst_atom_hifi2_platform,snd_soc_core,snd_pcm,snd_rawmidi
media                  40960  2 videodev,uvcvideo
spi_pxa2xx_platform    24576  0
int340x_thermal_zone    16384  2 int3403_thermal,processor_thermal_device
int3400_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
pwm_lpss_platform      16384  0
pwm_lpss               16384  1 pwm_lpss_platform
soundcore              16384  1 snd
mac_hid                16384  0
sch_fq_codel           20480  5
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
mmc_block              36864  3
i915                 1617920  10
i2c_algo_bit           16384  1 i915
drm_kms_helper        172032  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   401408  5 drm_kms_helper,i915
sdhci_pci              32768  0
sdhci                  49152  1 sdhci_pci
video                  45056  1 i915

```

**/proc/bus/input/devices**
```

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0C09:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1


I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0


I: Bus=0011 Vendor=0001 Product=0001 Version=ab83
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input2
U: Uniq=
H: Handlers=sysrq kbd event2 leds 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7


I: Bus=0003 Vendor=046d Product=c534 Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:14.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/0003:046D:C534.0001/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 leds 
B: PROP=0
B: EV=120013
B: KEY=1000000000007 ff800000000007ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=1f


I: Bus=0003 Vendor=046d Product=c534 Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:14.0-2/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.1/0003:046D:C534.0002/input/input4
U: Uniq=
H: Handlers=kbd mouse0 event4 
B: PROP=0
B: EV=1f
B: KEY=3007f 0 0 483ffff17aff32d bf54444600000000 ffff0001 130f938b17c000 677bfad941dfed 9ed68000004400 10000002
B: REL=1c3
B: ABS=100000000
B: MSC=10


I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0


I: Bus=0003 Vendor=2232 Product=1073 Version=0013
N: Name="Real HD WebCam: Real HD WebCam"
P: Phys=usb-0000:00:14.0-3/button
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0


I: Bus=0018 Vendor=0000 Product=0000 Version=0000
N: Name="Atmel maXTouch Touchpad"
P: Phys=i2c-1-004a/input0
S: Sysfs=/devices/pci0000:00/808622C1:05/i2c-1/i2c-ATML0000:00/input/input7
U: Uniq=
H: Handlers=mouse1 event7 
B: PROP=5
B: EV=b
B: KEY=e520 10000 0 0 0 0
B: ABS=ef1800001000003


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input8
U: Uniq=
H: Handlers=event8 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=7"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input9
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=8"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input10
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="chtrt5650 Headset"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/808622A8:00/cht-bsw-rt5645/sound/card1/input11
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=23
B: KEY=f 0 0 0 0
B: SW=14

```

**xinput test for USB mouse**
```

root@chromebook:~# xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Atmel maXTouch Touchpad                 	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Logitech USB Receiver                   	id=8	[slave  keyboard (3)]
    &#8627; Real HD WebCam: Real HD WebCam          	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; Logitech USB Receiver                   	id=13	[slave  keyboard (3)]
root@chromebook:~# xinput --test 9
motion a[0]=745 
motion a[1]=420 
button press   1 
button release 1 
motion a[1]=421 
motion a[0]=745 
button press   2 
button release 2 
motion a[0]=745 
motion a[1]=420 
motion a[0]=746 
button press   3 
motion a[0]=745 
button release 3 

```

**xinput test for touchpad**
```

root@chromebook:~# xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Atmel maXTouch Touchpad                 	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Logitech USB Receiver                   	id=8	[slave  keyboard (3)]
    &#8627; Real HD WebCam: Real HD WebCam          	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; Logitech USB Receiver                   	id=13	[slave  keyboard (3)]
root@chromebook:~# xinput --test 11
motion a[0]=1894 a[1]=81 
motion a[0]=1892 a[1]=82 
motion a[0]=1890 
motion a[0]=1889 
motion a[0]=1888 
motion a[0]=1888 
button press   1 
motion a[0]=1887 
motion a[1]=84 
motion a[1]=85 
motion a[1]=86 
motion a[0]=1886 a[1]=88 
motion a[0]=1886 a[1]=88 
motion a[0]=1885 a[1]=88 
motion a[0]=1884 
motion a[0]=1882 
motion a[1]=88 
motion a[0]=1883 a[1]=87 
motion a[1]=86 
motion a[1]=86 
motion a[1]=86 
motion a[1]=85 
motion a[1]=85 
motion a[1]=84 
motion a[0]=1882 
motion a[0]=1882 
motion a[1]=85 
motion a[0]=1882 
motion a[0]=1883 
motion a[0]=1883 
motion a[0]=1884 
motion a[0]=1884 
motion a[0]=1884 
motion a[0]=1885 
motion a[0]=1885 
motion a[0]=1886 
motion a[0]=1886 
motion a[0]=1886 a[1]=84 
motion a[0]=1887 a[1]=84 
motion a[0]=1887 a[1]=84 
motion a[1]=82 
motion a[0]=1888 a[1]=82 
motion a[1]=81 
motion a[1]=80 
motion a[1]=80 
motion a[1]=80 
motion a[1]=79 
motion a[1]=79 
motion a[1]=78 
motion a[1]=77 
motion a[1]=76 
motion a[1]=75 
motion a[1]=75 
motion a[1]=74 
motion a[1]=74 
motion a[1]=73 
motion a[1]=72 
motion a[1]=72 
motion a[1]=72 
motion a[1]=71 
motion a[1]=71 
motion a[0]=1888 
motion a[0]=1888 
motion a[0]=1889 
motion a[0]=1889 
motion a[1]=70 

```

---

