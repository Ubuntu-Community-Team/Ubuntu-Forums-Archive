---
title: "Biostar Racing X370GT7 with AMD Ryzen 7 2700X does not have  Power Supply Idle Contro"
date: 2019-04-30
forum: Hardware
---

### Post by Gustavo_Benedito_d on 2019-04-30
Hello,

I have recently purchased a new super PC. I have both Manjaro and Ubuntu. Observe that I am not a gamer. My computer details are: 


[LIST]
[*][B]Short details:
[/B] 
[/LIST]
[INDENT]**Processor:** AMD Ryzen 7 2700X
**Motherboard: **Biostar Racing X370 GT7
**Video card: **VGA Galax GTX 1660 6GB GDDR5
**RAM memory: **2x Memory Adata XPG 8GB DDR4 2666 MHz
**Energy/Power:** EVGA 450BT
**HDD: **Seagate Barracuda 2 TB
**SSD: **Adata 480 GB

[/INDENT]


[LIST]
[*]**Complete details:** 
[/LIST]
[INDENT]```

$ inxi -Fx
System:
  Host: gusbemacbe-amd Kernel: 5.0.0-13-generic x86_64 bits: 64 
  compiler: gcc v: 8.3.0 Desktop: Gnome 3.32.0 
  Distro: Ubuntu 19.04 (Disco Dingo) 
Machine:
  Type: Desktop Mobo: BIOSTAR model: X370GT7 serial: <root required> 
  UEFI: American Megatrends v: 5.13 date: 08/07/2018 
CPU:
  Topology: 8-Core model: AMD Ryzen 7 2700X bits: 64 type: MT MCP arch: Zen+ 
  rev: 2 L2 cache: 4096 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm 
  bogomips: 118159 
  Speed: 2069 MHz min/max: 2200/3700 MHz Core speeds (MHz): 1: 2025 2: 1967 
  3: 1883 4: 1895 5: 2195 6: 2195 7: 2195 8: 2193 9: 1888 10: 2044 11: 1884 
  12: 1892 13: 1887 14: 1897 15: 1901 16: 2041 
Graphics:
  Device-1: NVIDIA driver: nvidia v: 418.56 bus ID: 09:00.0 
  Display: x11 server: X.Org 1.20.4 driver: nvidia 
  unloaded: fbdev,modesetting,nouveau,vesa resolution: 1920x1080~60Hz 
  OpenGL: renderer: GeForce GTX 1660/PCIe/SSE2 v: 4.6.0 NVIDIA 418.56 
  direct render: Yes 
Audio:
  Device-1: NVIDIA driver: snd_hda_intel v: kernel bus ID: 09:00.1 
  Device-2: AMD Family 17h HD Audio vendor: Biostar Microtech Intl Corp 
  driver: snd_hda_intel v: kernel bus ID: 0b:00.3 
  Sound Server: ALSA v: k5.0.0-13-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Biostar Microtech Intl Corp driver: r8169 v: kernel port: f000 
  bus ID: 05:00.0 
  IF: enp5s0 state: down mac: b8:97:5a:ee:6e:4d 
  Device-2: Edimax type: USB driver: rt73usb bus ID: 5-1:2 
  IF: wlx001f1f63ecae state: up mac: 00:1f:1f:63:ec:ae 
Drives:
  Local Storage: total: 2.26 TiB used: 6.38 GiB (0.3%) 
  ID-1: /dev/sda vendor: Seagate model: ST2000DM008-2FR102 size: 1.82 TiB 
  temp: 37 C 
  ID-2: /dev/sdb vendor: A-Data model: SU630 size: 447.13 GiB temp: 43 C 
Partition:
  ID-1: / size: 423.89 GiB used: 6.31 GiB (1.5%) fs: ext4 dev: /dev/sdb3 
  ID-2: swap-1 size: 14.90 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sdb2 
Sensors:
  System Temperatures: cpu: 40.8 C mobo: N/A gpu: nvidia temp: 45 C 
  Fan Speeds (RPM): N/A gpu: nvidia fan: 0% 
Info:
  Processes: 404 Uptime: 12m Memory: 15.67 GiB used: 2.94 GiB (18.8%) 
  Init: systemd runlevel: 5 Compilers: gcc: 8.3.0 Shell: bash v: 5.0.3 
  inxi: 3.0.33 

```
[/INDENT]

I have already followed several instructions, but unsuccessfully:

1. [https://forum.manjaro.org/t/amd-ryzen-problems-and-fixes/55533](https://forum.manjaro.org/t/amd-ryzen-problems-and-fixes/55533)
2. [https://www.reddit.com/r/Amd/comments/6ox31y/what_is_the_state_of_ryzen_on_linux/](https://www.reddit.com/r/Amd/comments/6ox31y/what_is_the_state_of_ryzen_on_linux/)
3. [https://www.reddit.com/r/Amd/comments/99ge0t/ryzen_5_2400g_linux_compatibility/](https://www.reddit.com/r/Amd/comments/99ge0t/ryzen_5_2400g_linux_compatibility/)
4. [https://www.reddit.com/r/Amd/comments/6crru5/linux_instability_on_ryzen_7/](https://www.reddit.com/r/Amd/comments/6crru5/linux_instability_on_ryzen_7/)
5. [https://www.reddit.com/r/linuxhardware/comments/9y4bnw/are_there_any_problems_running_linux_on_ryzen/](https://www.reddit.com/r/linuxhardware/comments/9y4bnw/are_there_any_problems_running_linux_on_ryzen/)

---

### Post by TheFu on 2019-04-30
Did I miss a question?
Perhaps a newer firmware for the MB would help?   I know my Asus B450  has had 2 firmware updates since September. One in Dec18 and the other in Mar19.

---

### Post by Gustavo_Benedito_d on 2019-04-30
> **TheFu said:**
> Did I miss a question?
Perhaps a newer firmware for the MB would help?   I know my Asus B450  has had 2 firmware updates since September. One in Dec18 and the other in Mar19.

I want to change Power Supply Idle Control to Typical Current Idle, but Biostar Racing does not have this option. 

MB = megabyte?
Are you referring to Biostar Racing? And are you referring to "08/07/2018"?

---

### Post by Autodave on 2019-04-30
MB = mother board or BIOS update.

---

### Post by Gustavo_Benedito_d on 2019-04-30
> **Autodave said:**
> MB = mother board or BIOS update.

Do I have to use Windows to update BIOS? :-(

---

### Post by TheFu on 2019-04-30
> **Gustavo_Benedito_d said:**
> Do I have to use Windows to update BIOS? :-(

I didn't.  Modern motherboards usually have a way to upgrade the BIOS built-in.  Either directly using the network or from a USB flash drive.

---

### Post by Gustavo_Benedito_d on 2019-04-30
> **TheFu said:**
> I didn't.  Modern motherboards usually have a way to upgrade the BIOS built-in.  Either directly using the network or from a USB flash drive.

Can you explain how?

I watched the tutorial video, but I am afraid to do that, because he used a Dell laptop, different of the mine.

---

### Post by him610 on 2019-04-30
Check out your mainboard manual. There is normally a section dealing with BIOS updates. Biostar probably has instructions on its website.

---

### Post by Gustavo_Benedito_d on 2019-05-01
> **him610 said:**
> Check out your mainboard manual. There is normally a section dealing with BIOS updates. Biostar probably has instructions on its website.

I updated with the Biostar BIOS Flashed, but Biostar has informed that it is already the latest version. I decided to risk installing a BIOS file dated in March 2019, using Windows, but it did not work, because after installed and rebooted, Biostar reverted to the old BIOS file dated in 2018. No luck.

---

