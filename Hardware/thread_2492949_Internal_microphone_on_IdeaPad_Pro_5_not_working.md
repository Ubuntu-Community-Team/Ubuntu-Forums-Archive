---
title: "Internal microphone on IdeaPad Pro 5 not working"
date: 2023-11-28
forum: Hardware
---

### Post by bimmelbommel on 2023-11-28
Hi there,
I just bought a Lenovo IdeaPad Pro 5 (16ARP8) and installed Ubuntu 22.04.3. Everything is working fine until I tried to hop onto a call and noticed that the internal microphone doesn't work and in fact isn't recognized by the system at all.

[IMG]https://i.postimg.cc/mkGXVmgk/Screenshot-from-2023-11-28-14-22-56.png[/IMG]

It's not a hardware defect as the microphone is working as intended in Windows:

[IMG]https://i.postimg.cc/HLbT6swt/Screenshot-2023-11-27-153011.png[/IMG]

> patrick@patrick-IdeaPad-Pro-5-16ARP8:~$ inxi -Fxz
System:
  Kernel: 6.2.0-37-generic x86_64 bits: 64 compiler: N/A Desktop: GNOME 42.9
    Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: LENOVO product: 83AS v: IdeaPad Pro 5 16ARP8
    serial: <superuser required>
  Mobo: LENOVO model: LNVNB161216 v: SDK0T76463 WIN
    serial: <superuser required> UEFI: LENOVO v: L0CN25WW date: 05/23/2023
Battery:
  ID-1: BAT0 charge: 13.6 Wh (17.5%) condition: 77.5/75.0 Wh (103.4%)
    volts: 14.9 min: 15.6 model: SMP L22M4PF5 status: Discharging
CPU:
  Info: 8-core model: AMD Ryzen 7 7735HS with Radeon Graphics bits: 64
    type: MT MCP arch: Zen 3 rev: 1 cache: L1: 512 KiB L2: 4 MiB L3: 16 MiB
  Speed (MHz): avg: 1546 high: 1600 min/max: 1600/4828 boost: disabled
    cores: 1: 1371 2: 1600 3: 1600 4: 1391 5: 1600 6: 1581 7: 1600 8: 1419
    9: 1381 10: 1600 11: 1600 12: 1600 13: 1600 14: 1600 15: 1600 16: 1600
    bogomips: 102206
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm
Graphics:
  Device-1: AMD Rembrandt vendor: Lenovo driver: amdgpu v: kernel
    bus-ID: 73:00.0
  Device-2: Acer Integrated RGB Camera type: USB driver: uvcvideo
    bus-ID: 5-1:2
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: gpu: amdgpu resolution: 2560x1600~120Hz
  OpenGL:
    renderer: REMBRANDT (rembrandt LLVM 15.0.7 DRM 3.49 6.2.0-37-generic)
    v: 4.6 Mesa 23.0.4-0ubuntu1~22.04.1 direct render: Yes
Audio:
  Device-1: AMD vendor: Lenovo driver: snd_hda_intel v: kernel
    bus-ID: 73:00.1
  Device-2: AMD Raven/Raven2/FireFlight/Renoir Audio Processor
    vendor: Lenovo driver: snd_pci_acp6x v: kernel bus-ID: 73:00.5
  Device-3: AMD Family 17h HD Audio vendor: Lenovo driver: snd_hda_intel
    v: kernel bus-ID: 73:00.6
  Sound Server-1: ALSA v: k6.2.0-37-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek vendor: Lenovo driver: rtw89_8852ce v: kernel port: 4000
    bus-ID: 01:00.0
  IF: wlp1s0 state: up mac: <filter>
Bluetooth:
  Device-1: Realtek Bluetooth Radio type: USB driver: btusb v: 0.8
    bus-ID: 3-3:2
  Report: hciconfig ID: hci0 rfk-id: 2 state: down
    bt-service: enabled,running rfk-block: hardware: no software: no
    address: <filter>
