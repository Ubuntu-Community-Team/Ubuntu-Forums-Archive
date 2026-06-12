---
title: "No HDMI sound, other sound is Okay Ubuntu 21.10"
date: 2022-02-07
forum: Hardware
---

### Post by gds1960 on 2022-02-07
HDMI shows up on the list of audio outputs, but when I choose it, the sound doesn't work at all. I checked to make sure nothing was muted and sound was turned up to 100%. I am pretty new to this. I have mainly been using windows for almost 26 years. I used Fedora for a couple of years, more than 10 years ago. I know a few of the commands for displaying information, but not all of them. I have this wonderful, hdmi sound system and can't use it at all. Any suggestions at all would be helpful.

Further Explanation:
Gnome
Open Settings app 
Open Sound menu
Check Output
Output Device: HDMI/DisplayPort - Built-in Audio
Configuration: Digital Stereo (HDMI) Output
Click "Test" Button, Click all speaker buttons one at a time and they light up and go off after 2 seconds and I hear nothing.

System: 
32 GB DDR4 3200MHz RAM
SP Silicon Power SU001TBP34A80M28AB 1 TB SSD
Dell Constellation 2 TB HDD
LG M-DISC Blu-Ray Disc
ASUS Prime Z590-p WIFI
CPU Intel Core i9-11900K Rocket Lake

```
inxi -A
Audio:
  Device-1: Intel Tiger Lake-H HD Audio driver: snd_hda_intel 
  Device-2: Microdia Webcam Vitade AF type: USB 
  driver: snd-usb-audio,uvcvideo 
  Sound Server-1: ALSA v: k5.13.0-28-generic running: yes 
  Sound Server-2: PulseAudio v: 15.0 running: yes 
  Sound Server-3: PipeWire v: 0.3.32 running: yes 

```

```
sudo dmesg | egrep -i "(hdmi|snd)" 
 0.174499] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    6.707531] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[    6.746814] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    6.796457] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC897: line_outs=3 (0x14/0x15/0x16/0x0/0x0) type:line
[    6.796460] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    6.796461] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    6.796461] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    6.796462] snd_hda_codec_realtek hdaudioC0D0:    dig-out=0x1e/0x0
[    6.796462] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    6.796463] snd_hda_codec_realtek hdaudioC0D0:      Front Mic=0x19
[    6.796464] snd_hda_codec_realtek hdaudioC0D0:      Rear Mic=0x18
[    6.796464] snd_hda_codec_realtek hdaudioC0D0:      Line=0x1a
[    6.852290] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input29
[    6.852423] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input30
[    6.852543] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input31
[    6.852652] input: HDA Intel PCH HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input32
[    6.852713] input: HDA Intel PCH HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input33
[    6.852759] input: HDA Intel PCH HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input34
[    6.852815] input: HDA Intel PCH HDMI/DP,pcm=12 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input35
[    6.852862] input: HDA Intel PCH HDMI/DP,pcm=13 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input36
[    6.852904] input: HDA Intel PCH HDMI/DP,pcm=14 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input37
[    6.852959] input: HDA Intel PCH HDMI/DP,pcm=15 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input38
[    6.853004] input: HDA Intel PCH HDMI/DP,pcm=16 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input39
[    6.853048] input: HDA Intel PCH HDMI/DP,pcm=17 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input40
[    6.906705] usbcore: registered new interface driver snd-usb-audio

```

---

### Post by gds1960 on 2022-02-18
Almost all sound output sources are dead. The only output source that works is the front headphone

---

### Post by SeijiSensei on 2022-02-18
What is the HDMI source? A video card from NVIDIA or ATI? For NVIDIA at least, you can only get sound with the proprietary driver. Go to Settings > Driver Manager and see if the application installs a new driver for your card.

---

### Post by #&amp;thj^% on 2022-02-18
Along with Seijisensei suggestion, Please give this a shot:
By adding "snd_intel_dspcfg.dsp_driver=1" to "/etc/default/grub"
```
sudo nano /etc/default/grub
```
after 
```

GRUB_CMDLINE_LINUX_DEFAULT "snd_intel_dspcfg.dsp_driver=1"

```
update grub
```
sudo update-grub
```
reboot >>> any difference?

---

### Post by gds1960 on 2022-02-18
Thank you I tried what 1fallen said and it had it did not make any changes. Yes I rebooted.

---

