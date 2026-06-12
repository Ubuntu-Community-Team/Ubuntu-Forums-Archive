---
title: "Random Reboots with Hardware Error only on Ubuntu"
date: 2023-06-06
forum: Hardware
---

### Post by zckaufman on 2023-06-06
I am using Ubuntu 20.04 on my custom built PC and I replaced my CPU recently. Ever since I installed it my computer freezes and randomly reboots every 5-15 minutes with seemingly no rhyme or reason. During the reboot some Hardware Errors pop up on the screen and they are also visible in the Logs app after the reboot. They suggest the issue is with the CPU, so with that in mind I replaced the CPU with an old one to see if that was the issue and there were no more reboots. So I put in a warranty request with AMD and they shipped me a new one, but now that I put the new one into the machine I get the exact same issue. HOWEVER, I also have Windows 11 installed on this machine for work and when I am running Windows this never happens. So it only happens when using my new CPU on Ubuntu 20.04. Can anyone give me recommendations on what could be wrong? Thank you for any and all suggestions. 

Also, as part of the troubleshooting process I confirmed that I go nowhere near the max power usage or have any CPU temperature spikes.

PC Specs:
CPU - AMD Ryzen 9 5950X
GPUs - Nvidia RTX 2070 and RTX 3080
PSU - Corsair RM850x Gold
Motherboard - Asus TUF Gaming X570-Plus (WIFI) 
BIOS Version - 4602

---

### Post by tea for one on 2023-06-07
For a newish CPU, perhaps the kernel in 20.04 may not be the optimum choice?
A simple test would be to download and run a 2-3 hour live session of Ubuntu 22.04.

---

### Post by ajgreeny on 2023-06-07
What nvidia graphics driver are you using for the nvidia card, and have you really got two cards in the system?

Lets see the output of terminal command ```
inxi -Fzx
```
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by zckaufman on 2023-06-07
> **tea for one said:**
> For a newish CPU, perhaps the kernel in 20.04 may not be the optimum choice?
A simple test would be to download and run a 2-3 hour live session of Ubuntu 22.04.


Thank you for the suggestion! I will give it a shot. If I was to switch to Ubuntu 22.04 would I need to use a new install or could I upgrade using the terminal in Ubuntu 20.04?

---

### Post by zckaufman on 2023-06-07
> **ajgreeny said:**
> What nvidia graphics driver are you using for the nvidia card, and have you really got two cards in the system?

Lets see the output of terminal command ```
inxi -Fzx
```
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

I do have two cards in the system, and when I use Blender both are recognized, however, when looking at my drivers the system only shows the 2070. Below is the output of running that command. Thank you!

```

System:    Kernel: 5.15.0-73-generic x86_64 bits: 64 compiler: N/A Desktop: Gnome 3.36.9 
           Distro: Ubuntu 20.04.6 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASUSTeK model: TUF GAMING X570-PLUS (WI-FI) v: Rev X.0x serial: <filter> 
           UEFI: American Megatrends v: 4602 date: 02/23/2023 
CPU:       Topology: 16-Core model: AMD Ryzen 9 5950X bits: 64 type: MT MCP arch: Zen 3 rev: 2 L2 cache: 8192 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm bogomips: 217195 
           Speed: 4032 MHz min/max: 2200/3400 MHz Core speeds (MHz): 1: 4019 2: 5041 3: 2192 4: 2194 5: 2189 6: 2193 7: 2192 
           8: 2194 9: 4027 10: 5040 11: 4025 12: 4032 13: 4032 14: 4032 15: 4026 16: 4030 17: 4030 18: 2187 19: 2192 20: 2195 
           21: 2190 22: 2190 23: 2193 24: 4032 25: 2194 26: 2191 27: 3039 28: 3812 29: 3968 30: 3951 31: 2191 32: 2189 
Graphics:  Device-1: NVIDIA TU106 [GeForce RTX 2070] vendor: Gigabyte driver: N/A bus ID: 03:00.0 
           Display: x11 server: X.Org 1.20.13 driver: fbdev,nouveau unloaded: modesetting,vesa resolution: 3840x2160~88Hz 
           OpenGL: renderer: llvmpipe (LLVM 12.0.0 256 bits) v: 4.5 Mesa 21.2.6 direct render: Yes 
Audio:     Device-1: NVIDIA TU106 High Definition Audio vendor: Gigabyte driver: snd_hda_intel v: kernel bus ID: 03:00.1 
           Device-2: Advanced Micro Devices [AMD] Starship/Matisse HD Audio vendor: ASUSTeK driver: snd_hda_intel v: kernel 
           bus ID: 0a:00.4 
           Sound Server: ALSA v: k5.15.0-73-generic 
Network:   Device-1: Intel Wireless-AC 9260 driver: iwlwifi v: kernel port: f000 bus ID: 04:00.0 
           IF: wlp4s0 state: up mac: <filter> 
           Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet vendor: ASUSTeK driver: r8169 v: kernel port: e000 
           bus ID: 05:00.0 
           IF: enp5s0 state: down mac: <filter> 
Drives:    Local Storage: total: 2.73 TiB used: 323.66 GiB (11.6%) 
           ID-1: /dev/sda vendor: Samsung model: SSD 870 EVO 2TB size: 1.82 TiB 
           ID-2: /dev/sdb vendor: Samsung model: SSD 860 EVO 1TB size: 931.51 GiB 
Partition: ID-1: / size: 915.32 GiB used: 323.63 GiB (35.4%) fs: ext4 dev: /dev/sdb2 
Sensors:   System Temperatures: cpu: 32.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Info:      Processes: 581 Uptime: 5m Memory: 31.25 GiB used: 4.34 GiB (13.9%) Init: systemd runlevel: 5 Compilers: gcc: 9.4.0 
           Shell: zsh v: 5.8 inxi: 3.0.38 


```

---

### Post by ajgreeny on 2023-06-07
It seems you are not using an nvidia driver at all but the system's own open source driver
```
Graphics:  Device-1: NVIDIA TU106 [GeForce RTX 2070] vendor: Gigabyte driver: N/A bus ID: 03:00.0 
           Display: x11 server: X.Org 1.20.13 driver: fbdev,nouveau unloaded: modesetting,vesa resolution: 3840x2160~88Hz 
           OpenGL: renderer: llvmpipe (LLVM 12.0.0 256 bits) v: 4.5 Mesa 21.2.6 direct render: Yes 
```
I have never used nvidia graphics so I'm not sure what is best for you other than looking in your menu system for ***Additional Drivers*** to see if anything is offered as the default for that card.

I also have no idea if the two cards present in the system confuses things as a possible problem for you, so wait for more replies.

---

### Post by zckaufman on 2023-06-07
I get the random shutdowns even when just using one card. I've tried using both of them individually so I don't think the graphics cards are the issues.

---

