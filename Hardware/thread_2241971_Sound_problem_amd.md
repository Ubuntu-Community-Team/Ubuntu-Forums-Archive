---
title: "Sound problem amd"
date: 2014-08-29
forum: Hardware
---

### Post by manowar2 on 2014-08-29
Hi
I installed Ubuntu 14.10, first day sound have a not problem, but second day i don't hear sound. Sound icon is disabled.
TOSHIBA SATELLITE C55D-A-14G NOTEBOOK

[http://tinypic.com/r/wwlmco/8](http://tinypic.com/r/wwlmco/8)

** lspci**
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8330]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
00:02.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 01)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 3a)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 5
01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Sun PRO [Radeon HD 8570A/8570M] (rev ff)
02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Qualcomm Atheros QCA8172 Fast Ethernet (rev 10)


**lsmod**
Module                  Size  Used by
ctr                    13193  1 
ccm                    17856  1 
rfcomm                 75114  12 
bnep                   19884  2 
nls_iso8859_1          12713  1 
dm_crypt               23456  0 
uvcvideo               86628  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59907  1 uvcvideo
amd_freq_sensitivity    12615  0 
kvm_amd                60904  0 
v4l2_common            15715  1 videobuf2_core
kvm                   468567  1 kvm_amd
videodev              163831  3 uvcvideo,v4l2_common,videobuf2_core
arc4                   12573  2 
media                  22008  2 uvcvideo,videodev
ath9k                 157355  0 
snd_hda_codec_idt      60103  1 
snd_hda_codec_hdmi     52620  1 
crct10dif_pclmul       14268  0 
crc32_pclmul           13180  0 
snd_hda_codec_generic    70087  1 snd_hda_codec_idt
ghash_clmulni_intel    13230  0 
aesni_intel           165515  538 
ath9k_common           25638  1 ath9k
snd_hda_intel          30783  4 
aes_x86_64             17131  1 aesni_intel
ath9k_hw              460121  2 ath9k_common,ath9k
snd_hda_controller     32234  1 snd_hda_intel
lrw                    13323  1 aesni_intel
snd_hda_codec         145035  5 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
gf128mul               14951  1 lrw
glue_helper            14095  1 aesni_intel
ath3k                  13381  0 
ablk_helper            13597  1 aesni_intel
cryptd                 20531  270 ghash_clmulni_intel,aesni_intel,ablk_helper
btusb                  32408  0 
ath                    29397  3 ath9k_common,ath9k,ath9k_hw
snd_hwdep              17709  1 snd_hda_codec
mac80211              696913  1 ath9k
snd_pcm               105052  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
bluetooth             477375  23 bnep,ath3k,btusb,rfcomm
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            31197  1 snd_seq_midi
snd_seq                63540  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
cfg80211              514757  4 ath,ath9k_common,ath9k,mac80211
joydev                 17587  0 
snd_timer              30118  2 snd_pcm,snd_seq
edac_core              52405  0 
serio_raw              13483  0 
snd                    84025  19 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
parport_pc             32906  0 
soundcore              15091  2 snd,snd_hda_codec
ppdev                  17711  0 
lp                     17799  0 
fam15h_power           13112  0 
edac_mce_amd           22800  0 
i2c_piix4              22311  0 
k10temp                13191  0 
shpchp                 37216  0 
toshiba_bluetooth      12867  0 
parport                42481  3 lp,ppdev,parport_pc
sparse_keymap          13890  0 
mac_hid                13275  0 
hid_generic            12559  0 
usbhid                 53122  0 
hid                   110572  2 hid_generic,usbhid
uas                    27623  0 
usb_storage            67010  1 uas
radeon               1519387  3 
psmouse               113721  0 
i2c_algo_bit           13564  1 radeon
ahci                   30167  2 
ttm                    90376  1 radeon
libahci                32533  1 ahci
drm_kms_helper         99872  1 radeon
ohci_pci               13570  0 
drm                   322638  6 ttm,drm_kms_helper,radeon
alx                    41397  0 
mdio                   13561  1 alx
wmi                    19379  0 
video                  20569  0

**sudo rmmod snd_hda_codec_hdmi**
rmmod: ERROR: Module snd_hda_codec_hdmi is in use

