---
title: "Ubuntu 22.04.3 LTS (Dell XPS 9730) sound not working"
date: 2023-11-16
forum: Hardware
---

### Post by rkaalma on 2023-11-16
Hello!

I can't get the speakers / sound to work on my Dell XPS 9730. At first it was showing only "Dummy output" and after going through countless articles here and askUbuntu I managed to get it to "HDMI / DisplayPort - Built-in Audio" - I think this was a combined result of disabling "Secure Boot" and "Fastboot" in BIOS and adding the following lines at the end of "/etc/modprobe.d/alsa-base.conf" file:

```
options snd-hda-intel model=generic
options snd-hda-intel dmic_detect=0
```

So, currently I have:
1) Dell XPS 9730 laptop
2) Secure Boot disabled
3) Fastboot disabled
4) Ubuntu 22.04.3 LTS
5) sudo apt-get update && apt-get upgrade - done
6) Only "HDMI / DisplayPort - Built-in Audio" as available output device in settings

Here are some commonly requested results (from other threads) for troubleshooting:

```
$ sudo uname -a
Linux dellis 6.2.0-36-generic #37~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Mon Oct  9 15:34:04 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
```

```
$ sudo lspci -v | grep -A7 -i "audio"
0000:00:1f.3 Multimedia audio controller: Intel Corporation Device 51ca (rev 01)
    Subsystem: Dell Device 0bdb
    Flags: bus master, fast devsel, latency 64, IRQ 231, IOMMU group 16
    Memory at 6491250000 (64-bit, non-prefetchable) [size=16K]
    Memory at 6491000000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] Vendor Specific Information: Len=14 <?>
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
--
0000:01:00.1 Audio device: NVIDIA Corporation Device 22bc (rev a1)
    Subsystem: Dell Device 0bdb
    Flags: bus master, fast devsel, latency 0, IRQ 17, IOMMU group 17
    Memory at ad000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
```

```
$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****card 0: PCH [HDA Intel PCH], device 3: Generic Digital [Generic Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
$ sudo aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
samplerate
    Rate Converter Plugin Using Samplerate Library
speexrate
    Rate Converter Plugin Using Speex Resampler
jack
    JACK Audio Connection Kit
oss
    Open Sound System
pulse
    PulseAudio Sound Server
upmix
    Plugin for channel upmix (4,6,8)
vdownmix
    Plugin for channel downmix (stereo) with a simple spacialization
hw:CARD=PCH,DEV=3
    HDA Intel PCH, Generic Digital
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=3
    HDA Intel PCH, Generic Digital
    Hardware device with all software conversions
hdmi:CARD=PCH,DEV=0
    HDA Intel PCH, Generic Digital
    HDMI Audio Output
dmix:CARD=PCH,DEV=3
    HDA Intel PCH, Generic Digital
    Direct sample mixing device
usbstream:CARD=PCH
    HDA Intel PCH
    USB Stream Output
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 3
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 3
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 1
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, HDMI 2
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 3
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 3
    Direct sample mixing device
usbstream:CARD=NVidia
    HDA NVidia
    USB Stream Output
```

```
$ sudo inxi -xxAAudio:
  Device-1: Intel vendor: Dell driver: snd_hda_intel v: kernel
    bus-ID: 0000:00:1f.3 chip-ID: 8086:51ca
  Device-2: NVIDIA vendor: Dell driver: snd_hda_intel v: kernel
    bus-ID: 0000:01:00.1 chip-ID: 10de:22bc
  Sound Server-1: ALSA v: k6.2.0-36-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
```

