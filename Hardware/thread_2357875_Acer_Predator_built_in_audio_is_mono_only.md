---
title: "Acer Predator built in audio is mono only"
date: 2017-04-07
forum: Hardware
---

### Post by jlilly on 2017-04-07
Hello Gurus,

My Acer Predator G9-793-78CM laptop has an audio problem. The right speaker does not want to work, much less the built in sub-woofer. The audio jack outputs stereo, and I haven't tested the microphone input yet.

I tried downloading and compiling the RealTek Audio drivers from the RealTek website. Ran into numerous issues, though the real problem seems to be that this driver is only supported on kernel version 3.x.x

I also tried upgrading alsa as instructed [here]("https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS"), but when I install the deb file I get:
```
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.

```

Additionally, I tried reinstalling audio related packages as instructed [here]("http://www.alsa-project.org/db/?f=68e7fe12a18701f5a129e27d643bc678debd8d32"), but still only got mono. The command I ran was:
```

$ sudo apt install --reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` libasound2

```

Some information:

```

$ cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0x65120000 irq 126

```


```

$ dmesg | grep hda
[    2.895092] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC255: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    2.895094] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    2.895095] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    2.895096] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    2.895096] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    2.895097] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x1a
[    2.895098] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x12

```

```

[COLOR=#000000]!!################################[/COLOR]!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Fri Apr  7 04:09:38 UTC 2017


!!Linux Distribution
!!------------------

Ubuntu 16.04.2 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 16.04.2 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 16.04.2 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/" UBUNTU_CODENAME=xenial


!!DMI Information
!!---------------

Manufacturer:      Acer
Product Name:      Predator G9-793
Product Version:   V1.06
Firmware Version:  V1.06
Board Vendor:      Acer
Board Name:        Challenger2_SKS


!!ACPI Device Status Information
!!---------------

/sys/bus/acpi/devices/10250759:00/status      15
/sys/bus/acpi/devices/ACPI000C:00/status      15
/sys/bus/acpi/devices/INT33A1:00/status      15
/sys/bus/acpi/devices/INT340E:00/status      15
/sys/bus/acpi/devices/INT3F0D:00/status      15
/sys/bus/acpi/devices/LNXPOWER:00/status      1
/sys/bus/acpi/devices/MSFT0101:00/status      15
/sys/bus/acpi/devices/PNP0103:00/status      15
/sys/bus/acpi/devices/PNP0C02:00/status      3
/sys/bus/acpi/devices/PNP0C02:03/status      15
/sys/bus/acpi/devices/PNP0C02:04/status      3
/sys/bus/acpi/devices/PNP0C04:00/status      31
/sys/bus/acpi/devices/PNP0C0A:00/status      31
/sys/bus/acpi/devices/PNP0C0E:00/status      11
/sys/bus/acpi/devices/PNP0C0E:01/status      11
/sys/bus/acpi/devices/PNP0C0F:00/status      9
/sys/bus/acpi/devices/PNP0C0F:01/status      9
/sys/bus/acpi/devices/PNP0C0F:02/status      9
/sys/bus/acpi/devices/PNP0C0F:03/status      9
/sys/bus/acpi/devices/PNP0C0F:04/status      9
/sys/bus/acpi/devices/PNP0C0F:05/status      9
/sys/bus/acpi/devices/PNP0C0F:06/status      9
/sys/bus/acpi/devices/PNP0C0F:07/status      9
/sys/bus/acpi/devices/SYN1B8D:00/status      15
/sys/bus/acpi/devices/device:3e/status      15
/sys/bus/acpi/devices/device:81/status      11


!!Kernel Information
!!------------------

Kernel release:    4.8.0-46-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k4.8.0-46-generic
Library version:    1.1.0
Utilities version:  1.1.0


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0x65120000 irq 126


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1f.3 0403: 8086:a170 (rev 31)
    Subsystem: 1025:1132


!!Modprobe options (Sound related)
!!--------------------------------

snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
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
    bdl_pos_adj : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
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
    snoop : -1


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC255
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0255
Subsystem Id: 0x10251132
Revision Id: 0x100002
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3 D3cold CLKSTOP EPSS
  Power: setting=D0, actual=D0
GPIO: io=3, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x53 0x53]
  Converter: stream=1, channel=0
  PCM:
    rates [0x60]: 44100 48000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC255 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=1, channel=0
  PCM:
    rates [0x60]: 44100 48000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="ALC255 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1
  Amp-In vals:  [0x26 0x26]
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1
  Amp-In vals:  [0x97 0x97]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 1
     0x22
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 5
     0x18 0x19 0x1a 0x1b 0x1d
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Connection: 2
     0x03 0x0b
