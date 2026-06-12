---
title: "Audio constantly dropping out in Ubuntu 16.04 (NVidia and Intel Audio)"
date: 2016-06-16
forum: Hardware
---

### Post by dennis-w-olson on 2016-06-16
The audio keeps cutting in and out, and I can't figure out why. I've followed all steps in this guide:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

...and I've gotten no where. I'm wondering if the HDMI audio from the NVIDIA video card is causing it to "hiccup". How can I just disable the HDMI audio devices? I'm not using them.

I apologize if I'm posting to the wrong place. Please correct me if I'm doing this incorrectly. I've never had to ask for help before. The other Linux distros I've used never had issues with my hardware.

**sudo lspci -v | grep -A7 -i "audio"**
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
    DeviceName: Realtek High Definition Audio Device
    Subsystem: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at f7130000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
--
01:00.1 Audio device: NVIDIA Corporation GK106 HDMI Audio Controller (rev a1)
    Subsystem: eVga.com. Corp. GK106 HDMI Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f7080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

**aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: Generic Analog [Generic Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: Generic Digital [Generic Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: AUDIO [USB  AUDIO], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



**lsmod **
Module                  Size  Used by
vmnet                  53248  17
vmw_vsock_vmci_transport    28672  1
vsock                  36864  2 vmw_vsock_vmci_transport
vmw_vmci               65536  2 vmw_vsock_vmci_transport
vmmon                  86016  5
rfcomm                 69632  2
bnep                   20480  2
snd_hda_codec_hdmi     49152  1
nvidia_uvm            696320  0
nvidia_modeset        745472  5
snd_hda_codec_realtek    86016  0
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             172032  0
nvidia              10076160  137 nvidia_modeset,nvidia_uvm
kvm                   536576  1 kvm_intel
snd_hda_codec_generic    73728  2 snd_hda_codec_realtek
irqbypass              16384  1 kvm
snd_hda_intel          36864  7
snd_usb_audio         176128  1
crct10dif_pclmul       16384  0
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
crc32_pclmul           16384  0
snd_usbmidi_lib        36864  1 snd_usb_audio
snd_hda_core           86016  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  2 snd_usb_audio,snd_hda_codec
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
snd_seq_midi           16384  0
lrw                    16384  1 aesni_intel
snd_seq_midi_event     16384  1 snd_seq_midi
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
snd_rawmidi            32768  2 snd_usbmidi_lib,snd_seq_midi
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
snd_pcm               106496  6 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
btusb                  45056  0
joydev                 20480  0
btrtl                  16384  1 btusb
input_leds             16384  0
snd_timer              32768  2 snd_pcm,snd_seq
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             520192  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
drm                   360448  3 nvidia
snd                    81920  28 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
mei_me                 36864  0
soundcore              16384  1 snd
lpc_ich                24576  0
mei                    98304  1 mei_me
shpchp                 36864  0
ie31200_edac           16384  0
edac_core              53248  1 ie31200_edac
8250_fintek            16384  0
nuvoton_cir            20480  0
rc_core                28672  1 nuvoton_cir
wmi                    20480  0
mac_hid                16384  0
parport_pc             32768  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
uas                    24576  1
usb_storage            69632  1 uas
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
e1000e                237568  0
ahci                   36864  4
ptp                    20480  1 e1000e
libahci                32768  1 ahci
pps_core               20480  1 ptp
fjes                   28672  0
video                  40960  0

---

### Post by dennis-w-olson on 2016-06-16
I did a pulseaudio log, and saw this loop repeating over and over:

(  32.279|  11.592) D: [pulseaudio] module-alsa-card.c: Jack 'Front Headphone Jack' is now plugged in
(  32.279|   0.000) D: [pulseaudio] device-port.c: Setting port analog-output-headphones to status yes
(  32.279|   0.000) D: [pulseaudio] module-switch-on-port-available.c: Trying to switch to port analog-output-headphones
(  32.279|   0.000) D: [pulseaudio] module-alsa-card.c: Jack 'Front Mic Jack' is now unplugged
(  32.279|   0.000) D: [pulseaudio] device-port.c: Setting port analog-input-front-mic to status no
(  32.279|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
(  32.279|   0.000) D: [pulseaudio] module-switch-on-port-available.c: Trying to switch away from port analog-input-front-mic, found no better option
(  32.279|   0.000) D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
(  32.279|   0.000) D: [pulseaudio] module-udev-detect.c: Resuming all sinks and sources of card alsa_card.pci-0000_00_1b.0.
(  32.313|   0.033) D: [pulseaudio] module-alsa-card.c: Jack 'Front Headphone Jack' is now unplugged
(  32.313|   0.000) D: [pulseaudio] device-port.c: Setting port analog-output-headphones to status no

...It appears that the audio system was freaking out about a headphone jack on the front panel that had nothing plugged into it. I went into the BIOS and disabled the front panel audio and it stopped disconnecting and reconnecting, over and over.

I wouldn't call it a fix, but it's a work around.

---

### Post by Osamabingandhi on 2017-04-22
I found a way that might work for this issue. Pulseaudio is the system that handle sound and in the config file a way to handle sound is disabled and the solution is to activate that again:

edit with "sudo nano /etc/pulse/default.pa" in terminal (or "sudo gedit /etc/pulse/default.pa")

### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

change the above part of the file to make it look like this instead:

### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
load-module module-alsa-sink
load-module module-alsa-source device=hw:1,0
load-module module-oss device="/dev/dsp" sink_name=output source_name=input
load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
load-module module-null-sink
load-module module-pipe-sink

If you used nano to edit you save by ctrl O
reboot computer, or possible restart pulseaudio (I don't know how)

Then change sound settings under system settings for sound to use alsa instead of pulseaudio and see if that helps!

---