```
$ sudo inxi -AC --no-host
CPU:
  Info: 14-core (6-mt/8-st) model: 13th Gen Intel Core i9-13900H bits: 64
    type: MST AMCP cache: L2: 11.5 MiB
  Speed (MHz): avg: 2165 min/max: 400/5200:5400:4100 cores: 1: 654 2: 3000
    3: 774 4: 3000 5: 701 6: 3000 7: 771 8: 3000 9: 471 10: 3000 11: 400
    12: 3000 13: 3000 14: 543 15: 3000 16: 3000 17: 3000 18: 3000 19: 3000
    20: 3000
Audio:
  Device-1: Intel driver: snd_hda_intel
  Device-2: NVIDIA driver: snd_hda_intel
  Sound Server-1: ALSA v: k6.2.0-36-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
```

```
$ sudo lshw -c multimedia
  *-multimedia              
       description: Audio device
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0.1
       bus info: pci@0000:01:00.1
       logical name: card1
       logical name: /dev/snd/controlC1
       logical name: /dev/snd/hwC1D0
       logical name: /dev/snd/pcmC1D3p
       logical name: /dev/snd/pcmC1D7p
       logical name: /dev/snd/pcmC1D8p
       logical name: /dev/snd/pcmC1D9p
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:17 memory:ad000000-ad003fff
  *-usb:0
       description: Video
       product: Integrated_Webcam_HD: Integrate
       vendor: CN0679GY8LG00318B27JA00
       physical id: 6
       bus info: usb@1:6
       logical name: input15
       logical name: /dev/input/event4
       logical name: input16
       logical name: /dev/input/event5
       version: 22.81
       serial: SN0001
       capabilities: usb-2.01 usb
       configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
  *-multimedia
       description: Multimedia audio controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 1f.3
       bus info: pci@0000:00:1f.3
       logical name: card0
       logical name: /dev/snd/controlC0
       logical name: /dev/snd/hwC0D2
       logical name: /dev/snd/pcmC0D3p
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=64
       resources: iomemory:640-63f iomemory:640-63f irq:231 memory:6491250000-6491253fff memory:6491000000-64910fffff
```

```
$ sudo hwinfo --sound
26: PCI 1f.3: 0401 Multimedia audio controller                  
  [Created at pci.386]
  Unique ID: nS1_.9z+chhAoCs6
  SysFS ID: /devices/pci0000:00/0000:00:1f.3
  SysFS BusID: 0000:00:1f.3
  Hardware Class: sound
  Model: "Intel Multimedia audio controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x51ca 
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x0bdb 
  Revision: 0x01
  Driver: "snd_hda_intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0x6491250000-0x6491253fff (rw,non-prefetchable)
  Memory Range: 0x6491000000-0x64910fffff (rw,non-prefetchable)
  IRQ: 231 (161 events)
  Module Alias: "pci:v00008086d000051CAsv00001028sd00000BDBbc04sc01i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Driver Info #1:
    Driver Status: snd_sof_pci_intel_tgl is active
    Driver Activation Cmd: "modprobe snd_sof_pci_intel_tgl"
  Config Status: cfg=new, avail=yes, need=no, active=unknown


37: PCI 100.1: 0403 Audio device
  [Created at pci.386]
  Unique ID: NXNs._geyMh7Axu0
  Parent ID: vSkL.sYs7F72qFuA
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.1
  SysFS BusID: 0000:01:00.1
  Hardware Class: sound
  Model: "nVidia Audio device"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x22bc 
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x0bdb 
  Revision: 0xa1
  Driver: "snd_hda_intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xad000000-0xad003fff (rw,non-prefetchable)
  IRQ: 17 (337 events)
  Module Alias: "pci:v000010DEd000022BCsv00001028sd00000BDBbc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (PCI bridge)
```