Node 0x0e [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0f [Audio Mixer] wcaps 0x20010a: Mono Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00]
  Connection: 1
     0x0d
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Control: name="Internal Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x90a601c0: [Fixed] Mic at Int N/A
    Conn = Digital, Color = Unknown
    DefAssociation = 0xc, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00010014: OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x90171110: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Black
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0c
Node 0x15 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x16 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x17 [Pin Complex] wcaps 0x40050c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x40000000: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x19 [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x1a [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x03a11030: [Jack] Mic at Ext Left
    Conn = 1/8, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0001373c: IN OUT HP EAPD Detect
    Vref caps: HIZ 50 GRD 80 100
  EAPD 0x2: EAPD
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 2
     0x0c* 0x0d
Node 0x1c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x40e89b2d: [N/A] Reserved at Ext N/A
    Conn = DIN, Color = Pink
    DefAssociation = 0x2, Sequence = 0xd
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x1e [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 1
     0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=76
Node 0x21 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0001001c: OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x03211020: [Jack] HP Out at Ext Left
    Conn = 1/8, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 2
     0x0c 0x0d*
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 6
     0x18 0x19 0x1a 0x1b 0x1d 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x00 0x00]
  Connection: 7
     0x18 0x19 0x1a 0x1b 0x1d 0x0b 0x12
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  2 Apr  6 22:07 /dev/snd/controlC0
crw-rw----  1 root audio 116,  5 Apr  6 22:07 /dev/snd/hwC0D0
crw-rw----  1 root audio 116,  4 Apr  6 22:08 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116,  3 Apr  6 22:09 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  1 Apr  6 22:07 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Apr  6 22:07 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Apr  6 22:07 .
drwxr-xr-x 3 root root 180 Apr  6 22:07 ..
lrwxrwxrwx 1 root root  12 Apr  6 22:07 pci-0000:00:1f.3 -> ../controlC0


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC255 Analog [ALC255 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC255 Analog [ALC255 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [PCH]

Card hw:0 'PCH'/'HDA Intel PCH at 0x65120000 irq 126'
  Mixer name    : 'Realtek ALC255'
  Components    : 'HDA:10ec0255,10251132,00100002'
  Controls      : 21
  Simple ctrls  : 10
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 87
  Mono: Playback 83 [95%] [-3.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 0 [0%] [-65.25dB] [off]
  Front Right: Playback 0 [0%] [-65.25dB] [off]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 254 [100%] [-0.20dB]
  Front Right: Playback 254 [100%] [-0.20dB]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 63
  Front Left: Capture 38 [60%] [11.25dB] [on]
  Front Right: Capture 38 [60%] [11.25dB] [on]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Loopback Mixing',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Disabled'


!!Alsactl output
!!--------------

--startcollapse--
state.PCH {
    control.1 {
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 87'
            dbmin -6525
            dbmax 0
            dbvalue.0 -6525
            dbvalue.1 -6525
        }
    }
    control.2 {
        iface MIXER
        name 'Headphone Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.3 {
        iface MIXER
        name 'Speaker Playback Volume'
        value.0 87
        value.1 87
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 87'
            dbmin -6525
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
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
        name 'Loopback Mixing'
        value Disabled
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
        name 'Mic Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.7 {
        iface MIXER
        name 'Mic Playback Switch'
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
    control.9 {
        iface MIXER
        name 'Capture Volume'
        value.0 38
        value.1 38
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 63'
            dbmin -1725
            dbmax 3000
            dbvalue.0 1125
            dbvalue.1 1125
        }
    }
    control.10 {
        iface MIXER
        name 'Capture Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.11 {
        iface MIXER
        name 'Mic Boost Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 3'
            dbmin 0
            dbmax 3000
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.12 {
        iface MIXER
        name 'Internal Mic Boost Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 3'
            dbmin 0
            dbmax 3000
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.13 {
        iface MIXER
        name 'Master Playback Volume'
        value 83
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 87'
            dbmin -6525
            dbmax 0
            dbvalue.0 -300
        }
    }
    control.14 {
        iface MIXER
        name 'Master Playback Switch'
        value true
        comment {
            access 'read write'
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
        name 'Internal Mic Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.17 {
        iface CARD
        name 'Headphone Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.18 {
        iface CARD
        name 'Speaker Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.19 {
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
    control.20 {
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
    control.21 {
        iface MIXER
        name 'PCM Playback Volume'
        value.0 254
        value.1 254
        comment {
            access 'read write user'
            type INTEGER
            count 2
            range '0 - 255'
            tlv '0000000100000008ffffec1400000014'
            dbmin -5100
            dbmax 0
            dbvalue.0 -20
            dbvalue.1 -20
        }
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
ccm
rfcomm
ipt_MASQUERADE
nf_nat_masquerade_ipv4
xfrm_user
xfrm_algo
iptable_nat
nf_conntrack_ipv4
nf_defrag_ipv4
nf_nat_ipv4
xt_addrtype
iptable_filter
ip_tables
xt_conntrack
x_tables
nf_nat
nf_conntrack
br_netfilter
bridge
stp
llc
aufs
arc4
pci_stub
vboxpci
vboxnetadp
vboxnetflt
vboxdrv
bnep
binfmt_misc
joydev
i2c_designware_platform
i2c_designware_core
acer_wmi
mxm_wmi
sparse_keymap
nvidia_uvm
snd_hda_codec_realtek
snd_hda_codec_generic
intel_rapl
x86_pkg_temp_thermal
intel_powerclamp
snd_hda_intel
coretemp
snd_hda_codec
uvcvideo
crct10dif_pclmul
crc32_pclmul
snd_hda_core
ath10k_pci
ghash_clmulni_intel
snd_hwdep
videobuf2_vmalloc
ath10k_core
aesni_intel
snd_pcm
videobuf2_memops
videobuf2_v4l2
videobuf2_core
snd_seq_midi
ath
aes_x86_64
snd_seq_midi_event
videodev
lrw
mac80211
glue_helper
ablk_helper
snd_rawmidi
cryptd
snd_seq
media
snd_seq_device
btusb
intel_cstate
btrtl
cfg80211
intel_rapl_perf
snd_timer
snd
input_leds
soundcore
serio_raw
mei_me
idma64
mei
virt_dma
shpchp
intel_lpss_pci
ucsi
hci_uart
btbcm
btqca
btintel
bluetooth
wmi
intel_lpss_acpi
intel_lpss
tpm_crb
mac_hid
acpi_pad
kvm_intel
kvm
irqbypass
parport_pc
ppdev
lp
parport
autofs4
uas
usb_storage
nvidia_drm
nvidia_modeset
nvidia
drm_kms_helper
syscopyarea
sysfillrect
sysimgblt
fb_sys_fops
psmouse
drm
alx
ahci
mdio
libahci
i2c_hid
pinctrl_sunrisepoint
video
hid
pinctrl_intel
fjes


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x12 0x90a601c0
0x14 0x90171110
0x17 0x40000000
0x18 0x411111f0
0x19 0x411111f0
0x1a 0x03a11030
0x1b 0x411111f0
0x1d 0x40e89b2d
0x1e 0x411111f0
0x21 0x03211020

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D0/hints:


!!ALSA/HDA dmesg
!!--------------

[    2.886426] intel_rapl: Found RAPL domain dram
[    2.895092] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC255: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    2.895094] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    2.895095] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    2.895096] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    2.895096] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    2.895097] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x1a
[    2.895098] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x12
[    2.908965] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input16
[    2.909027] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1f.3/sound/card0/input17
[    2.929347] nvidia-uvm: Loaded the UVM driver in 8 mode, major device number 242

```
[(Above alsa dump also available here)]("http://www.alsa-project.org/db/?f=68e7fe12a18701f5a129e27d643bc678debd8d32")

Please help me Obi Wan Kenobi! You're my only hope!

---

### Post by ptok on 2018-01-20
This is a bit of necromancy, but there is basically no widely available solution to Predator laptop family sound problem.
I'm owner of 791, older model, but laptops form that line are very similar, so that solution should also work with 591, 592, 593, 792 and 793.
 We need to override pins on card. 

Lets start with installation of hdajackretask.

 sudo apt-get install alsa-tools-gui 

It's fairly easy to use graphical tool. Run it as normal user. Select ALC255 codec from slider on top and check "show  unconnected pins" from menu on the right.
Then you need to find unconnected pins which can override as internal speakers: I set up 0x17 as internal LFE and 0x1b as internal speaker.
On newer models those might differ (but probably don't). In that case You need to do a bit of guessing. 
Save settings by clicking "Install boot override", authenticate with password to save config and reboot to check if changes works.

For me that setting unlocked stereo.

---

