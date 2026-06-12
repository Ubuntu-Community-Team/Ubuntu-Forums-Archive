---
title: "gpu is over heating"
date: 2020-07-15
forum: Hardware
---

### Post by mm1379 on 2020-07-15
hello
I have used thermal paste some parts temperature become better but some not
```
[FONT=monospace][COLOR=#000000]dell_smm-virtual-0[/COLOR]
Adapter: Virtual device
Processor Fan: 5177 RPM
CPU:            +54.0°C   
Other:          +47.0°C   
Other:          +47.0°C   
GPU:            +71.0°C   
Other:          +67.0°C   
Other:          +67.0°C   

coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +55.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:        +55.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:        +55.0°C  (high = +86.0°C, crit = +100.0°C)
Core 2:        +53.0°C  (high = +86.0°C, crit = +100.0°C)
Core 3:        +52.0°C  (high = +86.0°C, crit = +100.0°C)

[/FONT]
```
fan is always turning but it doesn't blow hot air 
the problem is gpu is over heating (it's intel hd 3000 integrated graphic)
how can i solve it?
kubuntu18.04

Edited:gpu in this log is the nvidia one I thought it's intel because I switched to intel .

---

### Post by Autodave on 2020-07-15
Is this a laptop or desk top?

71 C does not worry me at all.  Max temp for Intel GPUs is about 100 C.

---

### Post by mm1379 on 2020-07-15
Nope 
It was usually around 50 before
Laptop
[SIZE=3]is the gpu at the same place as cpu in an integrated graphic.?[/SIZE]

---

### Post by Autodave on 2020-07-15
I have no idea where it is located: sorry.  Tell me this: if you shut down the machine and let it cool off completely, what is the GPU and other temps like when you first start it back up?  You may have a sensor telling you false info.

---

### Post by Frogs Hair on 2020-07-15
> is the gpu at the same place as cpu in an integrated graphic.? > Integrated graphics refers to a computer where the graphics processing unit (GPU) is built onto the same die as the CPU. Dedicated graphics is a separate chip mounted on the mother-board or a pci mounted graphics card.

---

### Post by mm1379 on 2020-07-15
It's weird that if intel hd is built into the cpu why cpu is cooler than gpu?

---

### Post by mm1379 on 2020-07-15
No they change

---

### Post by Autodave on 2020-07-15
Once again, I do not believe that you have a problem.  You either have a sensor lieing to you or a program not interpreting the data correctly.  Worse case scenario is that you have a GPU that is operating normally.

---

### Post by mm1379 on 2020-07-17
How can i know?
After gpu overheating fan is working more.

---

### Post by poorguy on 2020-07-17
Hello mm1379,

Open the terminal and copy and paste this command [SIZE=3]**inxi -Fxz**[/SIZE] and post the output to a post.

What type of thermal paste did you use.

---

### Post by Yellow Pasque on 2020-07-17
> **mm1379 said:**
> It's weird that if intel hd is built into the cpu why cpu is cooler than gpu?

Different parts of the die can be at different temperatures.

---

### Post by mm1379 on 2020-07-18
```
$ inxi -Fxz
System:    Kernel: 5.4.0-40-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 Desktop: KDE Plasma 5.18.5 
           Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Portable System: Dell product: Inspiron N5110 v: N/A serial: <filter> 
           Mobo: Dell model: 0HVRTT v: A09 serial: <filter> BIOS: Dell v: A09 date: 09/30/2011 
CPU:       Topology: Quad Core model: Intel Core i7-2670QM bits: 64 type: MT MCP arch: Sandy Bridge rev: 7 L2 cache: 6144 KiB 
           flags: avx lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 35121 
           Speed: 950 MHz min/max: 800/3100 MHz Core speeds (MHz): 1: 869 2: 819 3: 859 4: 860 5: 801 6: 859 7: 811 8: 852 
Graphics:  Device-1: Intel 2nd Generation Core Processor Family Integrated Graphics vendor: Dell driver: i915 v: kernel 
           bus ID: 00:02.0 
           Device-2: NVIDIA GF108M [GeForce GT 525M] vendor: Dell driver: N/A bus ID: 01:00.0 
           Display: x11 server: X.Org 1.20.8 driver: modesetting unloaded: fbdev,vesa resolution: 1366x768~60Hz 
           OpenGL: renderer: Mesa DRI Intel HD Graphics 3000 (SNB GT2) v: 3.3 Mesa 20.0.8 direct render: Yes 
Audio:     Device-1: Intel 6 Series/C200 Series Family High Definition Audio vendor: Dell driver: snd_hda_intel v: kernel 
           bus ID: 00:1b.0 
           Device-2: NVIDIA GF108 High Definition Audio driver: snd_hda_intel v: kernel bus ID: 01:00.1 
           Sound Server: ALSA v: k5.4.0-40-generic 
Network:   Device-1: Realtek RTL810xE PCI Express Fast Ethernet vendor: Dell driver: r8169 v: kernel port: d000 
           bus ID: 05:00.0 
           IF: enp5s0 state: down mac: <filter> 
           Device-2: Qualcomm Atheros AR9285 Wireless Network Adapter vendor: Dell driver: ath9k v: kernel port: d000 
           bus ID: 09:00.0 
           IF: wlp9s0 state: up mac: <filter> 
           Device-3: Qualcomm Atheros AR3011 Bluetooth type: USB driver: btusb bus ID: 1-1.4:5 
Drives:    Local Storage: total: 698.64 GiB used: 49.29 GiB (7.1%) 
           ID-1: /dev/sda vendor: Western Digital model: WD7500BPVT-75HXZT3 size: 698.64 GiB temp: 43 C 
Partition: ID-1: / size: 76.40 GiB used: 8.70 GiB (11.4%) fs: ext4 dev: /dev/sda1 
           ID-2: /home size: 499.23 GiB used: 40.60 GiB (8.1%) fs: ext4 dev: /dev/sda3 
Sensors:   System Temperatures: cpu: 55.0 C mobo: N/A 
           Fan Speeds (RPM): cpu: 5174 
Info:      Processes: 219 Uptime: 52m Memory: 7.68 GiB used: 1.11 GiB (14.5%) Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 
           Shell: bash v: 5.0.17 inxi: 3.0.38 
```

It seems something went wrong: 
I understand that GPU temps belongs to nvidia (I thought it's intel because I have switched to intel) when I switch yo intel temperature stuck at about 75 c but in nvidia it rises until the laptop shutdowns 
in intel temps increases when i move mouse or... (when screen refresh a lot) 
now i have installed kubuntu

---

### Post by poorguy on 2020-07-18
Well by posting your specs I was hoping to find some operating specs of the graphics processor however no luck.

According to Intel spec sheet on the processor max temp is 100 degrees Celsius.

If everything is working good using the Intel graphics than stay with that one.


When using the Nvidia graphics you stated that  **"Nvidia it rises until the laptop shutdowns" **and that could possibly be a driver issue.
Have you looked in additional drivers and see if an Nvidia proprietary graphics driver is available and if there is have you installed it.

---

