---
title: "Intel WhiskeyLake-U (i915) Sound Sink missing despite working Source of same Device"
date: 2024-11-12
forum: Hardware
---

### Post by bemotion on 2024-11-12
Hello,

Ive upgraded over the time from Ubuntu LTS 18 to 20 to 22 to 24.
After upgrading to 24, actually quite late this year around September, I had some issues with my laptop speaker not working. If I remember properly it wasnt right away and the sound was working previously.

I used PipeWire and Wireplumber since LTS 22, but considered that with all the PulseAudio and JackD1/D2 (tried both for different reasons) left overs I try to clean everything up and install Alsa/PipeWire/Wireplumber again.
After that I messed around alot with various search results I found online and asking ChatGPT alot but reversed every attempt if it didnt work.
Long story short: Nothing helped.
Alsa was messed despite attempts to purge and fresh install it again until the recent update of Pipewire/Wireplumber that came last week via apt update, and now that Alsa works fine again I gave it another shot to try and fix it.
But I couldnt get it working until now.

Opening f.e. Alsamixer, the HDA Intel SND / Realtek ALC236 is recognized. As the internal Microphone works as Source, I am baffled why the internal speakers as sinks wont work. I thought they are both managed by the same device, but maybe Im wrong here.

The issue is beyond my knowledge at this time, and all I can think of is that it got to be something Driver/Kernel related and is not "for me to fix".

My last resort before installing Ubuntu again, is to ask in here. Obviously I dont want to make a fresh install because there are so many "tweaks" over the years and so much Software I am depended on with my daily driver that I can not afford the time to setup everything. That is why I am using no internal Speakers since September.

I would appreciate if you lead me threw all logs you need.