### Post by #&amp;thj^% on 2022-02-18
> **gds1960 said:**
> Thank you I tried what 1fallen said and it had it did not make any changes. Yes I rebooted.

Thanks for trying, one more output please:
```
lspci -nnk | grep -i -A7 audio
```
Paste back wrapped in code Tags please.
See my signature to see how if in doubt

---

### Post by gds1960 on 2022-02-18
1fallen here is the code you wanted::

```
  lspci -nnk | grep -i -A7 audio
00:1f.3 Audio device [0403]: Intel Corporation Tiger Lake-H HD Audio Controller [8086:43c8] (rev 11)
    DeviceName: Onboard - Sound
    Subsystem: ASUSTeK Computer Inc. Tiger Lake-H HD Audio Controller [1043:8814]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_sof_pci_intel_tgl
00:1f.4 SMBus [0c05]: Intel Corporation Tiger Lake-H SMBus Controller [8086:43a3] (rev 11)
    DeviceName: Onboard - Other
    Subsystem: ASUSTeK Computer Inc. Tiger Lake-H SMBus Controller [1043:8694]
    Kernel driver in use: i801_smbus
    Kernel modules: i2c_i801

 
```

---

### Post by gds1960 on 2022-02-19
I did not do anything, except make two or three rounds of updates and now my sound works perfectly.

---

### Post by #&amp;thj^% on 2022-02-19
> **gds1960 said:**
> I did not do anything, except make two or three rounds of updates and now my sound works perfectly.

