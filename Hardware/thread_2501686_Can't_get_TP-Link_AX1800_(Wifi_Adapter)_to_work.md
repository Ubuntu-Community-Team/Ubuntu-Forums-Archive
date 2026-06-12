---
title: "Can't get TP-Link AX1800 (Wifi Adapter) to work"
date: 2024-10-17
forum: Hardware
---

### Post by mark-aber on 2024-10-17
Hi everyone,

I can't figure out why my wifi is not working.

I've bought an TP-Link AX1800 wifi stick and installed the following driver: [https://github.com/lwfinger/rtl8852au](https://github.com/lwfinger/rtl8852au).


lsusb
    ```
Bus 003 Device 003: ID 2357:013f TP-Link 802.11ac WLAN Adapter
```

lshw -C network
  ```
*-network
       description: Wireless interface
       physical id: 4
       bus info: usb@3:3
       logical name: wlx242fd016827b
       serial: 24:2f:d0:XX:XX:XX
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8852au driverversion=v1.15.0.1-0-g487ee886.20210714 firmware=N/A link=no multicast=yes wireless=unassociated
```

ip a
    ```
3: wlx242fd016827b: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
        link/ether <redacted> brd ff:ff:ff:ff:ff:ff
```
        
inxi --full --filter
    ```
System:
    Kernel: 6.8.0-45-generic arch: x86_64 bits: 64
    Console: pty pts/1 Distro: Ubuntu 24.04.1 LTS (Noble Numbat)
    Machine:
    Type: Desktop Mobo: ASRock model: B450M-HDV R4.0 serial: <filter> UEFI: American Megatrends
        v: P10.10 date: 01/24/2024
    CPU:
    Info: quad core model: AMD Ryzen 3 3200G with Radeon Vega Graphics bits: 64 type: MCP cache:
        L2: 2 MiB
    Speed (MHz): avg: 1400 min/max: 1400/3600 cores: 1: 1400 2: 1400 3: 1400 4: 1400
    Graphics:
    Device-1: AMD Picasso/Raven 2 [Radeon Vega Series / Radeon Mobile Series] driver: amdgpu
        v: kernel
    Display: server: No display server data found. Headless machine? tty: 316x90
        resolution: 1920x1080
    API: EGL v: 1.5 drivers: radeonsi,swrast platforms: surfaceless,device
    API: OpenGL v: 4.6 compat-v: 4.5 vendor: mesa v: 24.0.9-0ubuntu0.2 note: console (EGL sourced)
        renderer: AMD Radeon Vega 8 Graphics (radeonsi raven LLVM 17.0.6 DRM 3.57 6.8.0-45-generic),
        llvmpipe (LLVM 17.0.6 256 bits)
    Audio:
    Device-1: AMD Raven/Raven2/Fenghuang HDMI/DP Audio driver: snd_hda_intel
    Device-2: AMD Family 17h/19h HD Audio driver: snd_hda_intel
    API: ALSA v: k6.8.0-45-generic status: kernel-api
    Network:
    Device-1: Realtek RTL8111/8168/8211/8411 PCI Express Gigabit Ethernet driver: r8169
    IF: enp7s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
    Device-2: TP-Link 802.11ac WLAN Adapter driver: rtl8852au type: USB
    IF: wlx242fd016827b state: down mac: <filter>
    Drives:
    ID-1: /dev/sda vendor: Samsung model: SSD 840 EVO 120GB size: 111.79 GiB
    Partition:
    ID-1: / size: 53.21 GiB used: 11.51 GiB (21.6%) fs: ext4 dev: /dev/dm-0
    ID-2: /boot size: 1.9 GiB used: 182.5 MiB (9.4%) fs: ext4 dev: /dev/sda2
    ID-3: /boot/efi size: 1.05 GiB used: 6.1 MiB (0.6%) fs: vfat dev: /dev/sda1
    Swap:
    ID-1: swap-1 type: file size: 4 GiB used: 0 KiB (0.0%) file: /swap.img
    Info:
    Memory: total: 6 GiB available: 5.7 GiB used: 808.1 MiB (13.8%)
    Processes: 165 Uptime: 14m Init: systemd target: graphical (5) Shell: Bash inxi: 3.3.34
```
    


