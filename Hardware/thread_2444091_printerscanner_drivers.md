---
title: "printer/scanner drivers"
date: 2020-05-24
forum: Hardware
---

### Post by jp41 on 2020-05-24
hello all
I've just switched over to xubuntu coming from mint.
the problem i now have is that my canon pixma mg2400 printer/scanner/copier doesn't have any drivers and the only driver it shows when i do a search for additional drivers is generic driver that only prints text.
no drivers for the scanner either.
i had the same problem in mint ,could never get the scanner to work. I've tried all the advice and internet searches nothing worked.
anyone has a clue for me on how to get printer/scanner to work?

```
jp@jp:~$ inxi -FxzdSystem:    Kernel: 5.4.0-31-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 Desktop: Xfce 4.14.2 
           Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ECS model: G31T-M7 v: 1.0 serial: <filter> BIOS: American Megatrends v: 080014 date: 02/25/2010 
CPU:       Topology: Dual Core model: Pentium E5300 bits: 64 type: MCP arch: Penryn rev: A L2 cache: 2048 KiB 
           flags: lm nx pae sse sse2 sse3 ssse3 vmx bogomips: 10373 
           Speed: 1197 MHz min/max: 1203/2603 MHz Core speeds (MHz): 1: 1197 2: 1215 
Graphics:  Device-1: NVIDIA GT218 [GeForce 210] vendor: ASUSTeK EN210 SILENT driver: nvidia v: 340.108 bus ID: 01:00.0 
           Display: x11 server: X.Org 1.20.8 driver: nvidia unloaded: fbdev,modesetting,nouveau,vesa resolution: 1600x900~60Hz 
           OpenGL: renderer: GeForce 210/PCIe/SSE2 v: 3.3.0 NVIDIA 340.108 direct render: Yes 
Audio:     Device-1: Intel NM10/ICH7 Family High Definition Audio vendor: Elite Systems driver: snd_hda_intel v: kernel 
           bus ID: 00:1b.0 
           Device-2: NVIDIA High Definition Audio vendor: ASUSTeK driver: snd_hda_intel v: kernel bus ID: 01:00.1 
           Sound Server: ALSA v: k5.4.0-31-generic 
Network:   Device-1: Qualcomm Atheros Attansic L2 Fast Ethernet vendor: Elite Systems driver: atl2 v: 2.2.3 port: ec00 
           bus ID: 02:00.0 
           IF: ens32 state: up speed: 100 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 465.76 GiB used: 202.51 GiB (43.5%) 
           ID-1: /dev/sda vendor: Samsung model: HD503HI size: 465.76 GiB 
           Floppy-1: /dev/fd0 
           Optical-1: /dev/sr0 vendor: HL-DT-ST model: DVDRAM GH22NS40 rev: NL01 dev-links: cdrom,cdrw,dvd,dvdrw 
           Features: speed: 48 multisession: yes audio: yes dvd: yes rw: cd-r,cd-rw,dvd-r,dvd-ram state: running 
Partition: ID-1: / size: 456.95 GiB used: 202.51 GiB (44.3%) fs: ext4 dev: /dev/sda5 
Sensors:   System Temperatures: cpu: 59.0 C mobo: N/A gpu: nvidia temp: 68 C 
           Fan Speeds (RPM): N/A 
Info:      Processes: 173 Uptime: 9h 26m Memory: 2.92 GiB used: 956.8 MiB (32.0%) Init: systemd runlevel: 5 Compilers: 
           gcc: 9.3.0 Shell: bash v: 5.0.16 inxi: 3.0.38 
jp@jp:~$ 



```


ps. printer not connected when i did that inxi -Fxzd

---

### Post by kurt18947 on 2020-05-24
Have you search in these forums for your printer model? Sometimes someone else has solved what you're trying to do.  If you can't find anything useful, here's something to consider. Some printers have driverless printing/scanning. Here's how to tell about yours. I'll post a link to a thread, post #14 has the terminal commands. The topic is Samsung Multi-Function but Canon should be similar, Most if not all printers use CUPS (Common Unix Printing System) which is part of the Ubuntu distro.

```
https://ubuntuforums.org/showthread.php?t=2443539&page=2

```
If those are not helpful, here's something else you can try. I do not have any Canon devices so no experience. If you're not in the U.S., you could search for something like "linux+canon printer drivers". 

```
https://www.usa.canon.com/internet/portal/us/home/products/details/software/device-management/codehost-unix-linux-printing-with-brightq-pro
```

---

### Post by jp41 on 2020-05-26
ok i've done things like in [this]("https://ubuntuforums.org/showthread.php?t=2232486&highlight=canon+pixma+mg2400") thread and install the drivers for printer and scanner.
haven't treid printer yet cause ink is finished but if i try scanning with scangear i get error message (as in pic)


[IMG]https://i.ibb.co/wrXgz6D/Screenshot-2020-05-26-19-40-46.jpg[/IMG]




where to from here ?

---

### Post by jp41 on 2020-05-26
> **kurt18947 said:**
> Have you search in these forums for your printer model? Sometimes someone else has solved what you're trying to do.  If you can't find anything useful, here's something to consider. Some printers have driverless printing/scanning. Here's how to tell about yours. I'll post a link to a thread, post #14 has the terminal commands. The topic is Samsung Multi-Function but Canon should be similar, Most if not all printers use CUPS (Common Unix Printing System) which is part of the Ubuntu distro.<br>
<br>
```
https://ubuntuforums.org/showthread.php?t=2443539&amp;page=2<br>

```<br>
If those are not helpful, here's something else you can try. I do not have any Canon devices so no experience. If you're not in the U.S., you could search for something like "linux+canon printer drivers". <br>
<br>
```
https://www.usa.canon.com/internet/portal/us/home/products/details/software/device-management/codehost-unix-linux-printing-with-brightq-pro
```<br>
<br><br>did the commands...apparently my printer /scanner isin't driverless.<br><br>

---

