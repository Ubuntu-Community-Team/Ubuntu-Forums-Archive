---
title: "Rapid battery drain on Acer Aspire E15 E5-573G-56KR with Ubuntu 16.04"
date: 2016-11-18
forum: Hardware
---

### Post by cypresstwist2 on 2016-11-18
I have an Acer Aspire E15 E5-573G-56KR laptop with Ubuntu 16.04 on it. My battery life is disastrous on it. I am supposed to get at least 5 hours of battery life and when I plug out the power connector my battery life drains extremely fast (about 10% every 5 minutes or so).
Also, most of the times I cannot resume from suspend and have to force reboot my system as the screen is blank when I open up the lid. Has anyone else had this problem?

---

### Post by ajgreeny on 2016-11-18
The model number does not really give us enough info about the specs of that laptop as manufacturers change a lot of things from time to time, so tell us more by copying back here the output of terminal command ```
inxi -F
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by cypresstwist2 on 2016-11-18
```
cypress@aspire:~$ **inxi -F**
System:    Host: aspire Kernel: 4.4.0-47-generic x86_64 (64 bit) Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   System: Acer product: Aspire E5-573G v: V3.72
           Mobo: Acer model: ZORO_BH v: Type2 - A01 Board Version Bios: Insyde v: V1.37 date: 02/16/2016
CPU:       Dual core Intel Core i5-4210U (-HT-MCP-) cache: 3072 KB 
           clock speeds: max: 2700 MHz 1: 2600 MHz 2: 2651 MHz 3: 2573 MHz 4: 2581 MHz
Graphics:  Card-1: Intel Haswell-ULT Integrated Graphics Controller
           Card-2: NVIDIA GK208M [GeForce 920M]
           Display Server: X.Org 1.18.4 driver: nvidia Resolution: 1366x768@60.00hz
           GLX Renderer: GeForce 920M/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 367.57
Audio:     Card-1 Intel 8 Series HD Audio Controller driver: snd_hda_intel Sound: ALSA v: k4.4.0-47-generic
           Card-2 Intel Haswell-ULT HD Audio Controller driver: snd_hda_intel
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
           IF: enp2s0 state: down mac: 54:ab:3a:5e:f8:c4
           Card-2: Qualcomm Atheros Device 0042 driver: ath10k_pci
           IF: wlp3s0 state: up speed: N/A duplex: N/A mac: c8:ff:28:1a:43:f5
Drives:    HDD Total Size: 500.1GB (17.6% used) ID-1: /dev/sda model: WDC_WD5000LPCX size: 500.1GB
Partition: ID-1: / size: 363G used: 79G (23%) fs: ext4 dev: /dev/sda2
           ID-2: swap-1 size: 4.21GB used: 0.50GB (12%) fs: swap dev: /dev/sda3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 51.0C mobo: N/A gpu: 42C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 262 Uptime: 17:50 Memory: 2977.6/3871.7MB Client: Shell (bash) inxi: 2.2.35 
```

---

### Post by ajgreeny on 2016-11-18
I suspect this is a graphic card problem, but as I have only ever used integrated cards, never nvidia, I can't really help more, I'm afraid.

Do you know if the graphics is "Optimus" technology, in which Windows can automatically move from the integrated Intel card to the nvidia card depending on the graphic requirements of whatever program you're running?

---

### Post by cypresstwist2 on 2016-11-18
The card supports Optimus technology.

---

### Post by richardsdma on 2016-11-18
I am sure that video driver is to blame for this. Video drivers are the weak link in the linux world.

---

### Post by ajgreeny on 2016-11-18
OK, as it's an optimus setup I believe you will need to look into installing bumblebee, or maybe nvidia-prime, though I am afraid I can't tell you how to use it, nor how close it gets to the Windows drivers for those cards.

---

### Post by cypresstwist2 on 2016-11-18
I disabled the NVidia Card in NVidia Settings and I am using the Intel one now. The battery life improved dramatically.

---