Here is kind of a summary via ChatGPT what I tried since September
[https://chatgpt.com/share/6733ab92-7080-8000-aa25-ccacf3974527](https://chatgpt.com/share/6733ab92-7080-8000-aa25-ccacf3974527)

And here are a couple of "logs":
HWprobe
[https://linux-hardware.org/?probe=350609bc50](https://linux-hardware.org/?probe=350609bc50)
Hardware: HP ProBook 450 G6 with Intel i5-8265U CPU, no dedicated GPU.
-> Checking for Type "Sound" in HWprobe baffles me, as the device is named "Cannon Point-LP High Definition Audio Controller" and I cant see RealTek ACL236 nowhere.

System-Info Script
[https://paste.ubuntu.com/p/8WqxpZ9w6v/](https://paste.ubuntu.com/p/8WqxpZ9w6v/)


> uname -a
Linux USERXXX 6.8.0-47-lowlatency #47.1-Ubuntu SMP PREEMPT_DYNAMIC Mon Oct  7 15:01:17 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux

> cat /proc/asound/cards 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0x4000108000 irq 158
 1 [USB            ]: USB-Audio - ThinkPad Thunderbolt 3 Dock USB
                      Lenovo ThinkPad Thunderbolt 3 Dock USB at usb-0000:00:14.0-6.1.1.2, full speed



> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC236 Analog [ALC236 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [DELL U2413]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [DELL U2413]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: USB [ThinkPad Thunderbolt 3 Dock USB], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


> pactl info
Server String: /run/user/1000/pulse/native
Library Protocol Version: 35
Server Protocol Version: 35
Is Local: yes
Client Index: 88
Tile Size: 65472
User Name: USERXXX
Host Name: USERXXX
Server Name: PulseAudio (on PipeWire 1.0.5)
Server Version: 15.0.0
Default Sample Specification: float32le 2ch 48000Hz
Default Channel Map: front-left,front-right
Default Sink: bluez_output.90_9C_4A_E1_61_C8.1
Default Source: alsa_input.pci-0000_00_1f.3.analog-stereo
Cookie: d8fe:cbc7

> pactl list short sinks
49    alsa_output.usb-Lenovo_ThinkPad_Thunderbolt_3_Dock_USB_Audio_000000000000-00.analog-stereo    PipeWire    s24le 2ch 48000Hz    SUSPENDED
51    alsa_output.pci-0000_00_1f.3.hdmi-stereo    PipeWire    s32le 2ch 48000Hz    SUSPENDED
65    bluez_output.90_9C_4A_E1_61_C8.1    PipeWire    s16le 2ch 48000Hz    SUSPENDED

> inxi -AAudio:
  Device-1: Intel Cannon Point-LP High Definition Audio driver: snd_hda_intel
  Device-2: Lenovo ThinkPad Thunderbolt 3 Dock USB Audio
    driver: hid-generic,snd-usb-audio,usbhid type: USB
  API: ALSA v: k6.8.0-47-lowlatency status: kernel-api
  Server-1: PipeWire v: 1.0.5 status: active


--> I also installed firmware-sof-signed, so maybe I should try using that driver - but I havent specifically tried it until now.

> journalctl -xe | grep audio
Nov 12 19:44:11 USERXXX gnome-session[4561]: gnome-session-binary[4561]: WARNING: Desktop file /etc/xdg/autostart/pulseaudio.desktop for application pulseaudio.desktop could not be parsed or references a missing TryExec binary
Nov 12 19:44:11 USERXXX gnome-session-binary[4561]: WARNING: Desktop file /etc/xdg/autostart/pulseaudio.desktop for application pulseaudio.desktop could not be parsed or references a missing TryExec binary
Nov 12 19:59:55 USERXXX sudo[12912]:     USERXXX : TTY=pts/0 ; PWD=/home/USERXXX ; USER=root ; COMMAND=/usr/bin/mv /etc/xdg/autostart/pulseaudio.desktop /etc/xdg/autostart/pulseaudio.desktop.bak
Nov 12 20:00:12 USERXXX ubuntustudio-audio-config[13004]: Found "settings" metadata 28
Nov 12 20:00:12 USERXXX ubuntustudio-audio-config[13004]: set property: id:0 key:clock.force-quantum value:128 type:(null)
Nov 12 20:00:12 USERXXX ubuntustudio-audio-config[13010]: Found "settings" metadata 28
Nov 12 20:00:12 USERXXX ubuntustudio-audio-config[13010]: set property: id:0 key:clock.force-rate value:48000 type:(null)
(since than I "sudo mv /etc/xdg/autostart/pulseaudio.desktop /etc/xdg/autostart/pulseaudio.desktop.bak && systemctl --user mask pulseaudio && systemctl --user stop pulseaudio" already

> journalctl --user -xe | grep pipewire
Nov 12 19:44:10 USERXXX systemd[4258]: Listening on pipewire-pulse.socket - PipeWire PulseAudio.
Nov 12 19:44:10 USERXXX systemd[4258]: Listening on pipewire.socket - PipeWire Multimedia System Sockets.
Nov 12 19:44:10 USERXXX systemd[4258]: Started pipewire.service - PipeWire Multimedia Service.
Nov 12 19:44:10 USERXXX systemd[4258]: Started pipewire-pulse.service - PipeWire PulseAudio.
Nov 12 20:00:12 USERXXX systemd[4258]: Stopping pipewire-pulse.service - PipeWire PulseAudio...
Nov 12 20:00:12 USERXXX systemd[4258]: Stopped pipewire-pulse.service - PipeWire PulseAudio.
Nov 12 20:00:12 USERXXX systemd[4258]: pipewire-pulse.service: Consumed 24.142s CPU time, 14.0M memory peak, 0B memory swap peak.
Nov 12 20:00:12 USERXXX wireplumber[4295]: disconnected from pipewire
Nov 12 20:00:12 USERXXX systemd[4258]: Stopping pipewire.service - PipeWire Multimedia Service...
Nov 12 20:00:12 USERXXX systemd[4258]: Stopped pipewire.service - PipeWire Multimedia Service.
Nov 12 20:00:12 USERXXX systemd[4258]: pipewire.service: Consumed 1.307s CPU time, 8.6M memory peak, 0B memory swap peak.
Nov 12 20:00:12 USERXXX systemd[4258]: Started pipewire.service - PipeWire Multimedia Service.
Nov 12 20:00:12 USERXXX systemd[4258]: Started pipewire-pulse.service - PipeWire PulseAudio.

> sudo dmesg | grep snd
[sudo] password for USERXXX:
[  179.036592] snd_hda_intel 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040380
[  179.036737] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[  179.076273] snd_hda_intel 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040380
[  179.084464] snd_hda_intel 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040380
[  179.092020] snd_hda_intel 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040380
[  179.098100] usbcore: registered new interface driver snd-usb-audio
[  179.098115] snd_hda_intel 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040380
[  179.987985] snd_hda_intel 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040380
[  180.113362] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[  180.215911] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC236: line_outs=1 (0x21/0x0/0x0/0x0/0x0) type:hp
**[  180.215920] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)**
[  180.215923] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[  180.215926] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[  180.215927] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[  180.215929] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x19
[  180.215931] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x12

speaker_outs=0 was baffeling me?

> systemctl --user status pipewire
&#9679; pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; enabled; preset: enabled)
     Active: active (running) since Tue 2024-11-12 20:00:12 CET; 29min ago
TriggeredBy: &#9679; pipewire.socket
   Main PID: 12989 (pipewire)
      Tasks: 2 (limit: 47281)
     Memory: 5.7M (peak: 6.6M)
        CPU: 89ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewire.service
             &#9492;&#9472;12989 /usr/bin/pipewire

Nov 12 20:00:12 USERXXX systemd[4258]: Stopped pipewire.service - PipeWire Multimedia Service.
Nov 12 20:00:12 USERXXX systemd[4258]: pipewire.service: Consumed 1.307s CPU time, 8.6M memory peak, 0B memory swap peak.
Nov 12 20:00:12 USERXXX systemd[4258]: Started pipewire.service - PipeWire Multimedia Service.


> ps aux | grep pipewire
USERXXX       12989  0.0  0.0  42252 13776 ?        S<sl 20:00   0:00 /usr/bin/pipewire
USERXXX       12994  0.0  0.0  24004  5840 ?        Ssl  20:00   0:00 /usr/bin/pipewire -c filter-chain.conf
USERXXX       12999  0.0  0.0  42352 14732 ?        S<sl 20:00   0:00 /usr/bin/pipewire-pulse
USERXXX       17120  0.0  0.0   9280  2304 pts/0    S+   20:30   0:00 grep --color=auto pipewire


> ls -ld /run/user/1000
drwx------ 19 USERXXX USERXXX 640 Nov 12 20:13 /run/user/1000

> lsmod | grep snd_hda_intel
snd_hda_intel          61440  1
snd_intel_dspcfg       36864  3 snd_hda_intel,snd_sof,snd_sof_intel_hda_common
snd_hda_codec         204800  6 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek,snd_soc_hdac_hda,snd_sof_intel_hda
snd_hda_core          139264  9 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_hda_codec_realtek,snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_sof_intel_hda
snd_pcm               192512  12 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,soundwire_intel,snd_sof,snd_sof_intel_hda_common,snd_compress,snd_soc_core,snd_sof_utils,snd_hda_core,snd_pcm_dmaengine
snd                   143360  23 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_sof,snd_timer,snd_compress,snd_soc_core,snd_ump,snd_pcm,snd_rawmidi




Thanks for your time.

---

### Post by bemotion on 2024-11-22
Ive installed a fresh Ubuntu 24 LTS and the issue persists!
That is clearly NOT a user fault any longer but a bug by Ubuntu 24! Up until 22 LTS (never tested 23) everything was running, so it only can be the Kernels Firmware/Extra Modules IMO.

I escalated this issue to a bug report:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/2089400](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/2089400)

---

