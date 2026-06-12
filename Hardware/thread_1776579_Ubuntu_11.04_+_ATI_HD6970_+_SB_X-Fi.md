---
title: "Ubuntu 11.04 + ATI HD6970 + SB X-Fi"
date: 2011-06-06
forum: Hardware
---

### Post by Lisio on 2011-06-06
Made clean install of the ubuntu 11.04, updated everything through apt-get and install ati driver in Additional Drivers window. Now alsa doesn't see my SB X-Fi Xtreme Gamer Fatal1ty Pro Series. However, it can be found in lsmod and lspci.

```
root@server:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0
```

```
root@server:~# lsmod
Module Size Used by
snd_seq_midi 13324 0
snd_rawmidi 30486 1 snd_seq_midi
snd_seq_midi_event 14899 1 snd_seq_midi
snd_seq 61621 2 snd_seq_midi,snd_seq_midi_event
snd_seq_device 14462 3 snd_seq_midi,snd_rawmidi,snd_seq
snd_ctxfi 105792 0
snd_hda_intel 33211 0
snd_hda_codec_hdmi 28103 1
snd_hda_codec 103804 2 snd_hda_intel,snd_hda_codec_hdmi
snd_hwdep 13604 1 snd_hda_codec
snd_pcm 96625 4 snd_ctxfi,snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec
snd_timer 29602 2 snd_seq,snd_pcm
snd 67382 10 snd_rawmidi,snd_seq,snd_seq_device,snd_ctxfi,snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore 12680 1 snd
snd_page_alloc 18529 3 snd_ctxfi,snd_hda_intel,snd_pcm
binfmt_misc 17565 1
vboxnetadp 13382 0
vboxnetflt 28297 0
vboxdrv 268268 3 vboxnetadp,vboxnetflt
parport_pc 36959 0
ppdev 17113 0
vesafb 13761 1
fglrx 2739144 214
sp5100_tco 13744 0
i2c_piix4 13303 0
k10temp 13119 0
lp 17825 0
edac_core 53845 0
parport 46458 3 parport_pc,ppdev,lp
edac_mce_amd 23464 0
usbhid 46956 0
hid 91020 1 usbhid
pata_atiixp 13165 0
ahci 25951 4
libahci 26642 1 ahci
r8169 48022 0
```

```
root@server:~# lspci
00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Cayman XT [AMD Radeon HD 6900 Series]
01:00.1 Audio device: ATI Technologies Inc Device aa80
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:07.0 Multimedia audio controller: Creative Labs SB X-Fi
```

---

### Post by Yellow Pasque on 2011-06-06
Run alsa-info script: [http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973](http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973)

---

