---
title: "The problem with the screen turning black when booting Ubuntu."
date: 2022-07-14
forum: Hardware
---

### Post by sezriati on 2022-07-14
Hello to everyone. 

I have been using Ubuntu and other Linux Operating Systems on my computer for a while. When I press the power button of my computer in all of them, including Ubuntu, I encounter a waiting time of 1.5 to 2 minutes. During this time, the screen goes black, then the screen turns on, but again it is black with only a little light. Then it blacks out again. The system boots up completely after 2 minutes. What could be the reason for this?

---

### Post by ajgreeny on 2022-07-14
It is impossible to give you an answer to your question without much more information about the hardware and OS version you're using.

Once booted open a terminal and run command ```
systemd-analyze blame
``` and then run the [System-info-script]("https://raw.githubusercontent.com/UbuntuForums/system-info/main/system-info") which should help us a lot more.

PLease use Code-Tags for terminal output as it makes it much easier to interpret what is being shown.
See my signature below for a How-to.

---

### Post by sezriati on 2022-07-14
Hi again, i am forwarding the codes to you.

```

21.205s plymouth-quit-wait.service
16.150s snapd.seeded.service
10.608s apparmor.service
 6.855s NetworkManager-wait-online.service
 3.120s snapd.apparmor.service
  897ms systemd-oomd.service
  862ms systemd-resolved.service
  810ms systemd-timesyncd.service
  708ms rtkit-daemon.service
  702ms systemd-machine-id-commit.service
  557ms dev-nvme0n1p2.device
  446ms snapd.service
  340ms networkd-dispatcher.service
  252ms systemd-udev-trigger.service
  217ms bluetooth.service
  203ms accounts-daemon.service
  202ms systemd-logind.service
  199ms dev-loop5.device
  197ms dev-loop4.device
  197ms dev-loop3.device
  187ms dev-loop2.device
  187ms dev-loop1.device
  187ms user@1000.service
lines 1-23...skipping...
21.205s plymouth-quit-wait.service
16.150s snapd.seeded.service
10.608s apparmor.service
 6.855s NetworkManager-wait-online.service
 3.120s snapd.apparmor.service
  897ms systemd-oomd.service
  862ms systemd-resolved.service
  810ms systemd-timesyncd.service
  708ms rtkit-daemon.service
  702ms systemd-machine-id-commit.service
  557ms dev-nvme0n1p2.device
  446ms snapd.service
  340ms networkd-dispatcher.service
  252ms systemd-udev-trigger.service
  217ms bluetooth.service
  203ms accounts-daemon.service
  202ms systemd-logind.service
  199ms dev-loop5.device
  197ms dev-loop4.device
  197ms dev-loop3.device
  187ms dev-loop2.device
  187ms dev-loop1.device
  187ms user@1000.service
  184ms dev-loop6.device
  184ms dev-loop0.device
  179ms dev-loop7.device
  169ms udisks2.service
  156ms ModemManager.service
  146ms e2scrub_reap.service
  133ms power-profiles-daemon.service
  127ms upower.service
  112ms switcheroo-control.service
  111ms systemd-udevd.service
  105ms systemd-journald.service
   94ms NetworkManager.service
   88ms apport.service
   86ms secureboot-db.service
   85ms gpu-manager.service
   84ms keyboard-setup.service
   75ms avahi-daemon.service
   64ms polkit.service
   64ms grub-common.service
   58ms systemd-fsck@dev-disk-by\x2duuid-BAB3\x2d8F4C.service
   57ms gdm.service
   54ms cups.service
   51ms thermald.service
   46ms packagekit.service
   42ms systemd-modules-load.service
   37ms colord.service
   36ms rsyslog.service
   32ms wpa_supplicant.service
   31ms systemd-journal-flush.service
   30ms systemd-update-utmp.service
   28ms nvidia-persistenced.service
   25ms systemd-tmpfiles-setup.service
   24ms boot-efi.mount
   24ms kerneloops.service
lines 1-57
21.205s plymouth-quit-wait.service
16.150s snapd.seeded.service
10.608s apparmor.service
 6.855s NetworkManager-wait-online.service
 3.120s snapd.apparmor.service
  897ms systemd-oomd.service
  862ms systemd-resolved.service
  810ms systemd-timesyncd.service
  708ms rtkit-daemon.service
  702ms systemd-machine-id-commit.service
  557ms dev-nvme0n1p2.device
  446ms snapd.service
  340ms networkd-dispatcher.service
  252ms systemd-udev-trigger.service
  217ms bluetooth.service
  203ms accounts-daemon.service
  202ms systemd-logind.service
  199ms dev-loop5.device
  197ms dev-loop4.device
  197ms dev-loop3.device
  187ms dev-loop2.device
  187ms dev-loop1.device
  187ms user@1000.service
  184ms dev-loop6.device
  184ms dev-loop0.device
  179ms dev-loop7.device
  169ms udisks2.service
  156ms ModemManager.service
  146ms e2scrub_reap.service
  133ms power-profiles-daemon.service
  127ms upower.service
  112ms switcheroo-control.service
  111ms systemd-udevd.service
  105ms systemd-journald.service
   94ms NetworkManager.service
   88ms apport.service
   86ms secureboot-db.service
   85ms gpu-manager.service
   84ms keyboard-setup.service
   75ms avahi-daemon.service
   64ms polkit.service
   64ms grub-common.service
   58ms systemd-fsck@dev-disk-by\x2duuid-BAB3\x2d8F4C.service
   57ms gdm.service
   54ms cups.service
   51ms thermald.service
   46ms packagekit.service
   42ms systemd-modules-load.service
   37ms colord.service
   36ms rsyslog.service
   32ms wpa_supplicant.service
   31ms systemd-journal-flush.service
   30ms systemd-update-utmp.service
   28ms nvidia-persistenced.service
   25ms systemd-tmpfiles-setup.service
   24ms boot-efi.mount
   24ms kerneloops.service
   22ms snap-bare-5.mount
   21ms snap-core20-1405.mount
   20ms dev-hugepages.mount
   19ms snap-firefox-1232.mount
   19ms systemd-update-utmp-runlevel.service
   19ms plymouth-start.service
   19ms dev-mqueue.mount
   18ms openvpn.service
   18ms sys-kernel-debug.mount
   18ms systemd-user-sessions.service
   17ms snap-gnome\x2d3\x2d38\x2d2004-99.mount
   17ms sys-kernel-tracing.mount
   16ms systemd-sysusers.service
   16ms alsa-restore.service
   16ms grub-initrd-fallback.service
   16ms plymouth-read-write.service
   16ms snap-gtk\x2dcommon\x2dthemes-1534.mount
   15ms systemd-tmpfiles-setup-dev.service
   14ms snap-snap\x2dstore-575.mount
   13ms systemd-sysctl.service
   13ms kmod-static-nodes.service
   12ms snap-snapd-15177.mount
   12ms modprobe@configfs.service
   12ms console-setup.service
   11ms user-runtime-dir@1000.service
   11ms setvtrgb.service
   11ms snap-snapd\x2ddesktop\x2dintegration-10.mount
   11ms systemd-random-seed.service
   10ms modprobe@fuse.service
    9ms sys-fs-fuse-connections.mount
    8ms systemd-remount-fs.service
    8ms swapfile.swap
    7ms sys-kernel-config.mount
    6ms systemd-backlight@backlight:intel_backlight.service
    5ms modprobe@drm.service
    4ms systemd-rfkill.service
    4ms ufw.service
  946us snapd.socket

```