netplan --debug apply
    ```
** (generate:3592): DEBUG: 13:20:50.584: starting new processing pass
    ** (generate:3592): DEBUG: 13:20:50.584: wlx242fd016827b: adding wifi AP <redacted>
    ** (generate:3592): DEBUG: 13:20:50.584: We have some netdefs, pass them through a final round of validation
    ** (generate:3592): DEBUG: 13:20:50.584: wlx242fd016827b: setting default backend to 1
    ** (generate:3592): DEBUG: 13:20:50.584: Configuration is valid
    ** (generate:3592): DEBUG: 13:20:50.584: enp7s0: setting default backend to 1
    ** (generate:3592): DEBUG: 13:20:50.584: Configuration is valid
    ** (generate:3592): DEBUG: 13:20:50.585: Generating output files..
    ** (generate:3592): DEBUG: 13:20:50.585: Open vSwitch: definition enp7s0 is not for us (backend 1)
    ** (generate:3592): DEBUG: 13:20:50.585: NetworkManager: definition enp7s0 is not for us (backend 1)
    ** (generate:3592): DEBUG: 13:20:50.585: Creating wpa_supplicant config
    ** (generate:3592): DEBUG: 13:20:50.585: wlx242fd016827b: Creating wpa_supplicant configuration file run/netplan/wpa-wlx242fd016827b.conf
    ** (generate:3592): DEBUG: 13:20:50.585: Creating wpa_supplicant unit /run/systemd/system/netplan-wpa-wlx242fd016827b.service
    ** (generate:3592): DEBUG: 13:20:50.590: Creating wpa_supplicant service enablement link /run/systemd/system/systemd-networkd.service.wants/netplan-wpa-wlx242fd016827b.service
    ** (generate:3592): DEBUG: 13:20:50.590: Open vSwitch: definition wlx242fd016827b is not for us (backend 1)
    ** (generate:3592): DEBUG: 13:20:50.590: NetworkManager: definition wlx242fd016827b is not for us (backend 1)
    DEBUG:netplan generated networkd configuration changed, reloading networkd
    DEBUG:Cannot call Open vSwitch: Cannot apply OVS cleanup: ovsdb-server.service is 'not-found'.
    DEBUG:no netplan generated NM configuration exists
    ** (process:3591): DEBUG: 13:20:50.889: starting new processing pass
    ** (process:3591): DEBUG: 13:20:50.889: wlx242fd016827b: adding wifi AP <redacted>
    ** (process:3591): DEBUG: 13:20:50.889: We have some netdefs, pass them through a final round of validation
    ** (process:3591): DEBUG: 13:20:50.889: wlx242fd016827b: setting default backend to 1
    ** (process:3591): DEBUG: 13:20:50.889: Configuration is valid
    ** (process:3591): DEBUG: 13:20:50.889: enp7s0: setting default backend to 1
    ** (process:3591): DEBUG: 13:20:50.889: Configuration is valid
    DEBUG:Merged config:
    b''
    DEBUG:Link changes: {}
    DEBUG:netplan triggering .link rules for lo
    DEBUG:netplan triggering .link rules for enp7s0
    DEBUG:netplan triggering .link rules for wlx242fd016827b
    ** (process:3591): DEBUG: 13:20:50.970: starting new processing pass
    ** (process:3591): DEBUG: 13:20:50.970: wlx242fd016827b: adding wifi AP <redacted>
    ** (process:3591): DEBUG: 13:20:50.970: We have some netdefs, pass them through a final round of validation
    ** (process:3591): DEBUG: 13:20:50.970: wlx242fd016827b: setting default backend to 1
    ** (process:3591): DEBUG: 13:20:50.970: Configuration is valid
    ** (process:3591): DEBUG: 13:20:50.970: enp7s0: setting default backend to 1
    ** (process:3591): DEBUG: 13:20:50.970: Configuration is valid
    DEBUG:Merged config:
    b''

```

Carrier is still offline, no connection can be established with the existing wifi.

Any help is appreciated.

---