**sudo aplay -l**
Home directory not accessible:
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: 92HD95 Analog [92HD95 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

[B]ls /proc/asound
card0  cards    Generic    hwdep    oss  seq     version
card1  devices  Generic_1  modules  pcm  timers[/B]

---

### Post by Yellow Pasque on 2014-08-29
Can you give more info?: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
Are you trying to use HDMI or onboard sound?

---

### Post by manowar2 on 2014-08-29
> **Temüjin said:**
> Can you give more info?: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
Are you trying to use HDMI or onboard sound?

I attached file.
I don't know how i try HDMI or onboard sound. I only want listen music. Thank you.


upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.63
!!################################

!!Script ran on: Fri Aug 29 22:18:09 UTC 2014


!!Linux Distribution
!!------------------

Ubuntu Utopic Unicorn (development branch) \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu Utopic Unicorn (development branch)" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu Utopic Unicorn (development branch)" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


!!DMI Information
!!---------------

Manufacturer:      TOSHIBA
Product Name:      SATELLITE C55D-A-14G
Product Version:   PSCH2E-00X01KTE
Firmware Version:  1.20


!!Kernel Information
!!------------------

Kernel release:    3.17.0-031700rc2-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k3.17.0-031700rc2-generic
Library version:    1.0.28
Utilities version:  1.0.28


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xf0b40000 irq 39
 1 [Generic_1      ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xf0b44000 irq 40


!!PCI Soundcards installed in the system
!!--------------------------------------

00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:01.1 0403: 1002:9840
    Subsystem: 1179:fa30
--
00:14.2 0403: 1022:780d (rev 02)
    Subsystem: 1179:fa3c


!!Modprobe options (Sound related)
!!--------------------------------

snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2


!!Loaded sound module options
!!---------------------------

!!Module: snd_hda_intel
    align_buffer_size : -1
    bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N
    snoop : Y

!!Module: snd_hda_intel
    align_buffer_size : -1
    bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N
    snoop : Y


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: ATI R6xx HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100500
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0, Clock-stop-OK
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=1, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Control: name="HDMI/DP,pcm=3 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="ELD", index=0, device=3
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=01, enabled=1
  Connection: 1
     0x02
Node 0x04 [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x05 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x585600f0: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
Node 0x06 [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x07 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x585600f0: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Codec: IDT 92HD95
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x111d7695
Subsystem Id: 0x1179fa3c
Revision Id: 0x100101
No Modem Function Group found
Default PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3 D3cold S3D3cold CLKSTOP EPSS
  Power: setting=D0, actual=D0
GPIO: io=4, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Power-Map: 0x07
Node 0x0a [Pin Complex] wcaps 0x400581: Stereo
  Control: name="Headphone Jack", index=0, device=0
  Pincap 0x0001001c: OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x0421401f: [Jack] HP Out at Ext Right
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=01, enabled=1
  Power states: 
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x0b [Pin Complex] wcaps 0x400483: Stereo Amp-In
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Jack", index=0, device=0
  Amp-In caps: N/A
  Amp-In vals:  [0x01 0x01]
  Pincap 0x00011724: IN EAPD Detect
    Vref caps: HIZ 50 GRD 80
  EAPD 0x2: EAPD
  Pin Default 0x04a19040: [Jack] Mic at Ext Right
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
  Power states: 
  Power: setting=D3, actual=D3
Node 0x0c [Pin Complex] wcaps 0x400483: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00011724: IN EAPD Detect
    Vref caps: HIZ 50 GRD 80
  EAPD 0x2: EAPD
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states: 
  Power: setting=D3, actual=D3
Node 0x0d [Pin Complex] wcaps 0x400501: Stereo
  Control: name="Speaker Phantom Jack", index=0, device=0
  Pincap 0x00010050: OUT EAPD Balanced
  EAPD 0x2: EAPD
  Pin Default 0xd9130110: [Both] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states: 
  Power: setting=D0, actual=D0
  Connection: 2
     0x10 0x11*
Node 0x0e [Pin Complex] wcaps 0x400403: Stereo Amp-In
  Control: name="Internal Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Internal Mic Phantom Jack", index=0, device=0
  Amp-In caps: N/A
  Amp-In vals:  [0x01 0x01]
  Pincap 0x00000020: IN
  Pin Default 0xd9a30120: [Both] Mic at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power states: 
  Power: setting=D0, actual=D0
Node 0x0f [Pin Complex] wcaps 0x400403: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Power states: 
  Power: setting=D3, actual=D3
Node 0x10 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="92HD95 Analog", type="Audio", device=0
  Amp-Out caps: N/A
  Amp-Out vals:  [0x54 0x54]
  Converter: stream=5, channel=0
  Power states: 
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x11 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: N/A
  Amp-Out vals:  [0x2e 0x2e]
  Converter: stream=5, channel=0
  Power states: 
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x12 [Audio Input] wcaps 0x1d0541: Stereo
  Device: name="92HD95 Analog", type="Audio", device=0
  Converter: stream=1, channel=0
  SDI-Select: 0
  Power states: 
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x14
  Processing caps: benign=0, ncoeff=0
Node 0x13 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power states: 
  Power: setting=D3, actual=D3
  Delay: 13 samples
  Connection: 1
     0x15
  Processing caps: benign=0, ncoeff=0
Node 0x14 [Audio Selector] wcaps 0x300d0d: Stereo Amp-Out R/L
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-Out vals:  [0x9a 0x9a]
  Power states: 
  Power: setting=D0, actual=D0
  Connection: 5
     0x16 0x10 0x11 0x0e* 0x0f
Node 0x15 [Audio Selector] wcaps 0x300d0d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-Out vals:  [0x90 0x90]
  Power states: 
  Power: setting=D3, actual=D3
  Connection: 5
     0x16* 0x10 0x11 0x0e 0x0f
Node 0x16 [Audio Selector] wcaps 0x300501: Stereo
  Power states: 
  Power: setting=D3, actual=D3
  Connection: 2
     0x0c* 0x0b
Node 0x17 [Audio Output] wcaps 0x4061d: Stereo Digital Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power states: 
  Power: setting=D3, actual=D3
  Delay: 4 samples
Node 0x18 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states: 
  Power: setting=D3, actual=D3
  Connection: 1
     0x17
Node 0x19 [Beep Generator Widget] wcaps 0x70040c: Mono Amp-Out
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1
  Amp-Out vals:  [0x01]
  Power states: 
  Power: setting=D0, actual=D0
Node 0x1a [Vendor Defined Widget] wcaps 0xf00001: Stereo
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  2 Aug 29 22:13 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  5 Aug 29 22:13 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  4 Aug 29 22:13 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  8 Aug 29 22:13 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116,  3 Aug 30 01:14 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  7 Aug 30 01:14 /dev/snd/pcmC1D0c
crw-rw----+ 1 root audio 116,  6 Aug 30 01:14 /dev/snd/pcmC1D0p
crw-rw----+ 1 root audio 116,  1 Aug 29 22:13 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Aug 29 22:13 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Aug 29 22:13 .
drwxr-xr-x 3 root root 240 Aug 29 22:13 ..
lrwxrwxrwx 1 root root  12 Aug 29 22:13 pci-0000:00:01.1 -> ../controlC0
lrwxrwxrwx 1 root root  12 Aug 29 22:13 pci-0000:00:14.2 -> ../controlC1


!!Aplay/Arecord output
!!--------------------

APLAY

W: [pulseaudio] core-util.c: Failed to open configuration file '/home/manowar/.config/pulse//daemon.conf': Permission denied
W: [pulseaudio] daemon-conf.c: Failed to open configuration file: Permission denied
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: 92HD95 Analog [92HD95 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

W: [pulseaudio] core-util.c: Failed to open configuration file '/home/manowar/.config/pulse//daemon.conf': Permission denied
W: [pulseaudio] daemon-conf.c: Failed to open configuration file: Permission denied
**** List of CAPTURE Hardware Devices ****
card 1: Generic_1 [HD-Audio Generic], device 0: 92HD95 Analog [92HD95 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Generic]

Card hw:0 'Generic'/'HD-Audio Generic at 0xf0b40000 irq 39'
  Mixer name    : 'ATI R6xx HDMI'
  Components    : 'HDA:1002aa01,00aa0100,00100500'
  Controls      : 7
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

!!-------Mixer controls for card 1 [Generic_1]

Card hw:1 'Generic_1'/'HD-Audio Generic at 0xf0b44000 irq 40'
  Mixer name    : 'IDT 92HD95'
  Components    : 'HDA:111d7695,1179fa3c,00100101'
  Controls      : 21
  Simple ctrls  : 10
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 85 [67%] [-31.50dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 126 [99%] [-0.75dB] [on]
  Front Right: Playback 126 [99%] [-0.75dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 88 [69%] [-29.25dB] [on]
  Front Right: Playback 88 [69%] [-29.25dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 253 [99%] [-0.40dB]
  Front Right: Playback 253 [99%] [-0.40dB]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 1 [33%] [10.00dB]
  Front Right: 1 [33%] [10.00dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 1 [33%] [-12.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 26 [57%] [10.00dB] [off]
  Front Right: Capture 26 [57%] [10.00dB] [off]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 56 [47%] [-2.00dB]
  Front Right: Capture 56 [47%] [-2.00dB]
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 1 [33%] [10.00dB]
  Front Right: 1 [33%] [10.00dB]


!!Alsactl output
!!--------------

--startcollapse--
state.Generic {
    control.1 {
        iface CARD
        name 'HDMI/DP,pcm=3 Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.2 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.3 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.4 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.5 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.6 {
        iface PCM
        device 3
        name ELD
        value ''
        comment {
            access 'read volatile'
            type BYTES
            count 0
        }
    }
    control.7 {
        iface PCM
        device 3
        name 'Playback Channel Map'
        value.0 0
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access 'read write'
            type INTEGER
            count 8
            range '0 - 36'
        }
    }
}
state.Generic_1 {
    control.1 {
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 126
        value.1 126
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 127'
            dbmin -9525
            dbmax 0
            dbvalue.0 -75
            dbvalue.1 -75
        }
    }
    control.2 {
        iface MIXER
        name 'Headphone Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.3 {
        iface MIXER
        name 'Speaker Playback Volume'
        value.0 88
        value.1 88
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 127'
            dbmin -9525
            dbmax 0
            dbvalue.0 -2925
            dbvalue.1 -2925
        }
    }
    control.4 {
        iface MIXER
        name 'Speaker Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.5 {
        iface MIXER
        name 'Auto-Mute Mode'
        value Enabled
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Disabled
            item.1 Enabled
        }
    }
    control.6 {
        iface MIXER
        name 'Capture Volume'
        value.0 26
        value.1 26
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 46'
            dbmin -1600
            dbmax 3000
            dbvalue.0 1000
            dbvalue.1 1000
        }
    }
    control.7 {
        iface MIXER
        name 'Capture Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.8 {
        iface MIXER
        name 'Internal Mic Boost Volume'
        value.0 1
        value.1 1
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 3'
            dbmin 0
            dbmax 3000
            dbvalue.0 1000
            dbvalue.1 1000
        }
    }
    control.9 {
        iface MIXER
        name 'Mic Boost Volume'
        value.0 1
        value.1 1
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 3'
            dbmin 0
            dbmax 3000
            dbvalue.0 1000
            dbvalue.1 1000
        }
    }
    control.10 {
        iface MIXER
        name 'Beep Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.11 {
        iface MIXER
        name 'Beep Playback Volume'
        value 1
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 3'
            dbmin -1800
            dbmax 0
            dbvalue.0 -1200
        }
    }
    control.12 {
        iface MIXER
        name 'Master Playback Volume'
        value 85
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 127'
            dbmin -9999999
            dbmax 0
            dbvalue.0 -3150
        }
    }
    control.13 {
        iface MIXER
        name 'Master Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.14 {
        iface CARD
        name 'Internal Mic Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.15 {
        iface CARD
        name 'Mic Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.16 {
        iface CARD
        name 'Headphone Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.17 {
        iface CARD
        name 'Speaker Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.18 {
        iface PCM
        name 'Playback Channel Map'
        value.0 0
        value.1 0
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
    control.19 {
        iface PCM
        name 'Capture Channel Map'
        value.0 0
        value.1 0
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
    control.20 {
        iface MIXER
        name 'PCM Playback Volume'
        value.0 253
        value.1 253
        comment {
            access 'read write user'
            type INTEGER
            count 2
            range '0 - 255'
            tlv '0000000100000008ffffec1400000014'
            dbmin -5100
            dbmax 0
            dbvalue.0 -40
            dbvalue.1 -40
        }
    }
    control.21 {
        iface MIXER
        name 'Digital Capture Volume'
        value.0 56
        value.1 56
        comment {
            access 'read write user'
            type INTEGER
            count 2
            range '0 - 120'
            tlv '0000000100000008fffff44800000032'
            dbmin -3000
            dbmax 3000
            dbvalue.0 -200
            dbvalue.1 -200
        }
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
ctr
ccm
rfcomm
bnep
dm_crypt
nls_iso8859_1
uvcvideo
videobuf2_vmalloc
videobuf2_memops
videobuf2_core
v4l2_common
videodev
media
amd_freq_sensitivity
kvm_amd
kvm
snd_hda_codec_idt
crct10dif_pclmul
arc4
crc32_pclmul
ghash_clmulni_intel
snd_hda_codec_hdmi
snd_hda_codec_generic
aesni_intel
ath9k
aes_x86_64
snd_hda_intel
ath9k_common
ath9k_hw
lrw
gf128mul
glue_helper
ath3k
btusb
ablk_helper
cryptd
snd_hda_controller
bluetooth
joydev
serio_raw
snd_hda_codec
edac_core
k10temp
snd_hwdep
edac_mce_amd
fam15h_power
ath
snd_pcm
mac80211
snd_seq_midi
snd_seq_midi_event
snd_rawmidi
snd_seq
sparse_keymap
cfg80211
snd_seq_device
snd_timer
snd
shpchp
toshiba_bluetooth
i2c_piix4
soundcore
mac_hid
parport_pc
ppdev
lp
parport
hid_generic
usbhid
hid
uas
usb_storage
radeon
psmouse
i2c_algo_bit
ohci_pci
ttm
ahci
drm_kms_helper
libahci
drm
alx
mdio
wmi
video


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x03 0x185600f0
0x05 0x585600f0
0x07 0x585600f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D0/hints:

/sys/class/sound/hwC1D0/init_pin_configs:
0x0a 0x0421401f
0x0b 0x04a19040
0x0c 0x40f000f0
0x0d 0xd9130110
0x0e 0xd9a30120
0x0f 0x40f000f0
0x18 0x40f000f0

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:

/sys/class/sound/hwC1D0/hints:


!!ALSA/HDA dmesg
!!--------------

[    3.613741] [drm] Connector 1:
[    3.613743] [drm]   HDMI-A-1
[    3.613745] [drm]   HPD2
--
[   18.285753] usbcore: registered new interface driver btusb
[   18.504555] snd_hda_intel 0000:00:01.1: irq 39 for MSI/MSI-X
[   18.504978] snd_hda_intel 0000:00:14.2: irq 40 for MSI/MSI-X
[   18.690345] AVX version of gcm_enc/dec engaged.
--
[   18.698663] ath: Regpair used: 0x65
[   18.703674] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input18
[   18.929134] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
--
[   19.032102] usbcore: registered new interface driver ath3k
[   19.067287] sound hdaudioC1D0: autoconfig: line_outs=1 (0xd/0x0/0x0/0x0/0x0) type:speaker
[   19.067296] sound hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   19.067302] sound hdaudioC1D0:    hp_outs=1 (0xa/0x0/0x0/0x0/0x0)
[   19.067306] sound hdaudioC1D0:    mono: mono_out=0x0
[   19.067310] sound hdaudioC1D0:    inputs:
[   19.067315] sound hdaudioC1D0:      Internal Mic=0xe
[   19.067319] sound hdaudioC1D0:      Mic=0xb
[   19.078994] input: HD-Audio Generic Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input19
[   19.079174] input: HD-Audio Generic Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input20
[   19.408900] kvm: Nested Virtualization enabled
--
[   43.179194] systemd-logind[1522]: Linked /tmp/.X11-unix/X0 to /run/user/112/X11-display.
[   57.542433] snd_hda_intel 0000:00:01.1: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   57.762239] audit_printk_skb: 3 callbacks suppressed

---

