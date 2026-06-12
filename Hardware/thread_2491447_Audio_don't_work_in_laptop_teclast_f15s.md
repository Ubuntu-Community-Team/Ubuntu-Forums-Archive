---
title: "Audio don't work in laptop teclast f15s"
date: 2023-10-09
forum: Hardware
---

### Post by 20ubuworrior on 2023-10-09
[COLOR=#333333][FONT=&amp]Hello,[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]i've just installed linux Mint on my laptop with a dedicated ssd. I have also updated the kernel but the audio still not work.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]i've installed also pulseaudio but there are only a virtual device (but works into windows). I have also disable fast boot for windows[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]On alsamixer i see that i have a Intel Broxton HDMI

[/FONT][/COLOR][COLOR=#333333][FONT=&amp]I add also same info:

[/FONT][/COLOR]```
[COLOR=#2E8B57][FONT=Monaco]aplay /usr/share/sounds/alsa/Front_Center.wav Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono[/FONT][/COLOR]
```[COLOR=#333333][FONT=&amp]

[/FONT][/COLOR][COLOR=#2E8B57][FONT=Monaco]```
francesco@francesco-F15S:~$ inxi -FxzSystem:  Kernel: 5.15.0-84-generic x86_64 bits: 64 compiler: gcc v: 11.4.0    Desktop: Cinnamon 5.4.12 Distro: Linux Mint 21 Vanessa    base: Ubuntu 22.04 jammyMachine:  Type: Laptop System: TECLAST product: F15S v: N/A    serial: <superuser required>  Mobo: TECLAST model: F15S serial: <superuser required> UEFI: TECLAST    v: tPAD3.02 date: 06/02/2021Battery:  ID-1: BAT0 charge: 38.0 Wh (100.0%) condition: 38.0/38.0 Wh (100.0%)    volts: 8.7 min: N/A model: WB SR 1 WB Lion Battery status: ChargingCPU:  Info: quad core model: Intel Celeron J3455 bits: 64 type: MCP    arch: Goldmont rev: 9 cache: L1: 224 KiB L2: 2 MiB  Speed (MHz): avg: 863 high: 1055 min/max: 800/2300 cores: 1: 1055 2: 799    3: 799 4: 799 bogomips: 11980  Flags: ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmxGraphics:  Device-1: Intel HD Graphics 500 driver: i915 v: kernel bus-ID: 00:02.0  Device-2: Alcor Micro USB 2.0 Camera type: USB driver: uvcvideo    bus-ID: 1-8:5  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: modesetting    unloaded: fbdev,vesa gpu: i915 resolution: 1920x1080~60Hz  OpenGL: renderer: Mesa Intel HD Graphics 500 (APL 2)    v: 4.6 Mesa 23.0.4-0ubuntu1~22.04.1 direct render: YesAudio:  Device-1: Intel Celeron N3350/Pentium N4200/Atom E3900 Series Audio Cluster    driver: sof-audio-pci-intel-apl bus-ID: 00:0e.0  Sound Server-1: ALSA v: k5.15.0-84-generic running: yes  Sound Server-2: PulseAudio v: 15.99.1 running: yes  Sound Server-3: PipeWire v: 0.3.48 running: yesNetwork:  Device-1: Realtek RTL8821CE 802.11ac PCIe Wireless Network Adapter    driver: rtl8821ce v: v5.5.2.1_35598.20191029 port: e000 bus-ID: 03:00.0  IF: wlp3s0 state: up mac: <filter>Bluetooth:  Device-1: Realtek Bluetooth Radio type: USB driver: btusb v: 0.8    bus-ID: 1-7:4  Report: hciconfig ID: hci0 rfk-id: 1 state: up address: <filter>    bt-v: 2.1 lmp-v: 4.2Drives:  Local Storage: total: 235.73 GiB used: 22.18 GiB (9.4%)  ID-1: /dev/mmcblk0 model: S0J39D size: 116.48 GiB  ID-2: /dev/sda vendor: Kingchuxing model: 128GB size: 119.24 GiBPartition:  ID-1: / size: 116.32 GiB used: 22.11 GiB (19.0%) fs: ext4 dev: /dev/sda2  ID-2: /boot/efi size: 96 MiB used: 74.9 MiB (78.0%) fs: vfat    dev: /dev/mmcblk0p1Swap:  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfileSensors:  System Temperatures: cpu: 53.0 C mobo: N/A  Fan Speeds (RPM): N/AInfo:  Processes: 219 Uptime: 10m Memory: 5.62 GiB used: 2.37 GiB (42.2%)  Init: systemd runlevel: 5 Compilers: gcc: 11.4.0 Packages: 2261 Shell: Bash  v: 5.1.16 inxi: 3.3.13
```[/FONT][/COLOR][COLOR=#333333][FONT=&amp]


[/FONT][/COLOR]```
[COLOR=#2E8B57][FONT=Monaco]francesco@francesco-F15S:~$ aplay -l**** List of PLAYBACK Hardware Devices ****card 0: sofhdadsp [sof-hda-dsp], device 1: HDMI1 (*) []  Subdevices: 1/1  Subdevice #0: subdevice #0card 0: sofhdadsp [sof-hda-dsp], device 2: HDMI2 (*) []  Subdevices: 1/1  Subdevice #0: subdevice #0card 0: sofhdadsp [sof-hda-dsp], device 3: HDMI3 (*) []  Subdevices: 1/1  Subdevice #0: subdevice #0[/FONT][/COLOR]
```[COLOR=#333333][FONT=&amp]

[/FONT][/COLOR]```
[COLOR=#2E8B57][FONT=Monaco]journalctl -k | grep -Ei "ALSA|HDA|sof[-]|HDMI|snd[_-]|sound|hda.codec|hda.intel"
[/FONT][/COLOR][COLOR=#2E8B57][FONT=Monaco]journalctl -k | grep -Ei "ALSA|HDA|sof[-]|HDMI|snd[_-]|sound|hda.codec|hda.intel"ott 06 20:54:27 francesco-F15S kernel: ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)ott 06 20:54:28 francesco-F15S kernel: snd_hda_intel 0000:00:0e.0: DSP detected with PCI class/subclass/prog-if info 0x040100ott 06 20:54:29 francesco-F15S kernel: snd_soc_skl 0000:00:0e.0: DSP detected with PCI class/subclass/prog-if info 0x040100ott 06 20:54:29 francesco-F15S kernel: sof-audio-pci-intel-apl 0000:00:0e.0: DSP detected with PCI class/subclass/prog-if info 0x040100ott 06 20:54:29 francesco-F15S kernel: sof-audio-pci-intel-apl 0000:00:0e.0: DSP detected with PCI class/subclass/prog-if 0x040100ott 06 20:54:29 francesco-F15S kernel: sof-audio-pci-intel-apl 0000:00:0e.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])ott 06 20:54:29 francesco-F15S kernel: sof-audio-pci-intel-apl 0000:00:0e.0: use msi interrupt modeott 06 20:54:29 francesco-F15S kernel: sof-audio-pci-intel-apl 0000:00:0e.0: hda codecs found, mask 4ott 06 20:54:29 francesco-F15S kernel: sof-audio-pci-intel-apl 0000:00:0e.0: using HDA machine driver skl_hda_dsp_generic nowott 06 20:54:29 francesco-F15S kernel: sof-audio-pci-intel-apl 0000:00:0e.0: DMICs detected in NHLT tables: 0ott 06 20:54:29 francesco-F15S kernel: sof-audio-pci-intel-apl 0000:00:0e.0: Firmware info: version 2:0:0-b678aott 06 20:54:29 francesco-F15S kernel: sof-audio-pci-intel-apl 0000:00:0e.0: Firmware: ABI 3:20:0 Kernel ABI 3:18:0ott 06 20:54:29 francesco-F15S kernel: sof-audio-pci-intel-apl 0000:00:0e.0: warn: FW ABI is more recent than kernelott 06 20:54:29 francesco-F15S kernel: sof-audio-pci-intel-apl 0000:00:0e.0: unknown sof_ext_man header type 3 size 0x30ott 06 20:54:29 francesco-F15S kernel: sof-audio-pci-intel-apl 0000:00:0e.0: Firmware info: version 2:0:0-b678aott 06 20:54:29 francesco-F15S kernel: sof-audio-pci-intel-apl 0000:00:0e.0: Firmware: ABI 3:20:0 Kernel ABI 3:18:0ott 06 20:54:29 francesco-F15S kernel: sof-audio-pci-intel-apl 0000:00:0e.0: warn: FW ABI is more recent than kernelott 06 20:54:29 francesco-F15S kernel: sof-audio-pci-intel-apl 0000:00:0e.0: Topology: ABI 3:20:0 Kernel ABI 3:18:0ott 06 20:54:29 francesco-F15S kernel: sof-audio-pci-intel-apl 0000:00:0e.0: warn: topology ABI is more recent than kernelott 06 20:54:29 francesco-F15S kernel: sof-audio-pci-intel-apl 0000:00:0e.0: ASoC: Parent card not yet available, widget card binding deferredott 06 20:54:29 francesco-F15S kernel: input: sof-hda-dsp HDMI/DP,pcm=1 as /devices/pci0000:00/0000:00:0e.0/skl_hda_dsp_generic/sound/card0/input13ott 06 20:54:29 francesco-F15S kernel: input: sof-hda-dsp HDMI/DP,pcm=2 as /devices/pci0000:00/0000:00:0e.0/skl_hda_dsp_generic/sound/card0/input14ott 06 20:54:29 francesco-F15S kernel: input: sof-hda-dsp HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:0e.0/skl_hda_dsp_generic/sound/card0/input15[/FONT][/COLOR]
```[COLOR=#333333][FONT=&amp]

[/FONT][/COLOR][COLOR=#333333][FONT=&amp]Can sameone help me?[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]Regards[/FONT][/COLOR]

---