Great News. ;)
I was about to send you here: (Your good to go so just ignore)
latest sof drivers are here:
[https://github.com/thesofproject/sof-bin](https://github.com/thesofproject/sof-bin)
and drivers are not distro specific packaged so they can be used with any distro.
Sof drivers work with Intel Tiger Lake-LP Smart Sound Audio after additional configuration.

---

### Post by gds1960 on 2022-02-21
By the way this is a Rocket Lake CPU. After turning off my computer overnight, the problem returned.

---

### Post by #&amp;thj^% on 2022-02-21
> **gds1960 said:**
> By the way this is a Rocket Lake CPU. After turning off my computer overnight, the problem returned.

Understood, but your sound is: "Intel Corporation Tiger Lake-H HD Audio Controller"
Did you ever follow SeijiSensei advice and check for additional drivers? Please Do...
After list:
```
 modinfo snd_intel_dspcfg

```
sample:
```
filename:       /lib/modules/5.13.0-28-generic/kernel/sound/hda/snd-intel-dspcfg.ko
import_ns:      SND_INTEL_SOUNDWIRE_ACPI
description:    Intel DSP config driver
license:        GPL v2
srcversion:     F3B55034508AFB453B99536
depends:        snd-intel-sdw-acpi
retpoline:      Y
intree:         Y
name:           snd_intel_dspcfg
vermagic:       5.13.0-28-generic SMP mod_unload modversions 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        56:AE:E3:DA:DB:A3:0C:A1:4D:27:93:47:28:5B:E2:4B:77:04:EF:4F
sig_hashalgo:   sha512
signature:     <Sniped by me>
parm:           dsp_driver:Force the DSP driver for Intel DSP (0=auto, 1=legacy, 2=SST, 3=SOF) (int)

```
Note: **parm:           dsp_driver:Force the DSP driver for Intel DSP (0=auto, 1=legacy, 2=SST, 3=SOF) (int)**

---

### Post by gds1960 on 2022-02-21
```
  sudo dmesg | egrep -i "(hdmi|sof|snd)"
[sudo] password for glenn: 
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-5.13.0-28-generic root=UUID=2ae816e4-750f-4fd9-b6f9-c8f211fffcd3 ro snd_intel_dspcfg.dsp_driver=1
[    0.057060] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.13.0-28-generic root=UUID=2ae816e4-750f-4fd9-b6f9-c8f211fffcd3 ro snd_intel_dspcfg.dsp_driver=1
[    0.174712] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.278750] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.320517] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.320518] software IO TLB: mapped [mem 0x000000004d18e000-0x000000005118e000] (64MB)
[    0.584838] integrity: Loaded X.509 cert 'Microsoft Corporation UEFI CA 2011: 13adbf4309bd82709c8cd54f316ed522988a1bd4'
[    0.585902] integrity: Loaded X.509 cert 'Microsoft Windows Production PCA 2011: a92902398e16c49778cd90f99e4f9ae17c55af53'
[    3.600061] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[    3.659246] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    3.736522] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC897: line_outs=3 (0x14/0x15/0x16/0x0/0x0) type:line
[    3.736524] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.736525] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    3.736526] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    3.736526] snd_hda_codec_realtek hdaudioC0D0:    dig-out=0x1e/0x0
[    3.736527] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    3.736527] snd_hda_codec_realtek hdaudioC0D0:      Front Mic=0x19
[    3.736528] snd_hda_codec_realtek hdaudioC0D0:      Rear Mic=0x18
[    3.736528] snd_hda_codec_realtek hdaudioC0D0:      Line=0x1a
[    3.803196] usbcore: registered new interface driver snd-usb-audio
[    3.803762] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input29
[    3.803785] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input30
[    3.803804] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input31
[    3.803823] input: HDA Intel PCH HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input32
[    3.803846] input: HDA Intel PCH HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input33
[    3.803878] input: HDA Intel PCH HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input34
[    3.803957] input: HDA Intel PCH HDMI/DP,pcm=12 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input35
[    3.804041] input: HDA Intel PCH HDMI/DP,pcm=13 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input36
[    3.804293] input: HDA Intel PCH HDMI/DP,pcm=14 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input37
[    3.804581] input: HDA Intel PCH HDMI/DP,pcm=15 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input38
[    3.804862] input: HDA Intel PCH HDMI/DP,pcm=16 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input39
[    3.805084] input: HDA Intel PCH HDMI/DP,pcm=17 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input40 
```

---

### Post by gds1960 on 2022-02-22
```
 modinfo snd_intel_dspcfg
filename:       /lib/modules/5.13.0-30-generic/kernel/sound/hda/snd-intel-dspcfg.ko
import_ns:      SND_INTEL_SOUNDWIRE_ACPI
description:    Intel DSP config driver
license:        GPL v2
srcversion:     0519E69CA2EA74BDB94C562
depends:        snd-intel-sdw-acpi
retpoline:      Y
intree:         Y
name:           snd_intel_dspcfg
vermagic:       5.13.0-30-generic SMP mod_unload modversions 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        63:1A:61:43:A2:1F:07:B4:3C:C4:6B:85:30:7F:0B:A6:18:AF:6B:48
sig_hashalgo:   sha512
signature:
parm:           dsp_driver:Force the DSP driver for Intel DSP (0=auto, 1=legacy, 2=SST, 3=SOF) (int) 
```

---

### Post by #&amp;thj^% on 2022-02-22
You seem to not want to answer this: **Did you ever follow SeijiSensei advice and check for additional drivers?**
Post a screenshot of:
```
ubuntu-drivers devices
```

---

### Post by gds1960 on 2022-02-22
I think I may have a problem. I installed Ubuntu 20.04.3 and I installed Ubuntu 22.04 Beta and Fedora 35. All OS's had the same problem. 
So I dug out a HDMI 2.0 cable, instead of the display-port cable and all sound was normal. 
It looks like I have a defective display-port cable.

ubuntu-drivers devices displays nothing.
sudo ubuntu-drivers devices displays nothing
```
 ubuntu-drivers debug
=== log messages from detection ===
DEBUG:root:Loading custom detection plugin /usr/share/ubuntu-drivers-common/detect/arm-gles.py
DEBUG:root:plugin /usr/share/ubuntu-drivers-common/detect/arm-gles.py return value: None
DEBUG:root:Loading custom detection plugin /usr/share/ubuntu-drivers-common/detect/sl-modem.py
DEBUG:root:plugin /usr/share/ubuntu-drivers-common/detect/sl-modem.py return value: None
=== modaliases in the system ===
acpi:PNP0C14:
wmi:05901221-D566-11D1-B2F0-00A0C9062910
wmi:A6FEA33E-DABF-46F5-BFC8-460D961BEC9F
wmi:2BC49DEF-7B15-4F05-8BB7-EE37B9547C0B
platform:eisa
wmi:A0485619-3E07-4ABE-BE6B-0AB67E2A92E6
platform:microcode
platform:snd-soc-dummy
platform:intel_rapl_msr
platform:Fixed MDIO bus
wmi:C3021213-D0BC-41A2-BA17-816CD5ED7744
acpi:PNP0C0C:
acpi:ACPI000C:
platform:rtc-efi
wmi:1F13AB7F-6220-4210-8F8E-8BB5E71EE969
platform:coretemp
platform:regulatory
platform:eeepc-wmi
input:b0019v0000p0000e0000-e0,1,4,14,k71,72,73,8B,94,98,AB,AC,B8,B9,BF,D4,E0,E1,E3,EE,F0,1AF,215,216,217,218,219,21A,ram4,lsfw
acpi:PNP0C0E:
acpi:MSFT0101:
acpi:ACPI000E:
wmi:ABBC0F72-8EA1-11D1-00A0-C90629100000
wmi:B82BB115-43AE-4B35-B79D-BD6416ABC381
acpi:INT34C6:
platform:efivars
wmi:24E974FB-5D4C-468B-8F55-A2790C65B5EC
platform:asus-nb-wmi
input:b0019v0000p0000e0000-e0,1,4,14,k71,72,73,8C,94,95,96,98,A3,A4,A5,A6,A9,B7,B9,BF,D4,D7,E0,E1,E2,E3,E5,E6,ED,EE,F0,F7,F8,213,230,ram4,lsfw
wmi:0B3CBB35-E3C2-45ED-91C2-4C5A6D195D1C
wmi:97845ED0-4E6D-11DE-8A39-0800200C9A66
platform:pcspkr
pci:v00008086d000043D2sv00001043sd00008694bc01sc06i01
pci:v00008086d000043E9sv00001043sd00008694bc0Csc80i00
platform:idma64
pci:v00008086d00004385sv00001043sd00008694bc06sc01i00
acpi:PNP0103:
acpi:PNP0C04:
pci:v000010ECd00008125sv00001043sd000087D7bc02sc00i00
pci:v00008086d000043F0sv00008086sd00000074bc02sc80i00
pci:v00008086d000043E0sv00001043sd00008694bc07sc80i00
mei::6861ec7b-d07a-4673-856c-7f22b4d55769:01:
mei::3c4852d6-d47b-4f46-b05e-b5edc1aa440e:01:
mei::dba4d603-d7ed-4931-8823-17ad585705d5:01:
mei::dd17041c-09ea-4b17-a271-5b989867ec65:01:
mei::082ee5a7-7c25-470a-9643-0c06f0466ea1:00:
mei::42b3ce2f-bd9f-485a-96ae-26406230b1ff:01:
mei::309dcde8-ccb1-4062-8f78-600115a34327:01:
mei::55213584-9a29-4916-badf-0fb7ed682aeb:02:
mei::8e6a6715-9abc-4043-88ef-9e39c6f63e0f:02:
mei::8c2f4425-77d6-4755-aca3-891fdbc66a58:01:
mei::fbf6fcf1-96cf-4e2e-a6a6-1bab8cbe36b1:01:
mei::b638ab7e-94e2-4ea2-a552-d1c54b627f04:01:
mei::5565a099-7fe2-45c1-a22b-d7e9dfea9a2e:01:
pci:v00001987d00005012sv00001987sd00005012bc01sc08i02
pci:v00008086d000043A4sv00001043sd00008694bc0Csc80i00
pci:v00008086d000043C8sv00001043sd00008814bc04sc03i00
hdaudio:v80862816r00100000a01
hdaudio:v10EC0897r00100402a01
input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,
input:b0000v0000p0000e0000-e0,5,kramlsfw4,
input:b0000v0000p0000e0000-e0,5,kramlsfw2,
input:b0000v0000p0000e0000-e0,5,kramlsfw6,
input:b0000v0000p0000e0000-e0,5,kramlsfwD,
pci:v00008086d000043E8sv00001043sd00008694bc0Csc80i00
pci:v00008086d000043EFsv00001043sd00008694bc05sc00i00
pci:v00008086d00004C8Asv00001043sd00008694bc03sc00i00
input:b001Ev0000p0000e0001-e0,1,2,4,14,k71,72,73,74,8A,8B,8D,8E,8F,96,9E,9F,A1,A4,A6,A7,A8,AB,AE,C8,C9,D0,D5,160,163,166,167,16C,16D,173,17A,189,18E,18F,190,191,192,193,199,19C,19D,1B6,200,201,202,203,204,205,206,207,208,209,266,267,268,269,26A,26B,26C,26D,26E,26F,270,271,272,273,274,275,276,277,r0,1,am4,lsfw
pci:v00008086d000043EDsv00001043sd00008694bc0Csc03i30
usb:v046DpC52Bd1211dc00dsc00dp00ic03isc01ip01in00
hid:b0003g0001v0000046Dp0000C52B
usb:v046DpC52Bd1211dc00dsc00dp00ic03isc01ip02in01
usb:v046DpC52Bd1211dc00dsc00dp00ic03isc00ip00in02
hid:b0003g0102v0000046Dp00004051
input:b0003v046Dp4051e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,B,C,am4,lsfw
hid:b0003g0102v0000046Dp00002011
input:b0003v046Dp2011e0111-e0,1,2,3,4,11,14,k71,72,73,74,75,77,78,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E0,E1,E4,E5,E6,E7,E8,E9,EA,EB,F0,F1,F4,100,161,162,166,16A,16E,172,174,176,177,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,197,198,199,19A,19C,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1AF,1B0,1B1,1B7,1BA,240,241,242,243,244,245,246,247,248,249,250,251,260,261,262,263,264,265,r6,C,a20,m4,l0,1,2,3,4,sfw
usb:v8087p0026d0002dcE0dsc01dp01icE0isc01ip01in00
usb:v8087p0026d0002dcE0dsc01dp01icE0isc01ip01in01
usb:v0C45p6366d0100dcEFdsc02dp01ic01isc01ip00in02
usb:v0C45p6366d0100dcEFdsc02dp01ic0Eisc01ip00in00
input:b0003v0C45p6366e0100-e0,1,kD4,ramlsfw
usb:v0C45p6366d0100dcEFdsc02dp01ic01isc02ip00in03
usb:v0C45p6366d0100dcEFdsc02dp01ic0Eisc02ip00in01
usb:v0B05p19AFd0100dc00dsc00dp00ic03isc00ip00in02
hid:b0003g0001v00000B05p000019AF
usb:v0B05p19AFd0100dc00dsc00dp00icFFiscFFipFFin00
usb:v1D6Bp0002d0513dc09dsc00dp01ic09isc00ip00in00
usb:v05E3p0610d6060dc09dsc00dp02ic09isc00ip02in00
usb:v1D6Bp0003d0513dc09dsc00dp03ic09isc00ip00in00
pci:v00008086d000043A3sv00001043sd00008694bc0Csc05i00
platform:iTCO_wdt
i2c:ee1004
cpu:type:x86,ven0000fam0006mod00A7:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003A,003B,003D,0068,006A,006B,006C,006D,006F,0070,0072,0074,0075,0076,0078,0079,007C,007F,0080,0081,0082,0083,0084,0085,0086,0087,0088,0089,008B,008C,008D,008E,008F,0091,0093,0094,0095,0096,0097,0098,0099,009A,009B,009C,009D,009E,00C0,00C5,00C8,00E1,00E3,00E7,00F0,00F1,00F3,00F5,00F9,00FA,00FB,00FE,00FF,0100,0101,0102,0103,0104,0111,0120,0121,0123,0125,0126,0127,0128,0129,012A,012D,012E,0130,0131,0132,0133,0134,0135,0137,0139,013C,013D,013E,013F,0140,0141,0142,0143,0164,0165,01C0,01C1,01C2,01C4,01C5,01C6,01C7,01C8,01C9,01CA,01CB,01CD,01CE,01CF,01D0,01D1,0201,0202,0203,0204,0206,0208,0209,020A,020B,020C,020E,0216,0244,024A,025A,025B,025C,025D,025F
dmi:bvnAmericanMegatrendsInc.:bvr1203:bd10/27/2021:br12.3:svnASUS:pnSystemProductName:pvrSystemVersion:rvnASUSTeKCOMPUTERINC.:rnPRIMEZ590-PWIFI:rvrRev1.xx:cvnDefaultstring:ct3:cvrDefaultstring:skuSKU:
acpi:LNXSYSTM:
acpi:LNXSYBUS:
acpi:LNXCPU:
acpi:PNP0C0F:
acpi:INT33A1:PNP0D80:
acpi:PNP0C02:
input:b0019v0000p0001e0000-e0,1,k74,ramlsfw
acpi:INT340E:PNP0C02:
input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw
acpi:PNP0A08:PNP0A03:
acpi:LNXPOWER:
acpi:INT3F0D:PNP0C02:
acpi:PNP0100:
acpi:PNP0501:
acpi:PNP0000:
input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw
acpi:PRP00001:PNP0A05:
acpi:PNP0C0B:
=== matching driver packages ===

 
```

---

### Post by #&amp;thj^% on 2022-02-22
Sounds like all is good then. 
Good Detective work on your part.

---

