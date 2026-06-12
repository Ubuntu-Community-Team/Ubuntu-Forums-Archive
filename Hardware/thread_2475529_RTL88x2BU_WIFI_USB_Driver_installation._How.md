---
title: "RTL88x2BU WIFI USB Driver installation. How?"
date: 2022-05-30
forum: Hardware
---

### Post by ax3lpl on 2022-05-30
I don't know anything about Ubuntu and I would like to install wifi usb, what should I do? Can anyone write CLEAR STEP BY STEP what a Linux user (who is not familiar with commands, programming) should do to install this device?

---

### Post by ajgreeny on 2022-05-30
We need to know a lot more about your system to be able to help you better so please show us the output from terminal command
***inxi -Fzx***
Please use Code Tags for the output.
See my signature below for a How-To if you don't know what that means.

There is also information about wireless networking at [https://ubuntuforums.org/forumdisplay.php?f=336](https://ubuntuforums.org/forumdisplay.php?f=336)

---

### Post by ax3lpl on 2022-05-30
```
***inxi -Fzx***
```

output:
```
System:  Kernel: 5.13.0-40-generic x86_64 bits: 64 compiler: gcc v: 11.2.0
    Desktop: GNOME 40.5 Distro: Ubuntu 21.10 (Impish Indri)
Machine:
  Type: Desktop Mobo: Gigabyte model: H61M-D2-B3 serial: <superuser required>
    BIOS: Award v: F3 date: 02/22/2011
CPU:
  Info: dual core model: Intel Core i3-2100 bits: 64 type: MT MCP
    arch: Sandy Bridge rev: 7 cache: L1: 128 KiB L2: 512 KiB L3: 3 MiB
  Speed (MHz): avg: 2418 high: 2690 min/max: 1600/3100 cores: 1: 2690
    2: 2631 3: 2586 4: 1765 bogomips: 24743
  Flags: avx ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: AMD Redwood XT [Radeon HD 5670/5690/5730]
    vendor: Hightech Information System driver: radeon v: kernel
    bus-ID: 01:00.0
  Display: wayland server: X.Org v: 1.21.1.2 with: Xwayland v: 21.1.2
    compositor: gnome-shell driver: X: loaded: ati,radeon
    unloaded: fbdev,modesetting,vesa gpu: radeon resolution: 1360x768~60Hz
  OpenGL:
    renderer: AMD REDWOOD (DRM 2.50.0 / 5.13.0-40-generic LLVM 12.0.1)
    v: 3.3 Mesa 21.2.6 direct render: Yes
Audio:
  Device-1: Intel 6 Series/C200 Series Family High Definition Audio
    vendor: Gigabyte driver: snd_hda_intel v: kernel bus-ID: 00:1b.0
  Device-2: AMD Redwood HDMI Audio [Radeon HD 5000 Series]
    vendor: Hightech Information System driver: snd_hda_intel v: kernel
    bus-ID: 01:00.1
  Sound Server-1: ALSA v: k5.13.0-40-generic running: yes
  Sound Server-2: PulseAudio v: 15.0 running: yes
  Sound Server-3: PipeWire v: 0.3.32 running: yes
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: Gigabyte driver: r8169 v: kernel port: ee00 bus-ID: 03:00.0
  IF: enp3s0 state: down mac: <filter>
  IF-ID-1: pan1 state: down mac: <filter>
  IF-ID-2: usb0 state: unknown speed: -1 duplex: half mac: <filter>
Bluetooth:
  Device-1: Cambridge Silicon Radio Bluetooth Dongle (HCI mode) type: USB
    driver: btusb v: 0.8 bus-ID: 2-1.5:3
  Report: hciconfig ID: hci0 rfk-id: 0 state: down
    bt-service: enabled,running rfk-block: hardware: no software: yes
    address: <filter>
Drives:
  Local Storage: total: 931.51 GiB used: 51.22 GiB (5.5%)
  ID-1: /dev/sda vendor: Seagate model: ST31000524AS size: 931.51 GiB
Partition:
  ID-1: / size: 182.34 GiB used: 51.22 GiB (28.1%) fs: ext4 dev: /dev/sda6
  ID-2: /boot/efi size: 61.13 GiB used: 5.5 MiB (0.0%) fs: vfat
    dev: /dev/sda1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 143.7 MiB (7.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 50.0 C mobo: N/A gpu: radeon temp: 47.0 C
  Fan Speeds (RPM): N/A
Info:
  Processes: 330 Uptime: 4h 29m Memory: 7.75 GiB used: 5.25 GiB (67.8%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.2.0 Packages: 2294 Shell: Bash
  v: 5.1.8 inxi: 3.3.13



```

---

### Post by mIk3_08 on 2022-05-31
> **ax3lpl said:**
> I don't know anything about Ubuntu and I would like to install wifi usb, what should I do? Can anyone write CLEAR STEP BY STEP what a Linux user (who is not familiar with commands, programming) should do to install this device? If you haven't bought any WIFI USB yet. My advice to you is, There are WIFI USB devices supported by Linux. They are plug and play so you don't get any issue when installing it. Others have included driver software in package so you just have to follow the instructions for installation. Good Luck and Cheers.

---

### Post by mIk3_08 on 2022-05-31
I was not able to noticed the title of your thread post that you already have this "RTL88x2BU WIFI USB"  Apology. My bad. Just wanna ask if this device is supported by Linux?  And I saw there are some RinCat in git a driver for this device.  I don't know if it works since I don't have this kind of device. so just see it by yourself in git. Regards and cheers.

---

### Post by ax3lpl on 2022-05-31
> **mIk3_08 said:**
> If you haven't bought any WIFI USB yet. My advice to you is, There are WIFI USB devices supported by Linux. They are plug and play so you don't get any issue when installing it. Others have included driver software in package so you just have to follow the instructions for installation. Good Luck and Cheers.

> **mIk3_08 said:**
> I was not able to noticed the title of your thread post that you already have this "RTL88x2BU WIFI USB"  Apology. My bad. Just wanna ask if this device is supported by Linux?  And I saw there are some RinCat in git a driver for this device.  I don't know if it works since I don't have this kind of device. so just see it by yourself in git. Regards and cheers.

Look, I'm on the UBUNTU forum, I didn't go to the forum about baking cakes or folding paper planes. I entered the UBUNTU forum. I would like to install a USB dongle from a very well-known manufacturer, REALTEK. How to do it? Is the installation of regular WIFI USB too complicated? How do I know if it is or is not on some list? I am not interested in it, I would like to install a driver for a device that is a UNIVERSAL Plug & Play device, is linux a windows 3.11 system that nothing works on it? I can't understand why can't a simple device be installed? Is ubuntu an archaic operating system? Or maybe he left yesterday and nobody knows how to operate it? Or maybe you need a PhD or a professorship in computer science to install a USB device? Or maybe LINUX IS SO STUPID OPERATING SYSTEM THAT NOTHING CAN BE DONE WITHOUT BEING AN IT PROGRAM PROGRAMMER?

---

### Post by howefield on 2022-05-31
You have two threads, both of which have very quickly become unproductive.

Perhaps you could beg whomever sold/gave you the machine to take it back, for reasons which may be obvious. Or you could read the forums [Code of Conduct ]("https://ubuntuforums.org/misc.php?do=showrules")and the associated posting tips, then come back and try again. 

In the meantime, thread closed.

---

