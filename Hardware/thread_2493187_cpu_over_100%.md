---
title: "cpu over 100%"
date: 2023-12-06
forum: Hardware
---

### Post by fayda2 on 2023-12-06
Hi,
I want to know that if this is normal or not.. i have only brave opened and doing basic web browsing and youtube videos 
when i run top command sometimes i see over 100 in cpu usage

---

### Post by Frogs Hair on 2023-12-06
Hello and welcome fayda2,

Is this when running Brave ?

---

### Post by fayda2 on 2023-12-06
> **Frogs Hair said:**
> Hello and welcome fayda2,

Is this when running Brave ?
Yes and the cpu temp easily reaches over 80 .... tried firefox too and it's the same

---

### Post by Frogs Hair on 2023-12-06
Post the output of the following to provide system info.

```
inxi -Fxz
```

If inxi is not installed use the following first.

```
sudo apt install inxi
```

---

### Post by TheFu on 2023-12-06
If you have more than 1 core, numbers related to that total number of cores is to be expected.  Workload matters.  If youtube is providing a video in a way that your GPU doesn't handle in hardware, that leaves the CPU to perform the video decoding.

I have a 6 core (12 thread) system.  Using the 'uptime' command, it shows that is it busy now. Actually, very busy at least for the last 1, 5, and 15 minute periods show.
```
$ uptime 
 14:25:20 up 3 days,  3:43,  4 users,  load average: **11.62, 12.09, 11.85**
```

Busy, very, very, busy system.  Of course, that is batch processing so I gave it a lower priority to prevent the system from being unresponsive.

I would show the CPU temperatures, but my kernel doesn't support that. I know with an older Ryzen CPU that AMD automatically throttles at 95degC.  I can live with that.

As long as all your cores aren't pegged AND unresponsive, does it really matter?

---

### Post by fayda2 on 2023-12-07
```
System:
  Kernel: 6.2.0-37-generic x86_64 bits: 64 compiler: N/A Desktop: GNOME 42.9
    Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: ASUSTeK product: ASUS TUF Gaming F15 FX506HM_FX506HM
    v: 1.0 serial: <superuser required>
  Mobo: ASUSTeK model: FX506HM v: 1.0 serial: <superuser required>
    UEFI: American Megatrends LLC. v: FX506HM.315 date: 03/03/2023
Battery:
  ID-1: BAT1 charge: 71.6 Wh (100.0%) condition: 71.6/90.2 Wh (79.3%)
    volts: 16.5 min: 15.9 model: ASUS A32-K55 status: Full
CPU:
  Info: 8-core model: 11th Gen Intel Core i7-11800H bits: 64 type: MCP
    smt: disabled arch: Tiger Lake rev: 1 cache: L1: 640 KiB L2: 10 MiB
    L3: 24 MiB
  Speed (MHz): avg: 3193 high: 3942 min/max: 800/4600 cores: 1: 3942
    2: 3649 3: 2444 4: 3552 5: 3858 6: 1783 7: 3105 8: 3218 bogomips: 36864
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel TigerLake-H GT1 [UHD Graphics] vendor: ASUSTeK driver: i915
    v: kernel bus-ID: 00:02.0
  Device-2: NVIDIA GA106M [GeForce RTX 3060 Mobile / Max-Q] vendor: ASUSTeK
    driver: nvidia v: 535.129.03 bus-ID: 01:00.0
  Device-3: Sonix USB2.0 HD UVC WebCam type: USB driver: uvcvideo
    bus-ID: 3-7:3
  Display: x11 server: X.Org v: 1.21.1.4 driver: X:
    loaded: modesetting,nvidia unloaded: fbdev,nouveau,vesa gpu: i915
    resolution: 1920x1080~240Hz
  OpenGL: renderer: Mesa Intel UHD Graphics (TGL GT1)
    v: 4.6 Mesa 23.0.4-0ubuntu1~22.04.1 direct render: Yes
Audio:
  Device-1: Intel Tiger Lake-H HD Audio vendor: ASUSTeK driver: snd_hda_intel
    v: kernel bus-ID: 00:1f.3
  Device-2: NVIDIA vendor: ASUSTeK driver: snd_hda_intel v: kernel
    bus-ID: 01:00.1
  Sound Server-1: ALSA v: k6.2.0-37-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: MEDIATEK MT7921 802.11ax PCI Express Wireless Network Adapter
    vendor: AzureWave driver: mt7921e v: kernel bus-ID: 2e:00.0
  IF: wlp46s0 state: up mac: <filter>
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: ASUSTeK driver: r8169 v: kernel port: 3000 bus-ID: 2f:00.0
  IF: enp47s0 state: down mac: <filter>
  IF-ID-1: docker0 state: down mac: <filter>
  IF-ID-2: virbr0 state: down mac: <filter>
Bluetooth:
  Device-1: IMC Networks Wireless_Device type: USB driver: btusb v: 0.8
    bus-ID: 3-14:4
  Report: hciconfig ID: hci0 rfk-id: 0 state: down
    bt-service: enabled,running rfk-block: hardware: no software: yes
    address: <filter>
Drives:
  Local Storage: total: 476.94 GiB used: 40.15 GiB (8.4%)
  ID-1: /dev/nvme0n1 vendor: Intel model: SSDPEKNU512GZ size: 476.94 GiB
    temp: 20.9 C
Partition:
  ID-1: / size: 467.89 GiB used: 40.14 GiB (8.6%) fs: ext4
    dev: /dev/nvme0n1p2
  ID-2: /boot/efi size: 511 MiB used: 6.1 MiB (1.2%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 55.0 C mobo: 27.8 C
  Fan Speeds (RPM): cpu: 1900
Info:
  Processes: 296 Uptime: 13m Memory: 15.36 GiB used: 3.07 GiB (20.0%)
  Init: systemd runlevel: 5 Compilers: gcc: N/A Packages: 2106 Shell: Bash
  v: 5.1.16 inxi: 3.3.13
```