### Post by Lisio on 2011-06-06
```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Mon Jun  6 16:06:46 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 11.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.04"


!!DMI Information
!!---------------

Manufacturer:      Gigabyte Technology Co., Ltd.
Product Name:      GA-MA770T-UD3P
Product Version:    


!!Kernel Information
!!------------------

Kernel release:    2.6.38-8-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.24.1
Utilities version:  1.0.24.2


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfdefc000 irq 43


!!PCI Soundcards installed in the system
!!--------------------------------------

01:00.1 Audio device: ATI Technologies Inc Device aa80
03:07.0 Multimedia audio controller: Creative Labs SB X-Fi


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

01:00.1 0403: 1002:aa80
	Subsystem: 1458:aa80
--
03:07.0 0401: 1102:0005
	Subsystem: 1102:002c


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-ctxfi: index=0
snd-hda-intel: index=1


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: ATI R6xx HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="HDMI 0", type="HDMI", device=3
  Converter: stream=1, channel=0
  Digital: Enabled
  Digital category: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=03, enabled=1
  Connection: 1
     0x02
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw---- 1 root audio 116,  4 Jun  6 20:06 /dev/snd/controlC1
crw-rw---- 1 root audio 116,  3 Jun  6 20:06 /dev/snd/hwC1D0
crw-rw---- 1 root audio 116,  2 Jun  6 20:06 /dev/snd/pcmC1D3p
crw-rw---- 1 root audio 116,  1 Jun  6 20:06 /dev/snd/seq
crw-rw---- 1 root audio 116, 33 Jun  6 20:06 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jun  6 20:06 .
drwxr-xr-x 3 root root 160 Jun  6 20:06 ..
lrwxrwxrwx 1 root root  12 Jun  6 20:06 pci-0000:01:00.1 -> ../controlC1


!!ALSA configuration files
!!------------------------

!!System wide config file (/etc/asound.conf)

# Virtual 5.1 device (softvol):
# for volume control
pcm.softvol {
    type            softvol
    slave.pcm        "six"
    control {
        name        "UpMix51"
        card        0
    }
}

# software device with 6 channels 
pcm.six {
        type route
        slave.pcm "multi"
        ttable.0.0 1
        ttable.1.1 1
        ttable.2.2 1
        ttable.3.3 1
        ttable.4.4 1
        ttable.5.5 1
}


# customize this, if your xfi hast not the index=0 
# Splitting the channels into six different devices:
pcm.multi {
    type            multi
    slaves {
        a.pcm        "hw:0,0"
        a.channels    2

        b.pcm        "hw:0,1"
        b.channels    2

        c.pcm        "hw:0,2"
        c.channels    2
    }
    bindings {
        0.slave        a
        0.channel    0
        1.slave        a
        1.channel    1
        2.slave        b
        2.channel    0
        3.slave        b
        3.channel    1
        4.slave        c
        4.channel    0
        5.slave        c
        5.channel    1
    }
}

# Low/Highpass for channel speration
# controls[ x ] specifies the crossover frequency x for the subwoofer.
# 80-120 for most common systems

pcm.lowpass_21to21 {
    type ladspa
    slave.pcm upmix_21to51
    path "/usr/lib/ladspa"
    channels 3
    plugins {
      0 {
         id 1098  # Identity (Audio) (1098/identity_audio)
         policy duplicate
         input.bindings.0 "Input";
         output.bindings.0 "Output";
      }

      1 {
         id 1052  # High-pass filter
     
         policy none
         input.bindings.0 "Input";
         output.bindings.0 "Output";
         input {
            controls [ 120 ]
         }
      }

      2 {
         id 1052  # High-pass filter
     
         policy none
         input.bindings.1 "Input";
         output.bindings.1 "Output";
         input {
            controls [ 120 ]
         }
      }

      3 {
         id 1051  # Low-pass filter
     
         policy none
         input.bindings.2 "Input";
         output.bindings.2 "Output";
         input {
            controls [ 120 ]
         }
      }

   }
}

# upmix 2.0 to 5.1
pcm.upmix_20to51 {
   type plug
   slave.pcm "lowpass_21to21"
   slave.channels 3
   ttable {
      0.0     1       # left channel
      1.1     1       # right channel
      0.2     0.5     # mix left and right ...
      1.2     0.5     # channel for subwoofer
   }
}

#upmix 2.1 to 5.1
pcm.upmix_21to51 {
   type plug
   #For use without software volume control
   slave.pcm softvol
   slave.channels 6
   ttable {
      0.0     1       # front left
      1.1     1       # front right
      0.2     1       # rear left
      1.3     1       # rear right

      # Front left/right to center.
      0.4     0.5
      1.4     0.5

      # Power of the subwoofer, normally 1 (or if you like, more)

      2.5     1
    }
}

# Overwrite your default devices

pcm.!default {
    type            asym
    playback.pcm        "upmix_20to51"
}

pcm.!surround51 {
    type            plug
    slave.pcm        "softvol"
}

!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****

!!Amixer output
!!-------------

!!-------Mixer controls for card 1 [Generic]

Card hw:1 'Generic'/'HD-Audio Generic at 0xfdefc000 irq 43'
  Mixer name	: 'ATI R6xx HDMI'
  Components	: 'HDA:1002aa01,00aa0100,00100200'
  Controls      : 4
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.Generic {
	control.1 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.2 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.3 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.4 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
snd_ctxfi
snd_hda_intel
snd_hda_codec_hdmi
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
snd
soundcore
snd_page_alloc
binfmt_misc
vboxnetadp
vboxnetflt
vboxdrv
parport_pc
ppdev
vesafb
sp5100_tco
i2c_piix4
edac_core
edac_mce_amd
fglrx
k10temp
lp
parport
usbhid
hid
pata_atiixp
ahci
libahci
r8169


!!Sysfs Files
!!-----------

/sys/class/sound/hwC1D0/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   13.677552] [fglrx] module loaded - fglrx 8.84.60 [Mar 24 2011] with 1 minors
[   14.172412] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[   14.172427] SB-XFi 0000:03:07.0: enabling device (0000 -> 0003)
--
[   14.292495] ctxfi: Something wrong!!!
[   14.292513] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   14.292555] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[   14.292570] HDA Intel 0000:01:00.1: setting latency timer to 64
[   14.292573] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[   14.292610] SB-XFi: probe of 0000:03:07.0 failed with error -16
[   14.330094] ALSA hda_intel.c:915: codec_mask = 0x1
[   14.330137] ALSA hda_intel.c:1364: codec #0 probed OK
[   14.330139] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[   14.331928] ALSA hda_generic.c:652: hda_generic: no proper input path found
[   14.331931] ALSA hda_generic.c:287: Skip Digital OUT node 2
[   14.331933] ALSA hda_generic.c:430: hda_generic: no proper output path found
[   14.331936] ALSA hda_generic.c:1006: hda_generic: no PCM found
[   14.410476] EXT4-fs (sda5): warning: maximal mount count reached, running e2fsck is recommended
--
[   26.660117] eth1: no IPv6 routers present
[   31.980354] HDA Intel 0000:01:00.1: PCI INT B disabled
[   32.825326] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   32.825370] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[   32.825389] HDA Intel 0000:01:00.1: setting latency timer to 64
[   32.825392] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[   32.870052] ALSA hda_intel.c:915: codec_mask = 0x1
[   32.870105] ALSA hda_intel.c:1364: codec #0 probed OK
[   32.870107] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[   32.872075] ALSA hda_generic.c:652: hda_generic: no proper input path found
[   32.872079] ALSA hda_generic.c:287: Skip Digital OUT node 2
[   32.872081] ALSA hda_generic.c:430: hda_generic: no proper output path found
[   32.872083] ALSA hda_generic.c:1006: hda_generic: no PCM found
[   32.878151] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[   32.878168] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[   32.998181] SB-XFi: probe of 0000:03:07.0 failed with error -16
[   65.950315] HDA Intel 0000:01:00.1: PCI INT B disabled
[   66.693799] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[   66.693815] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[   66.813828] SB-XFi: probe of 0000:03:07.0 failed with error -16
[   66.818192] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   66.818234] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[   66.818252] HDA Intel 0000:01:00.1: setting latency timer to 64
[   66.818255] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[   66.870121] ALSA hda_intel.c:915: codec_mask = 0x1
[   66.870165] ALSA hda_intel.c:1364: codec #0 probed OK
[   66.870167] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[   66.870418] HDMI: sink_present = 0, eld_valid = 1
[   66.870658] input: HD-Audio Generic HDMI/DP as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input4
[  152.150503] HDA Intel 0000:01:00.1: PCI INT B disabled
[  153.271670] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[  153.271713] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[  153.271731] HDA Intel 0000:01:00.1: setting latency timer to 64
[  153.271733] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[  153.310207] ALSA hda_intel.c:915: codec_mask = 0x1
[  153.310313] ALSA hda_intel.c:1364: codec #0 probed OK
[  153.310320] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[  153.320833] HDMI: sink_present = 0, eld_valid = 1
[  153.321364] input: HD-Audio Generic HDMI/DP as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input5
[  153.334083] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[  153.334121] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[  153.454237] SB-XFi: probe of 0000:03:07.0 failed with error -16
[  209.860497] HDA Intel 0000:01:00.1: PCI INT B disabled
[  210.215113] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[  210.215152] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[  210.335386] SB-XFi: probe of 0000:03:07.0 failed with error -16
[  210.354730] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[  210.354833] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[  210.354875] HDA Intel 0000:01:00.1: setting latency timer to 64
[  210.354883] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[  210.390191] ALSA hda_intel.c:915: codec_mask = 0x1
[  210.390292] ALSA hda_intel.c:1364: codec #0 probed OK
[  210.390299] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[  210.390582] HDMI: sink_present = 0, eld_valid = 1
[  210.391106] input: HD-Audio Generic HDMI/DP as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input6
[  296.860467] HDA Intel 0000:01:00.1: PCI INT B disabled
[  297.743276] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[  297.743319] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[  297.743337] HDA Intel 0000:01:00.1: setting latency timer to 64
[  297.743340] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[  297.780122] ALSA hda_intel.c:915: codec_mask = 0x1
[  297.780227] ALSA hda_intel.c:1364: codec #0 probed OK
[  297.780235] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[  297.785787] ALSA hda_generic.c:652: hda_generic: no proper input path found
[  297.785798] ALSA hda_generic.c:287: Skip Digital OUT node 2
[  297.785805] ALSA hda_generic.c:430: hda_generic: no proper output path found
[  297.785813] ALSA hda_generic.c:1006: hda_generic: no PCM found
[  297.798528] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[  297.798566] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[  297.918673] SB-XFi: probe of 0000:03:07.0 failed with error -16
[  318.320611] HDA Intel 0000:01:00.1: PCI INT B disabled
[  319.111296] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[  319.111337] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[  319.231469] SB-XFi: probe of 0000:03:07.0 failed with error -16
[  319.276232] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[  319.276333] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[  319.276371] HDA Intel 0000:01:00.1: setting latency timer to 64
[  319.276379] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[  319.310205] ALSA hda_intel.c:915: codec_mask = 0x1
[  319.310300] ALSA hda_intel.c:1364: codec #0 probed OK
[  319.310307] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[  319.316016] ALSA hda_generic.c:652: hda_generic: no proper input path found
[  319.316026] ALSA hda_generic.c:287: Skip Digital OUT node 2
[  319.316033] ALSA hda_generic.c:430: hda_generic: no proper output path found
[  319.316042] ALSA hda_generic.c:1006: hda_generic: no PCM found
[  533.800750] HDA Intel 0000:01:00.1: PCI INT B disabled
[  534.891355] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[  534.891399] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[  534.891417] HDA Intel 0000:01:00.1: setting latency timer to 64
[  534.891420] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[  534.930162] ALSA hda_intel.c:915: codec_mask = 0x1
[  534.930264] ALSA hda_intel.c:1364: codec #0 probed OK
[  534.930271] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[  534.930552] HDMI: sink_present = 0, eld_valid = 1
[  534.931072] input: HD-Audio Generic HDMI/DP as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input7
[  534.951705] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[  534.951744] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[  535.071865] SB-XFi: probe of 0000:03:07.0 failed with error -16
[  856.210492] HDA Intel 0000:01:00.1: PCI INT B disabled
[  872.169427] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[  872.169468] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[  872.289637] SB-XFi: probe of 0000:03:07.0 failed with error -16
[  876.719427] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[  876.719445] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[  876.839509] SB-XFi: probe of 0000:03:07.0 failed with error -16
[ 1391.727709] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[ 1391.727747] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[ 1391.847916] SB-XFi: probe of 0000:03:07.0 failed with error -16
[ 1424.523910] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[ 1424.523949] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[ 1424.644130] SB-XFi: probe of 0000:03:07.0 failed with error -16
[ 1549.682420] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[ 1549.682461] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[ 1549.802628] SB-XFi: probe of 0000:03:07.0 failed with error -16
[ 1565.468094] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[ 1565.468117] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[ 1565.588231] SB-XFi: probe of 0000:03:07.0 failed with error -16
[ 1573.885428] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 1573.885472] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[ 1573.885490] HDA Intel 0000:01:00.1: setting latency timer to 64
[ 1573.885493] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[ 1573.922053] ALSA hda_intel.c:915: codec_mask = 0x1
[ 1573.922175] ALSA hda_intel.c:1364: codec #0 probed OK
[ 1573.922177] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[ 1573.927890] ALSA hda_generic.c:652: hda_generic: no proper input path found
[ 1573.927893] ALSA hda_generic.c:287: Skip Digital OUT node 2
[ 1573.927895] ALSA hda_generic.c:430: hda_generic: no proper output path found
[ 1573.927898] ALSA hda_generic.c:1006: hda_generic: no PCM found
[ 1583.181198] HDA Intel 0000:01:00.1: PCI INT B disabled
[ 1584.094511] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 1584.094616] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[ 1584.094658] HDA Intel 0000:01:00.1: setting latency timer to 64
[ 1584.094666] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[ 1584.130204] ALSA hda_intel.c:915: codec_mask = 0x1
[ 1584.130311] ALSA hda_intel.c:1364: codec #0 probed OK
[ 1584.130319] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[ 1584.130602] HDMI: sink_present = 0, eld_valid = 1
[ 1584.131117] input: HD-Audio Generic HDMI/DP as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input8
[ 1584.151360] ALSA init.c:199: cannot find the slot for index 0 (range 0-0), error: -16
[ 1584.151420] SB-XFi: probe of 0000:03:07.0 failed with error -16
[ 1599.780406] HDA Intel 0000:01:00.1: PCI INT B disabled
[ 1600.642458] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[ 1600.642475] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[ 1600.762570] SB-XFi: probe of 0000:03:07.0 failed with error -16
[ 1600.790601] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 1600.790701] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[ 1600.790741] HDA Intel 0000:01:00.1: setting latency timer to 64
[ 1600.790749] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[ 1600.840231] ALSA hda_intel.c:915: codec_mask = 0x1
[ 1600.840330] ALSA hda_intel.c:1364: codec #0 probed OK
[ 1600.840337] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[ 1600.845941] ALSA hda_generic.c:652: hda_generic: no proper input path found
[ 1600.845952] ALSA hda_generic.c:287: Skip Digital OUT node 2
[ 1600.845959] ALSA hda_generic.c:430: hda_generic: no proper output path found
[ 1600.845967] ALSA hda_generic.c:1006: hda_generic: no PCM found
[ 1611.251199] HDA Intel 0000:01:00.1: PCI INT B disabled
[ 1612.122691] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 1612.122794] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[ 1612.122834] HDA Intel 0000:01:00.1: setting latency timer to 64
[ 1612.122843] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[ 1612.179679] ALSA hda_intel.c:915: codec_mask = 0x1
[ 1612.179913] ALSA hda_intel.c:1364: codec #0 probed OK
[ 1612.179921] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[ 1612.180247] HDMI: sink_present = 0, eld_valid = 1
[ 1612.180766] input: HD-Audio Generic HDMI/DP as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input9
[ 1612.200179] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[ 1612.200196] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[ 1612.319923] SB-XFi: probe of 0000:03:07.0 failed with error -16
[ 1779.240514] HDA Intel 0000:01:00.1: PCI INT B disabled
[ 1780.336391] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[ 1780.336431] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[ 1780.456017] SB-XFi: probe of 0000:03:07.0 failed with error -16
[ 1780.501348] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 1780.501451] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[ 1780.501491] HDA Intel 0000:01:00.1: setting latency timer to 64
[ 1780.501499] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[ 1780.550182] ALSA hda_intel.c:915: codec_mask = 0x1
[ 1780.550289] ALSA hda_intel.c:1364: codec #0 probed OK
[ 1780.550296] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[ 1780.555921] ALSA hda_generic.c:652: hda_generic: no proper input path found
[ 1780.555932] ALSA hda_generic.c:287: Skip Digital OUT node 2
[ 1780.555939] ALSA hda_generic.c:430: hda_generic: no proper output path found
[ 1780.555947] ALSA hda_generic.c:1006: hda_generic: no PCM found
[ 1792.890652] HDA Intel 0000:01:00.1: PCI INT B disabled
[ 1793.797537] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 1793.797586] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[ 1793.797604] HDA Intel 0000:01:00.1: setting latency timer to 64
[ 1793.797607] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[ 1793.850211] ALSA hda_intel.c:915: codec_mask = 0x1
[ 1793.850321] ALSA hda_intel.c:1364: codec #0 probed OK
[ 1793.850328] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[ 1793.850611] HDMI: sink_present = 0, eld_valid = 1
[ 1793.851135] input: HD-Audio Generic HDMI/DP as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input10
[ 1793.871497] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[ 1793.871536] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[ 1793.991719] SB-XFi: probe of 0000:03:07.0 failed with error -16
[ 1831.970618] HDA Intel 0000:01:00.1: PCI INT B disabled
[ 1833.018966] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[ 1833.019003] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[ 1833.138950] SB-XFi: probe of 0000:03:07.0 failed with error -16
[ 1833.192561] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 1833.192653] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[ 1833.192692] HDA Intel 0000:01:00.1: setting latency timer to 64
[ 1833.192700] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[ 1833.230187] ALSA hda_intel.c:915: codec_mask = 0x1
[ 1833.230275] ALSA hda_intel.c:1364: codec #0 probed OK
[ 1833.230282] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[ 1833.235926] ALSA hda_generic.c:652: hda_generic: no proper input path found
[ 1833.235937] ALSA hda_generic.c:287: Skip Digital OUT node 2
[ 1833.235944] ALSA hda_generic.c:430: hda_generic: no proper output path found
[ 1833.235952] ALSA hda_generic.c:1006: hda_generic: no PCM found
[ 1833.246893] snd_hda_codec_hdmi: Unknown parameter `index'
[ 1843.010897] HDA Intel 0000:01:00.1: PCI INT B disabled
[ 1843.861624] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 1843.861726] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[ 1843.861767] HDA Intel 0000:01:00.1: setting latency timer to 64
[ 1843.861775] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[ 1843.900236] ALSA hda_intel.c:915: codec_mask = 0x1
[ 1843.900341] ALSA hda_intel.c:1364: codec #0 probed OK
[ 1843.900348] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[ 1843.906169] ALSA hda_generic.c:652: hda_generic: no proper input path found
[ 1843.906180] ALSA hda_generic.c:287: Skip Digital OUT node 2
[ 1843.906187] ALSA hda_generic.c:430: hda_generic: no proper output path found
[ 1843.906195] ALSA hda_generic.c:1006: hda_generic: no PCM found
[ 1843.922318] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[ 1843.922355] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[ 1844.042534] SB-XFi: probe of 0000:03:07.0 failed with error -16
[ 1853.940635] HDA Intel 0000:01:00.1: PCI INT B disabled
[ 1854.736123] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[ 1854.736163] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[ 1854.856334] SB-XFi: probe of 0000:03:07.0 failed with error -16
[ 1854.867973] snd_hda_codec: Unknown parameter `index'
[ 1854.966508] snd_hda_codec: Unknown parameter `index'
[ 1861.968871] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[ 1861.968893] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[ 1862.089014] SB-XFi: probe of 0000:03:07.0 failed with error -16
[ 1875.063324] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[ 1875.063361] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[ 1875.183542] SB-XFi: probe of 0000:03:07.0 failed with error -16
[ 1896.645012] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 1896.645108] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[ 1896.645156] HDA Intel 0000:01:00.1: setting latency timer to 64
[ 1896.645164] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[ 1896.680123] ALSA hda_intel.c:915: codec_mask = 0x1
[ 1896.680212] ALSA hda_intel.c:1364: codec #0 probed OK
[ 1896.680214] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[ 1896.684251] ALSA hda_generic.c:652: hda_generic: no proper input path found
[ 1896.684254] ALSA hda_generic.c:287: Skip Digital OUT node 2
[ 1896.684256] ALSA hda_generic.c:430: hda_generic: no proper output path found
[ 1896.684259] ALSA hda_generic.c:1006: hda_generic: no PCM found
[ 1903.270568] HDA Intel 0000:01:00.1: PCI INT B disabled
[ 1904.274550] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 1904.274657] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[ 1904.274698] HDA Intel 0000:01:00.1: setting latency timer to 64
[ 1904.274706] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[ 1904.310179] ALSA hda_intel.c:915: codec_mask = 0x1
[ 1904.310310] ALSA hda_intel.c:1364: codec #0 probed OK
[ 1904.310318] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[ 1904.315931] ALSA hda_generic.c:652: hda_generic: no proper input path found
[ 1904.315942] ALSA hda_generic.c:287: Skip Digital OUT node 2
[ 1904.315949] ALSA hda_generic.c:430: hda_generic: no proper output path found
[ 1904.315957] ALSA hda_generic.c:1006: hda_generic: no PCM found
[ 1904.336217] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[ 1904.336255] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[ 1904.456303] SB-XFi: probe of 0000:03:07.0 failed with error -16
[ 1917.791224] HDA Intel 0000:01:00.1: PCI INT B disabled
[ 1918.699128] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[ 1918.699151] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[ 1918.819258] SB-XFi: probe of 0000:03:07.0 failed with error -16
[ 1918.834757] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 1918.834816] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[ 1918.834839] HDA Intel 0000:01:00.1: setting latency timer to 64
[ 1918.834843] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[ 1918.883084] ALSA hda_intel.c:915: codec_mask = 0x1
[ 1918.883238] ALSA hda_intel.c:1364: codec #0 probed OK
[ 1918.883246] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[ 1918.883540] HDMI: sink_present = 0, eld_valid = 1
[ 1918.884058] input: HD-Audio Generic HDMI/DP as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input11
[ 9879.189109] EXT4-fs (sda2): Unaligned AIO/DIO on inode 659049 by VirtualBox; performance will be poor.
[10976.014961] CE: hpet increased min_delta_ns to 20113 nsec
[11098.911457] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[11098.911487] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x4011
[11098.930237] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[11098.930276] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x4011
[11098.932564] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x2
[11098.932672] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x2
[11098.937513] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[11098.937544] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x4011
[11098.937558] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[11098.937586] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x4011
[11099.123088] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[11103.967247] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x2
[11103.967356] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x2
[11142.300534] HDA Intel 0000:01:00.1: PCI INT B disabled
[11143.010207] snd: Not freed snd_alloc_kmalloc = 72
[11143.010216] snd: kmalloc(72) from ffffffffa031c1eb not freed
[11143.182555] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[11143.182618] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[11143.182638] HDA Intel 0000:01:00.1: setting latency timer to 64
[11143.182641] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[11143.220297] ALSA hda_intel.c:915: codec_mask = 0x1
[11143.220402] ALSA hda_intel.c:1364: codec #0 probed OK
[11143.220410] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[11143.226936] ALSA hda_generic.c:652: hda_generic: no proper input path found
[11143.226947] ALSA hda_generic.c:287: Skip Digital OUT node 2
[11143.226954] ALSA hda_generic.c:430: hda_generic: no proper output path found
[11143.226963] ALSA hda_generic.c:1006: hda_generic: no PCM found
[11143.240895] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[11143.240932] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[11143.361123] SB-XFi: probe of 0000:03:07.0 failed with error -16
[11153.250648] HDA Intel 0000:01:00.1: PCI INT B disabled
[11154.161144] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[11154.161162] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[11154.281259] SB-XFi: probe of 0000:03:07.0 failed with error -16
[11154.297646] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[11154.297825] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[11154.297867] HDA Intel 0000:01:00.1: setting latency timer to 64
[11154.297875] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[11154.330180] ALSA hda_intel.c:915: codec_mask = 0x1
[11154.330303] ALSA hda_intel.c:1364: codec #0 probed OK
[11154.330311] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[11154.330598] HDMI: sink_present = 0, eld_valid = 1
[11154.331124] input: HD-Audio Generic HDMI/DP as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input12
[11159.250387] HDA Intel 0000:01:00.1: PCI INT B disabled
[11160.222101] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[11160.222296] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[11160.222339] HDA Intel 0000:01:00.1: setting latency timer to 64
[11160.222348] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[11160.260058] ALSA hda_intel.c:915: codec_mask = 0x1
[11160.260166] ALSA hda_intel.c:1364: codec #0 probed OK
[11160.260174] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[11160.265957] ALSA hda_generic.c:652: hda_generic: no proper input path found
[11160.265969] ALSA hda_generic.c:287: Skip Digital OUT node 2
[11160.265976] ALSA hda_generic.c:430: hda_generic: no proper output path found
[11160.265984] ALSA hda_generic.c:1006: hda_generic: no PCM found
[11160.280196] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[11160.280232] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[11160.400398] SB-XFi: probe of 0000:03:07.0 failed with error -16
[11163.801227] HDA Intel 0000:01:00.1: PCI INT B disabled
[11164.672019] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[11164.672058] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[11164.792231] SB-XFi: probe of 0000:03:07.0 failed with error -16
[11164.808349] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[11164.808528] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[11164.808569] HDA Intel 0000:01:00.1: setting latency timer to 64
[11164.808577] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[11164.841352] ALSA hda_intel.c:915: codec_mask = 0x1
[11164.841496] ALSA hda_intel.c:1364: codec #0 probed OK
[11164.841503] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[11164.841788] HDMI: sink_present = 0, eld_valid = 1
[11164.842330] input: HD-Audio Generic HDMI/DP as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input13
[11169.880574] HDA Intel 0000:01:00.1: PCI INT B disabled
[11170.900556] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[11170.900621] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[11170.900639] HDA Intel 0000:01:00.1: setting latency timer to 64
[11170.900642] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[11170.940056] ALSA hda_intel.c:915: codec_mask = 0x1
[11170.940164] ALSA hda_intel.c:1364: codec #0 probed OK
[11170.940172] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[11170.945965] ALSA hda_generic.c:652: hda_generic: no proper input path found
[11170.945976] ALSA hda_generic.c:287: Skip Digital OUT node 2
[11170.945983] ALSA hda_generic.c:430: hda_generic: no proper output path found
[11170.945991] ALSA hda_generic.c:1006: hda_generic: no PCM found
[11170.959936] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[11170.959976] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[11171.080227] SB-XFi: probe of 0000:03:07.0 failed with error -16
[11174.781149] HDA Intel 0000:01:00.1: PCI INT B disabled
[11175.570312] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[11175.570349] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[11175.690509] SB-XFi: probe of 0000:03:07.0 failed with error -16
[11175.706582] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[11175.706770] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[11175.706810] HDA Intel 0000:01:00.1: setting latency timer to 64
[11175.706818] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[11175.740063] ALSA hda_intel.c:915: codec_mask = 0x1
[11175.740170] ALSA hda_intel.c:1364: codec #0 probed OK
[11175.740177] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[11175.740461] HDMI: sink_present = 0, eld_valid = 1
[11175.740990] input: HD-Audio Generic HDMI/DP as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input14
[11945.202688] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[11945.202718] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x4011
[11945.202752] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[11945.202778] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x4011
[11945.203329] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x2
[11945.203386] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x2
[11945.205295] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[11945.205322] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x4011
[11945.205334] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[11945.205360] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x4011
[11945.389811] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[11950.213434] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x2
[11950.213557] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x2
[13339.030521] HDA Intel 0000:01:00.1: PCI INT B disabled
[13349.300237] snd: Not freed snd_alloc_kmalloc = 72
[13349.300247] snd: kmalloc(72) from ffffffffa03181eb not freed
[13360.593534] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[13360.593573] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[13360.713751] SB-XFi: probe of 0000:03:07.0 failed with error -16
[13363.463778] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[13363.463816] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
--
[13363.583989] SB-XFi: probe of 0000:03:07.0 failed with error -16
[13945.116414] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[13945.116513] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[13945.116557] HDA Intel 0000:01:00.1: setting latency timer to 64
[13945.116565] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[13945.150052] ALSA hda_intel.c:915: codec_mask = 0x1
[13945.150196] ALSA hda_intel.c:1364: codec #0 probed OK
[13945.150203] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[13945.156064] ALSA hda_generic.c:652: hda_generic: no proper input path found
[13945.156075] ALSA hda_generic.c:287: Skip Digital OUT node 2
[13945.156082] ALSA hda_generic.c:430: hda_generic: no proper output path found
[13945.156091] ALSA hda_generic.c:1006: hda_generic: no PCM found
[13952.101283] HDA Intel 0000:01:00.1: PCI INT B disabled
[13953.180168] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[13953.180270] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[13953.180322] HDA Intel 0000:01:00.1: setting latency timer to 64
[13953.180331] ALSA hda_intel.c:2590: chipset global capabilities = 0x1001
[13953.230182] ALSA hda_intel.c:915: codec_mask = 0x1
[13953.230292] ALSA hda_intel.c:1364: codec #0 probed OK
[13953.230299] ALSA hda_intel.c:1463: Enable sync_write for AMD chipset
[13953.230580] HDMI: sink_present = 0, eld_valid = 1
[13953.231111] input: HD-Audio Generic HDMI/DP as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input15
[13953.252009] ALSA ctatc.c:1267: ctxfi: chip 20K1 model Unknown (1102:002c) is found
[13953.252027] SB-XFi 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[13953.273581] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[13953.273611] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x4011
[13953.273645] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[13953.273671] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x4011
[13953.274280] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x2
[13953.274331] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x2
[13953.275863] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[13953.275891] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x4011
[13953.275902] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[13953.275928] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x4011
[13953.372059] PLL initialization failed!!!
--
[13953.372129] SB-XFi: probe of 0000:03:07.0 failed with error -16
[13953.460365] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[13958.282683] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x2
[13958.282799] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x2


```

---