Drives:
  Local Storage: total: 476.94 GiB used: 11.3 GiB (2.4%)
  ID-1: /dev/nvme0n1 vendor: Lenovo model: UMIS RPJTJ512MKP1QDY
    size: 476.94 GiB temp: 28.9 C
Partition:
  ID-1: / size: 95.56 GiB used: 11.23 GiB (11.8%) fs: ext4
    dev: /dev/nvme0n1p5
  ID-2: /boot/efi size: 256 MiB used: 70.2 MiB (27.4%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  Alert: No swap data was found.
Sensors:
  System Temperatures: cpu: 38.0 C mobo: N/A gpu: amdgpu temp: 38.0 C
  Fan Speeds (RPM): N/A
Info:
  Processes: 398 Uptime: 4m Memory: 13.33 GiB used: 2.23 GiB (16.7%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.4.0 Packages: 1810 Shell: Bash
  v: 5.1.16 inxi: 3.3.13



Here's what I tried so far:

1. Installed PulseAudio Volume Control and check there

[IMG]https://i.postimg.cc/jSdsZXDM/Screenshot-from-2023-11-28-14-25-31.png[/IMG]

I also tried to unlock the channels and set the left one to zero (was recommended somewhere):

[IMG]https://i.postimg.cc/bv42tJzH/Screenshot-from-2023-11-28-14-25-42.png[/IMG]

2. Changed the input channel in /etc/modprobe.d/alsa-base.conf according to this tutorial: [https://candid.technology/ubuntu-microphone-not-working/](https://candid.technology/ubuntu-microphone-not-working/)

3. Tried to install the missing codecs but for my sound card there was no suitable codec name here: [https://www.kernel.org/doc/html/latest/sound/hd-audio/models.html](https://www.kernel.org/doc/html/latest/sound/hd-audio/models.html)

At least I found out that the codec apparently is a Realtek ALC257
```
cat /proc/asound/card*/codec* | grep Codec
Codec: ATI R6xx HDMI
Codec: Realtek ALC257
```

4. Stumbled upon a similar problem with ALC257 here and tried it's solution: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1904213](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1904213)

The temporary solution was posted here (although I think it doesn't apply to my hardware): [https://github.com/thesofproject/linux/issues/2460#issuecomment-779212719](https://github.com/thesofproject/linux/issues/2460#issuecomment-779212719)

5. Disabled Realtek driver module according to: [http://mreen.epizy.com/SoundFixTips2.html?i=1](http://mreen.epizy.com/SoundFixTips2.html?i=1)

6. Updated SOF driver according to a tutorial with a similar problem and ALC256: [https://forums.linuxmint.com/viewtopic.php?f=42&t=373391](https://forums.linuxmint.com/viewtopic.php?f=42&t=373391)

7. Booted the newest Ubuntu 23.10 from USB and checked the sound settings which was still empty

8. I've found an Arch forum that discussed exactly the issue I'm facing with ALC257: [https://bbs.archlinux.org/viewtopic.php?pid=2056452](https://bbs.archlinux.org/viewtopic.php?pid=2056452) Apparently ALC257 is the headphone/audio jack and not the internal microphone. My output is almost the same but instead of the ACP/ACP3X/ACP6x Audio Coprocessor from answer #5 I have an Raven/Raven2/FireFlight/Renoir Audio Processor:

```
lspci | grep Audio
73:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 1640
73:00.5 Multimedia controller: Advanced Micro Devices, Inc. [AMD] Raven/Raven2/FireFlight/Renoir Audio Processor (rev 60)
73:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) HD Audio Controller
```

The solution in the thread was to enable snd_pci_acp6x driver and its DMIC support to the kernel config. I'm hoping to do s.th. similar with the Raven/Raven2/FireFlight/Renoir Audio Processor. Now I've never done anything like this before and am also not sure how to do it in Ubuntu. 

Can someone tell me how to do it (the system is new, if it breaks then no worries) or have any other ideas to try?

Thanks,
Patrick

---

