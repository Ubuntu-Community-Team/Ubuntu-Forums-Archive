---
title: "No sound on ALC892"
date: 2018-12-08
forum: Hardware
---

### Post by Renorems on 2018-12-08
Hello everyone,
I have a sound problem that I can not solve. I recently changed my hardware (new motherboard, CPU, RAM) and since then I have no sound. Of course, I did not reinstall my ubuntu. I tested from a live-usb, no sound either. Here's some informations :

```

$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller (rev 04)
01:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)

$ cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7430000 irq 44
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf7080000 irq 17

$ aplay -l
**** Liste des Périphériques Matériels PLAYBACK ****
carte 0: PCH [HDA Intel PCH], périphérique 0: ALC892 Analog [ALC892 Analog]
  Sous-périphériques: 0/1
  Sous-périphérique #0: subdevice #0
carte 0: PCH [HDA Intel PCH], périphérique 1: ALC892 Digital [ALC892 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 1: NVidia [HDA NVidia], périphérique 3: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 1: NVidia [HDA NVidia], périphérique 7: HDMI 1 [HDMI 1]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 1: NVidia [HDA NVidia], périphérique 8: HDMI 2 [HDMI 2]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 1: NVidia [HDA NVidia], périphérique 9: HDMI 3 [HDMI 3]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0

$ aplay -L
default
    Playback/recording through the PulseAudio sound server
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
sysdefault:CARD=PCH
    HDA Intel PCH, ALC892 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Front speakers
surround21:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
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
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 3
    Direct sample snooping device
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

$ cat /etc/modprobe.d/alsa-base.conf
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

options snd-hda-intel model=auto

$ dmesg | grep snd_hda
[   16.878183] snd_hda_intel 0000:01:00.1: Disabling MSI
[   16.878189] snd_hda_intel 0000:01:00.1: Handle vga_switcheroo audio client
[   16.965836] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC892: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[   16.965838] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   16.965839] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   16.965840] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[   16.965841] snd_hda_codec_realtek hdaudioC0D0:    dig-out=0x11/0x1e
[   16.965841] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[   16.965843] snd_hda_codec_realtek hdaudioC0D0:      Front Mic=0x19
[   16.965844] snd_hda_codec_realtek hdaudioC0D0:      Rear Mic=0x18
[   16.965844] snd_hda_codec_realtek hdaudioC0D0:      Line=0x1a
[   43.810674] Modules linked in: binfmt_misc intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm irqbypass crct10dif_pclmul nvidia_uvm(POE) crc32_pclmul ghash_clmulni_intel nvidia_drm(POE) pcbc aesni_intel snd_hda_codec_hdmi nvidia_modeset(POE) snd_hda_codec_realtek aes_x86_64 snd_hda_codec_generic nvidia(POE) snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm eeepc_wmi asus_wmi snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq crypto_simd wmi_bmof mxm_wmi sparse_keymap drm_kms_helper cryptd snd_seq_device snd_timer snd input_leds glue_helper drm intel_cstate mei_me mei ipmi_devintf ipmi_msghandler mac_hid intel_rapl_perf serio_raw video fb_sys_fops syscopyarea sysfillrect sysimgblt soundcore wmi sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid

```

I do not know what to do: any help would be appreciated.

---