```
$ sudo fwupdmgr get-devices
XPS 17 9730
&#9474;
&#9500;&#9472;VEN 04F3:00 04F3:32AA:
&#9474;     Device ID:          cc9c1b47c3126a46379087db3bf18fa324f317ae
&#9474;     Summary:            Touchpad
&#9474;     Current version:    0x0001
&#9474;     Bootloader Version: 0x0001
&#9474;     Vendor:             HIDRAW:0x04F3
&#9474;     GUIDs:              6a4cc925-e7b4-5626-a63e-9748c5155e7e &#8592; HIDRAW\VEN_04F3&DEV_32AA&REV_00
&#9474;                         8e5cc6d9-e582-5ca2-ae2b-4813aac2a457 &#8592; HIDRAW\VEN_04F3&DEV_32AA
&#9474;                         3b356bf8-a977-584a-a75c-723e88f8b4a8 &#8592; HIDRAW\VEN_04F3&DEV_32AA&MOD_001F
&#9474;                         4f9fe0ae-f26e-5c1d-8a4e-a7506fb02f96 &#8592; ELANTP\ICTYPE_13
&#9474;                         a88064c8-6da5-5b83-92ce-db2889f77ac3 &#8592; ELANTP\ICTYPE_13&MOD_001F
&#9474;     Device Flags:       • Internal device
&#9474;                         • Updatable
&#9474;   
&#9500;&#9472;Fingerprint Sensor:
&#9474;     Device ID:          d432baa2162a32c1554ef24bd8281953b9d07c11
&#9474;     Summary:            Match-On-Chip fingerprint sensor
&#9474;     Current version:    01000274
&#9474;     Vendor:             Goodix (USB:0x27C6)
&#9474;     Install Duration:   10 seconds
&#9474;     Serial Number:      UID42E36CF0_XXXX_MOC_B0
&#9474;     GUIDs:              267adb9d-b0eb-5ad0-9a94-db1e15359ebe &#8592; USB\VID_27C6&PID_63AC&REV_0100
&#9474;                         6f754a46-4a1d-590e-9c92-2ddafd352253 &#8592; USB\VID_27C6&PID_63AC
&#9474;     Device Flags:       • Updatable
&#9474;                         • Device can recover flash failures
&#9474;                         • Signed Payload
&#9474;   
&#9500;&#9472;Integrated Webcam HD:
&#9474;     Device ID:          23cf6368c14a875f74c38a5a423518f38d8abbbc
&#9474;     Current version:    22.81
&#9474;     Vendor:             CN0679GY8LG00318B27JA00 (USB:0x0C45)
&#9474;     Serial Number:      SN0001
&#9474;     GUIDs:              e448be98-e5fd-5d3d-a10e-a6457b15ac0a &#8592; USB\VID_0C45&PID_6748&REV_2281
&#9474;                         7cf56ef8-a08f-570b-a98d-56a65f737b9f &#8592; USB\VID_0C45&PID_6748
&#9474;     Device Flags:       • Updatable
&#9474;   
&#9500;&#9472;PC SN820 NVMe WD 4096GB:
&#9474;     Device ID:          c430a03ca2a65dfe2412ff950c79c51f6aec1317
&#9474;     Summary:            NVM Express solid state drive
&#9474;     Current version:    62012435
&#9474;     Vendor:             Sandisk Corp (NVME:0x15B7)
&#9474;     Serial Number:      23114N440810
&#9474;     GUIDs:              d665cfca-5c7e-50bb-ab20-2038a002a8f6 &#8592; STORAGE-DELL-112237
&#9474;                         133bcf78-25ba-11ec-9621-0242ac130002
&#9474;     Device Flags:       • Updatable
&#9474;                         • System requires external power source
&#9474;                         • Supported on remote server
&#9474;                         • Needs a reboot after installation
&#9474;                         • Signed Payload
&#9474;   
&#9500;&#9472;System Firmware:
&#9474; &#9474;   Device ID:          a45df35ac0e948ee180fe216a5f703f32dda163f
&#9474; &#9474;   Summary:            UEFI ESRT device
&#9474; &#9474;   Current version:    67072
&#9474; &#9474;   Minimum Version:    67072
&#9474; &#9474;   Vendor:             Dell Inc. (DMI:Dell Inc.)
&#9474; &#9474;   Update State:       Success
&#9474; &#9474;   GUIDs:              932db17c-aac5-425a-87cb-e21e1536544e
&#9474; &#9474;                       230c8b18-8d9b-53ec-838b-6cfc0383493a &#8592; main-system-firmware
&#9474; &#9474;   Device Flags:       • Internal device
&#9474; &#9474;                       • Updatable
&#9474; &#9474;                       • System requires external power source
&#9474; &#9474;                       • Needs a reboot after installation
&#9474; &#9474;                       • Cryptographic hash verification is available
&#9474; &#9474;                       • Device is usable for the duration of the update
&#9474; &#9474;                       • Full disk encryption secrets may be invalidated when updating
&#9474; &#9474; 
&#9474; &#9492;&#9472;UEFI dbx:
&#9474;       Device ID:        362301da643102b9f38477387e2193e57abaa590
&#9474;       Summary:          UEFI revocation database
&#9474;       Current version:  272
&#9474;       Minimum Version:  272
&#9474;       Vendor:           UEFI:Linux Foundation
&#9474;       Install Duration: 1 second
&#9474;       GUIDs:            00fe3755-a4d8-5ef7-ba5f-47979fbb3423 &#8592; UEFI\CRT_E28D59CA489BD2AD580F2EA5D62D6A29BB9C02AE5A818434A37DA7FC11DFF9E9
&#9474;                         4a6cd2cb-8741-5257-9d1f-89a275dacca7 &#8592; UEFI\CRT_E28D59CA489BD2AD580F2EA5D62D6A29BB9C02AE5A818434A37DA7FC11DFF9E9&ARCH_X64
&#9474;                         c6682ade-b5ec-57c4-b687-676351208742 &#8592; UEFI\CRT_A1117F516A32CEFCBA3F2D1ACE10A87972FD6BBE8FE0D0B996E09E65D802A503
&#9474;                         f8ba2887-9411-5c36-9cee-88995bb39731 &#8592; UEFI\CRT_A1117F516A32CEFCBA3F2D1ACE10A87972FD6BBE8FE0D0B996E09E65D802A503&ARCH_X64
&#9474;       Device Flags:     • Internal device
&#9474;                         • Updatable
&#9474;                         • Needs a reboot after installation
&#9474;                         • Only version upgrades are allowed
&#9474;                         • Signed Payload
&#9474;     
&#9500;&#9472;UEFI Device Firmware:
&#9474;     Device ID:          349bb341230b1a86e5effe7dfe4337e1590227bd
&#9474;     Summary:            UEFI ESRT device
&#9474;     Current version:    16660
&#9474;     Minimum Version:    16660
&#9474;     Vendor:             DMI:Dell Inc.
&#9474;     Update State:       Success
&#9474;     GUID:               e72475a2-b8f0-4217-bbea-3304b187ae54
&#9474;     Device Flags:       • Internal device
&#9474;                         • Updatable
&#9474;                         • System requires external power source
&#9474;                         • Needs a reboot after installation
&#9474;                         • Device is usable for the duration of the update
&#9474;   
&#9500;&#9472;UEFI Device Firmware:
&#9474;     Device ID:          2292ae5236790b47884e37cf162dcf23bfcd1c60
&#9474;     Summary:            UEFI ESRT device
&#9474;     Current version:    8833
&#9474;     Minimum Version:    8833
&#9474;     Vendor:             DMI:Dell Inc.
&#9474;     Update State:       Success
&#9474;     GUID:               07dcc837-0c45-6748-8501-00fed36dcdbb
&#9474;     Device Flags:       • Internal device
&#9474;                         • Updatable
&#9474;                         • System requires external power source
&#9474;                         • Needs a reboot after installation
&#9474;                         • Device is usable for the duration of the update
&#9474;   
&#9492;&#9472;UEFI Device Firmware:
      Device ID:          f95c9218acd12697af946874bfe4239587209232
      Summary:            UEFI ESRT device
      Current version:    1644241973
      Minimum Version:    1644241973
      Vendor:             DMI:Dell Inc.
      Update State:       Success
      GUID:               133bcf78-25ba-11ec-9621-0242ac130002
      Device Flags:       • Internal device
                          • Updatable
                          • System requires external power source
                          • Needs a reboot after installation
                          • Device is usable for the duration of the update
```