---

### Post by TheFu on 2023-12-07
a) whenever posting text output, please wrap it in 'code tags' and show the exact command used.  This always applies, not just this thread, but any threads past or future.

b) Appears to be a laptop with a Core i7 and onboard iGPU.  
Appears there's an nvidia GPU inside it with nvidia drivers.
16GB of RAM and just a 2GB swapfile.  That should be fine, though it isn't what I'd setup.

c) I'd setup the storage/partitions different too, but that's more about safety, backups, and OS upgrades than performance. Should be fine, performance-wise.

Ok, so there are some things to check.

Ensure that the nvidia GPU is actually being used.  I've never had a laptop with dual GPUs, so I don't know how to do that. I suspect it is pre-boot, in the BIOS, but I honestly don't know.

Ensure that whatever application you are using to watch videos is actually using hardware decoding from the GPU you intend.  This can change based on the video codec encoding, since hardware doesn't magically include the ability to decode any sort of video encodings.  For example, web browsers often default to CPU decoding of video because it is safer and less likely to crash the OS.  Different browsers will have different performance settings, so you'll need to check them all.  Or use a different program. I never use a web browser to watch videos, for example.

h.264 should always work and pretty much any GPU the last 8 yrs.  h.265 should work on your Nvidia 3xxx GPU, if the program doing the playback uses the GPU and not the CPU for decoding.

I realize this is all high-level stuff, not a detailed answer.  You have 8 cores, so does it really matter?  If it was using 800%, then I'd worry.

---

### Post by Yellow Pasque on 2023-12-07
I'd use htop if possible. That will report total CPU% from 0-100. Quick google says maybe you can do the same thing in top by entering capital i (Shift + i)

> **TheFu said:**
> Ensure that the nvidia GPU is actually being used.  I've never had a laptop with dual GPUs, so I don't know how to do that. I suspect it is pre-boot, in the BIOS, but I honestly don't know.

There's probably no convenient graphics switch in the BIOS/EFI. Nowadays, it seems like everything is muxless and done through the OS. Anyway, it's probably not a good idea to use Nvidia for general web browsing and video accel. Modern Intel chips do that very efficiently assuming VA-API is working correctly:
```
vainfo
```

EDIT: you may also want to see if hardware accelerated video is available in your browser, by entering this in the address bar:
```
brave://gpu
```

---

### Post by TheFu on 2023-12-07
I don't use htop.  It is pretty, but **glances** has more system-wide information.

**top** and **glances** and **free** are my normal tools ... if I don't go into **munin** for full monitoring reports.  Only admins would likely setup munin.  I like the historical data and seeing information for the last day, week, month, 6 months year, or longer.

---

### Post by SeijiSensei on 2023-12-08
Run top, then type "1". This will show the load on every core like this:
```

%Cpu0  :  0.3 us,  0.7 sy,  0.0 ni, 99.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
%Cpu1  :  0.3 us,  0.0 sy,  0.0 ni, 99.3 id,  0.3 wa,  0.0 hi,  0.0 si,  0.0 st 
%Cpu2  :  1.7 us,  0.3 sy,  0.0 ni, 98.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
%Cpu3  :  4.0 us,  1.7 sy,  0.0 ni, 93.3 id,  1.0 wa,  0.0 hi,  0.0 si,  0.0 st 

```

---

