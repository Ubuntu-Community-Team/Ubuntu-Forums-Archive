---
title: "[Dell 7310 Touch with 23.10] terrible video/audio on Realtek Integrated Webcam HD"
date: 2024-01-08
forum: Hardware
---

### Post by hitbyambulance2 on 2024-01-08
just got this refurb Dell 7310 Touch and installed Ubuntu 23.10 on it. Something is terribly wrong with the webcam (drivers?), as the displayed/transmitted video is extremely grainy with not true-to-life color, and the transmitted audio is 'lo-fi' sounding with constant static in the background. (Standard pre-recorded or svideo/audio playback is fine, it's only webcam related.) This problem manifests the same in both Skype and Google Meet.

sound device info is located at
[http://alsa-project.org/db/?f=3312ec5f15f3c5db54e2e766ee34c918e706acc8](http://alsa-project.org/db/?f=3312ec5f15f3c5db54e2e766ee34c918e706acc8)


```
$ inxi -Fxz
System:
  Kernel: 6.5.0-14-generic arch: x86_64 bits: 64 compiler: N/A Desktop: GNOME
    v: 45.1 Distro: Ubuntu 23.10 (Mantic Minotaur)
Machine:
  Type: Laptop System: Dell product: Latitude 7310 v: N/A
    serial: <superuser required>
  Mobo: Dell model: 00N7RN v: A01 serial: <superuser required> UEFI: Dell
    v: 1.24.0 date: 07/06/2023
Battery:
  ID-1: BAT0 charge: 24.5 Wh (71.4%) condition: 34.3/51.0 Wh (67.4%)
    volts: 7.4 min: 7.6 model: BYD DELL HRGYV0C status: discharging
CPU:
  Info: quad core model: Intel Core i7-10610U bits: 64 type: MT MCP
    arch: Comet/Whiskey Lake note: check rev: C cache: L1: 256 KiB L2: 1024 KiB
    L3: 8 MiB
  Speed (MHz): avg: 700 high: 800 min/max: 400/4900 cores: 1: 800 2: 400
    3: 800 4: 800 5: 800 6: 800 7: 800 8: 400 bogomips: 36799
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel CometLake-U GT2 [UHD Graphics] vendor: Dell Latitude 7310
    driver: i915 v: kernel arch: Gen-9.5 bus-ID: 00:02.0
  Device-2: Realtek Integrated_Webcam_HD driver: uvcvideo type: USB
    bus-ID: 1-6:2
  Display: wayland server: X.Org v: 1.23.2 with: Xwayland v: 23.2.0
    compositor: gnome-shell driver: dri: iris gpu: i915
    resolution: 1280x720~60Hz
  API: OpenGL v: 4.6 Mesa 23.2.1-1ubuntu3.1 renderer: Mesa Intel UHD
    Graphics (CML GT2) direct-render: Yes
Audio:
  Device-1: Intel Comet Lake PCH-LP cAVS vendor: Dell driver: snd_hda_intel
    v: kernel bus-ID: 00:1f.3
  API: ALSA v: k6.5.0-14-generic status: kernel-api
  Server-1: PipeWire v: 0.3.79 status: active
Network:
  Device-1: Intel Comet Lake PCH-LP CNVi WiFi driver: iwlwifi v: kernel
    bus-ID: 00:14.3
  IF: wlo1 state: up mac: <filter>
Bluetooth:
  Device-1: Intel AX201 Bluetooth driver: btusb v: 0.8 type: USB
    bus-ID: 1-10:4
  Report: hciconfig ID: hci0 rfk-id: 2 state: up address: <filter> bt-v: 5.2
    lmp-v: 11
Drives:
  Local Storage: total: 476.94 GiB used: 11.31 GiB (2.4%)
  ID-1: /dev/nvme0n1 vendor: SK Hynix model: PC611 NVMe 512GB
    size: 476.94 GiB temp: 34.9 C
Partition:
  ID-1: / size: 467.35 GiB used: 11.31 GiB (2.4%) fs: ext4 dev: /dev/nvme0n1p2
  ID-2: /boot/efi size: 1.05 GiB used: 6.1 MiB (0.6%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: file size: 4 GiB used: 256 KiB (0.0%) file: /swap.img
Sensors:
  System Temperatures: cpu: 43.0 C pch: 41.0 C mobo: N/A
  Fan Speeds (rpm): N/A
Info:
  Processes: 340 Uptime: 5d 5h 48m Memory: total: 16 GiB note: est.
  available: 15.29 GiB used: 9.68 GiB (63.3%) Init: systemd
  target: graphical (5) Compilers: N/A Packages: 1573 Shell: Bash v: 5.2.15
  inxi: 3.3.29


```

---