```
$ sudo fwupdmgr get-updates 
Devices with no available firmware updates: 
 • VEN 04F3:00 04F3:32AA
 • Fingerprint Sensor
 • Integrated Webcam HD
 • System Firmware
 • UEFI Device Firmware
 • UEFI Device Firmware
 • UEFI Device Firmware
 • UEFI dbx
Devices with the latest available firmware version:
 • PC SN820 NVMe WD 4096GB
No updates available
```

I'd really appreciate the help.

---

### Post by keywizard on 2024-01-23
Hi. Did you find a solution to the problem?

---

### Post by rkaalma on 2024-01-25
> **keywizard said:**
> Hi. Did you find a solution to the problem?
Unfortunately no.

I tried many suggestions around different forums without any success - thus came here to seek help. Currently my best hope is that MAYBE it will be fixed with Ubuntu 24.04.

I'd be willing to pay someone who believes to be able to fix it but I don't know where to look for such person.

---

### Post by rkaalma on 2024-04-14
I managed to fix the issue by installing clean (while keeping my home dir) Ubuntu 24.04 - I created a boot-image USB from a ISO downloaded from here: [https://cdimage.ubuntu.com/daily-live/current/](https://cdimage.ubuntu.com/daily-live/current/)

I had my / and /home in different partitions so it went quite easy for me although It's surely possible to re-install it otherwise as well (Google). You have to keep in mind that all system apps must be re-installed (unless /bin.

**Note: **I actually upgraded to 24.04 before re-installing but this didn't resolve the issue for me. I had most likely messed up some configurations or firmware while trying to get the sound to work on 22.04 - thus, re-install did the trick for me.

---

### Post by gabrielsere on 2024-08-08
The same happens to me.
I had Ubuntu 22 and a couple of months ago the audio started to fail until it stopped working. 
Now I put in a fresh installation of Ubuntu 24.04 and I only have HDMI output. The analog output is missing.

These are the outputs from my computer

```

ls /proc/asound/card0/cod*
/proc/asound/card0/codec#2

cat /proc/asound/card0/codec#2 
Codec: Intel Kabylake HDMI
Address: 2
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x8086280b
Subsystem Id: 0x80860101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0, Clock-stop-OK
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Device: name="HDMI 2", type="HDMI", device=8
  Converter: stream=1, channel=0
  Digital: Enabled KAE
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1a]: 16 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled KAE
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1a]: 16 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled KAE
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1a]: 16 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0b000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Devices: 0
  Connection: 0
Node 0x06 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0b000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Devices: 0
  Connection: 0
Node 0x07 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0b000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Devices: 0
  Connection: 0
Node 0x08 [Vendor Defined Widget] wcaps 0xf00000: Mono

aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: PCH [HDA Intel PCH], dispositivo 3: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: PCH [HDA Intel PCH], dispositivo 7: HDMI 1 [HDMI 1]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: PCH [HDA Intel PCH], dispositivo 8: HDMI 2 [HDMI 2]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

I think this is the expected output of "aplay" (taken from internet)
```

aplay -l
**** List of PLAYBACK Hardware Devices ****
**card 0: PCH [HDA Intel PCH], device 0: ALC3271 Analog [ALC3271 Analog]**
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
...

```

As you can see, the analog output in my computer is missing, which I assume is what modulates the output through the speakers.

---

### Post by stanwood on 2024-12-07
I have a Dell XPS 15 501LX running Ubuntu 24.04.1, which had exactly the same issue (No sound on HP, only dummy output).

I could fix this quite easily as followed:

```
sudo nano /etc/modprobe.d/alsa-base.conf
```

(add at the end of the file) :

```
# Enable internal audio and headphone jack on Dell
options snd-hda-intel model=auto
blacklist snd_soc_avs
```

Save and reboot

---