---

### Post by ajgreeny on 2022-07-27
Sorry, I missed your post #3.

OK, so what is showing in that is your machine looks as if it's getting to **plymouth**, ie the graphical spinning ubuntu screen or something similar, (I use Xubuntu which just shows the word Xubuntu with a spinning circle icon below) before the login screen appears.

We still need to know more about your hardware so please run the [system-info-script]("https://raw.githubusercontent.com/UbuntuForums/system-info/main/system-info") as I asked last post which will tell us a lot of detail.

If you find that a bit difficult to understand just run command ```
inxi -Fzx
``` and copy back here the output of that command. You may have to install inxi first.
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by sezriati on 2022-08-01
```

System:
  Kernel: 5.15.0-43-generic x86_64 bits: 64 compiler: gcc v: 11.2.0
    Desktop: GNOME 42.2 Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: LENOVO product: 81WB v: IdeaPad3-15IML05
    serial: <superuser required>
  Mobo: LENOVO model: INVALID v: SDK0K17763 WIN
    serial: <superuser required> UEFI: LENOVO v: DXCN39WW date: 10/13/2021
Battery:
  ID-1: BAT0 charge: 30.9 Wh (97.8%) condition: 31.6/35.3 Wh (89.4%)
    volts: 8.5 min: 7.6 model: CPT-COS L16C2PB1 status: N/A
CPU:
  Info: quad core model: Intel Core i5-10210U bits: 64 type: MT MCP
    arch: Comet/Whiskey Lake note: check rev: C cache: L1: 256 KiB L2: 1024 KiB
    L3: 6 MiB
  Speed (MHz): avg: 876 high: 1317 min/max: 400/4200 cores: 1: 1317 2: 895
    3: 800 4: 800 5: 800 6: 800 7: 800 8: 800 bogomips: 33599
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel CometLake-U GT2 [UHD Graphics] vendor: Lenovo driver: i915
    v: kernel bus-ID: 00:02.0
  Device-2: NVIDIA GM108M [GeForce MX130] vendor: Lenovo driver: nvidia
    v: 515.48.07 bus-ID: 01:00.0
  Device-3: Syntek Integrated Camera type: USB driver: uvcvideo
    bus-ID: 1-7:3
  Display: x11 server: X.Org v: 1.21.1.3 driver: X:
    loaded: modesetting,nvidia unloaded: fbdev,nouveau,vesa gpu: i915
    resolution: 1920x1080~60Hz
  OpenGL: renderer: Mesa Intel UHD Graphics (CML GT2) v: 4.6 Mesa 22.0.1
    direct render: Yes
Audio:
  Device-1: Intel Comet Lake PCH-LP cAVS vendor: Lenovo driver: snd_hda_intel
    v: kernel bus-ID: 00:1f.3
  Sound Server-1: ALSA v: k5.15.0-43-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Intel Comet Lake PCH-LP CNVi WiFi driver: iwlwifi v: kernel
    bus-ID: 00:14.3
  IF: wlp0s20f3 state: up mac: <filter>
Bluetooth:
  Device-1: Intel Bluetooth 9460/9560 Jefferson Peak (JfP) type: USB
    driver: btusb v: 0.8 bus-ID: 1-10:4
  Report: hciconfig ID: hci0 rfk-id: 2 state: down
    bt-service: enabled,running rfk-block: hardware: no software: yes
    address: <filter>
Drives:
  Local Storage: total: 238.47 GiB used: 19.31 GiB (8.1%)
  ID-1: /dev/nvme0n1 vendor: Western Digital
    model: PC SN520 SDAPMUW-256G-1101 size: 238.47 GiB temp: 44.9 C
Partition:
  ID-1: / size: 233.18 GiB used: 19.3 GiB (8.3%) fs: ext4 dev: /dev/nvme0n1p2
  ID-2: /boot/efi size: 511 MiB used: 5.2 MiB (1.0%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 1.5 MiB (0.1%) file: /swapfile
Sensors:
  System Temperatures: cpu: 64.0 C pch: 64.0 C mobo: N/A
  Fan Speeds (RPM): N/A
Info:
  Processes: 327 Uptime: 6h 42m Memory: 7.51 GiB used: 3.84 GiB (51.1%)
  Init: systemd runlevel: 5 Compilers: gcc: N/A Packages: 1808 Shell: Bash
  v: 5.1.16 inxi: 3.3.13

```


I did what you said, waiting for your reply.

---

### Post by ajgreeny on 2022-08-02
I see you have an nvidia graphic card which unfortunately for you I know next to nothing about never having had a computer with nvidia card installed.

In the past it was necessary to start  using the nomodeset boot-option but I thought that had now become unnecessary; perhaps I have that wrong so it may be worth trying a cold boot and at the grub menu hit e (edit) on the line that ends with ***quiet splash*** and add the word ***nomodeset*** then hit F10 to boot, (check that as it's so long since I needed to do anything like that and can't remember the boot key shortcut).

That may give you a GUI but possibly at a very low resolution from which you can still install the best nvidia driver for your card.

Sorry I can't help more but as I say nvidia  cards are unknown to me.

---

### Post by bert89 on 2022-08-05
Try a cold boot and press the edit menu in the line, a silent splash ends and I added the word nomodest and it helped me and at the end f10 should help let me know how it will help you if not, you need to do something else

---

