---
title: "touchpad work incorrect"
date: 2019-09-22
forum: Hardware
---

### Post by andykuz on 2019-09-22
Hello, please hep.
I installed ubuntu on new laptop dell. Not working right click. After install ubuntu tweak tools - set check box in mouse click emulation in "Area". Right click start working but on left button and usualy click on right button of touchpad. Please help how can i change left and right button?

Thanks a lot.

```
user@dell-laptop:~$ inxi -Fxz
System:    Host: dell-laptop Kernel: 5.0.0-29-generic x86_64
           bits: 64 gcc: 7.4.0
           Desktop: Gnome 3.28.4 (Gtk 3.22.30-1ubuntu4)
           Distro: Ubuntu 18.04.3 LTS
Machine:   Device: laptop System: Dell product: Inspiron 3585 v: 1.0.0 serial: N/A
           Mobo: Dell model: 0CNMRV v: X01 serial: N/A
           UEFI: Dell v: 1.0.0 date: 11/20/2018
Battery    BAT1: charge: 30.1 Wh 73.6% condition: 40.9/42.0 Wh (97%)
           model: Simplo 0x320x380x330x350x000x000x0006 status: Discharging
CPU:       Quad core AMD Ryzen 5 2500U with Radeon Vega Mobile Gfx (-MT-MCP-) 
           arch: Zen rev.0 cache: 2048 KB
           
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 15969
           clock speeds: max: 2000 MHz 1: 1515 MHz 2: 1392 MHz 3: 1324 MHz
           4: 1361 MHz 5: 1478 MHz 6: 1356 MHz 7: 1628 MHz 8: 1574 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series]
           bus-ID: 04:00.0
           Display Server: x11 (X.Org 1.20.4 ) driver: amdgpu
           Resolution: 1920x1080@60.05hz
           OpenGL: renderer: AMD RAVEN (DRM 3.27.0, 5.0.0-29-generic, LLVM 8.0.0)
           version: 4.5 Mesa 19.0.2 Direct Render: Yes
Audio:     Card-1 Advanced Micro Devices [AMD] Device 15e3
           driver: snd_hda_intel bus-ID: 04:00.6
           Card-2 Advanced Micro Devices [AMD/ATI] Device 15de
           driver: snd_hda_intel bus-ID: 04:00.1
           Sound: Advanced Linux Sound Architecture v: k5.0.0-29-generic
Network:   Card-1: Realtek RTL810xE PCIE Fast Ethernet controller
           driver: r8169 port: 2000 bus-ID: 02:00.0
           IF: enp2s0 state: down mac: <filter>
           Card-2: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter
           driver: ath10k_pci bus-ID: 03:00.0
           IF: wlp3s0 state: up mac: <filter>
           Card-3: Atheros usb-ID: 003-004
           IF: N/A state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: 256.1GB (3.2% used)
           ID-1: /dev/nvme0n1 model: BC501_NVMe_SK_hynix_256GB size: 256.1GB
Partition: ID-1: / size: 234G used: 7.6G (4%) fs: ext4 dev: /dev/nvme0n1p2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: N/A mobo: N/A gpu: 56.0
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 300 Uptime: 15:17 Memory: 3088.7/5914.0MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.201) inxi: 2.3.56
```

---

### Post by andykuz on 2019-09-22
In settings of mouse was right mouse. Change to left to resolve my problem. Please close this topic. Sorry and thanks.

---

### Post by uRock on 2019-09-22
I'm glad you got that figured out.

To close the topic, please click on Thread Tools in the upper right and select to Mark as solved.

---

### Post by Jan_Johansson on 2019-11-03
> **andykuz said:**
> Hello, please hep.
I installed ubuntu on new laptop dell. Not working right click. After install ubuntu tweak tools - set check box in mouse click emulation in "Area". Right click start working but on left button and usualy click on right button of touchpad. Please help how can i change left and right button?



What do you mean by "set check box in mouse click emulation in "Area"? I have been looking through my Ubuntu tweak and can't find this "Area" anywhere, my version is 0,8,7 which one do you have?

My laptops right click stopped working after my girlfriend messed around with my laptop, it worked fine a few hours earlier, and I can't figure out how she disabled my right click. So replying to your thread seem in order as you have not closed it.

Jan

---

### Post by valereguerin on 2019-12-06
touchpad Lenovo Legion Y520



double click & click on touchpad doesn't work (scrolling with two finger is good....)```
System:    Host: whitehunter-Lenovo-Y520-15IKBN Kernel: 5.3.13-050313-generic x86_64 (other Kernel it's the same thing....)
           bits: 64
           Desktop: Xfce 4.12.3 Distro: Ubuntu 18.04.3 LTS
Machine:   Device: laptop System: LENOVO product: 80WK v: Lenovo Y520-15IKBN serial: N/A
           Mobo: LENOVO model: LNVNB161216 v: SDK0J40709 WIN serial: N/A
           UEFI: LENOVO v: 4KCN45WW date: 01/11/2019
Battery    BAT0: charge: 34.2 Wh 100.0% condition: 34.2/45.0 Wh (76%)
CPU:       Quad core Intel Core i5-7300HQ (-MCP-) cache: 6144 KB
           clock speeds: max: 3500 MHz 1: 1158 MHz 2: 2304 MHz 3: 2361 MHz
           4: 2528 MHz
Graphics:  Card-1: Intel Device 591b
           Card-2: NVIDIA GP107M [GeForce GTX 1050 Mobile]
           Display Server: x11 (X.Org 1.20.4 )
           drivers: modesetting,nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.02hz
           OpenGL: renderer: GeForce GTX 1050/PCIe/SSE2
           version: 4.6.0 NVIDIA 435.21
Audio:     Card Intel CM238 HD Audio Controller driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k5.3.13-050313-generic
Network:   Card-1: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter
           driver: ath10k_pci
           IF: wlp3s0 state: up mac: 64:6e:69:db:2f:45
           Card-2: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp4s0 state: down mac: 54:e1:ad:98:65:b6
           Card-3: Atheros
           IF: null-if-id state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: 3128.6GB (24.1% used)
           ID-1: /dev/nvme0n1 model: SAMSUNG_MZVLW128HEGR size: 128.0GB
           ID-2: /dev/sdb model: ST1000LM035 size: 1000.2GB
           ID-3: USB /dev/sda model: Expansion size: 2000.4GB
Partition: ID-1: / size: 192G used: 158G (87%) fs: ext4 dev: /dev/sdb3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 43.0C mobo: N/A gpu: 33C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 299 Uptime: 8:37 Memory: 2808.8/7853.4MB
           Client: Shell (bash) inxi: 2.3.56 
```



long time support....funny boy...

---

### Post by mörgæs on 2019-12-07
How does it work in a live boot of 19.10?

---

### Post by valereguerin on 2019-12-10
....18.04 isn't LTS ?....ON my Lenovo ! 
19.10????see my post about Security ...

---

