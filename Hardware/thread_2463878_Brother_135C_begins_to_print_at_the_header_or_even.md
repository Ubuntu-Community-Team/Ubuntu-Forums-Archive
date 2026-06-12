---
title: "Brother 135C begins to print at the header or even above"
date: 2021-06-20
forum: Hardware
---

### Post by pryb on 2021-06-20
Hello,
I have a poblem with my Brother 135C on Ubuntu 20.04. It has been installed correctly according to the guide on the producer site. But it starts printing text at the header or even higher because the begining of the text is cut off and then continue at the header and goes on through the whole sheet of paper. Does anyone had a similar problem?

---

### Post by brian_p on 2021-06-20
> **pryb said:**
> Hello,
I have a poblem with my Brother 135C on Ubuntu 20.04. It has been installed correctly according to the guide on the producer site. But it starts printing text at the header or even higher because the begining of the text is cut off and then continue at the header and goes on through the whole sheet of paper. Does anyone had a similar problem?

What are you printing and what application is being used?

---

### Post by pryb on 2021-06-20
To be honest it doesn't matter. It can be Open Office, Libre Office, PDF file etc. Result is always the same.

---

### Post by him610 on 2021-06-20
Sounds as if you may have installed incorrect drivers, or you may have wrong page size specified in print device. (just guessing with those thoughts) 
I have a Brother MFC-7360N that I have never had any issues with. Yours is connected using a USB cable with which I have no experience. 

Did you download the correct Linux Debian software from the Brother website, [https://support.brother.com/g/b/downloadlist.aspx?c=gb&lang=en&prod=dcp135c_eu_as&os=128]("https://support.brother.com/g/b/downloadlist.aspx?c=gb&lang=en&prod=dcp135c_eu_as&os=128")
The 'Driver Install Tool' is all you should need to properly install the software.

What are the specs of your computer? Please show results (between code tags)  of....
```
inxi -Fxz
```

---

### Post by pryb on 2021-06-21
I've installed driver correctly from the site you mentioned. All the setting are also correct. No idea what to do. ```
System:    Kernel: 5.8.0-55-generic x86_64 bits: 64 compiler: N/A Desktop: Xfce 4.14.2            Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:   Type: Portable System: Dell product: Studio 1555 v: A13 serial: <filter> 
           Mobo: Dell model: 0J276M v: A13 serial: <filter> BIOS: Dell v: A13 date: 04/02/2011 
Battery:   ID-1: BAT0 charge: 3.5 Wh condition: 3.5/4.4 Wh (80%) model: SDI Dell status: Full 
           Device-1: hidpp_battery_0 model: Logitech Wireless Gaming Mouse charge: 55% (should be ignored) status: Discharging 
CPU:       Topology: Dual Core model: Intel Core2 Duo P8800 bits: 64 type: MCP arch: Penryn rev: A L2 cache: 3072 KiB 
           flags: lm nx pae sse sse2 sse3 sse4_1 ssse3 vmx bogomips: 10640 
           Speed: 798 MHz min/max: 800/2667 MHz Core speeds (MHz): 1: 798 2: 798 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] RV710/M92 [Mobility Radeon HD 4530/4570/545v] vendor: Dell 
           driver: radeon v: kernel bus ID: 01:00.0 
           Display: x11 server: X.Org 1.20.9 driver: ati,radeon unloaded: fbdev,modesetting,vesa resolution: 1366x768~60Hz 
           OpenGL: renderer: AMD RV710 (DRM 2.50.0 / 5.8.0-55-generic LLVM 11.0.0) v: 3.3 Mesa 20.2.6 direct render: Yes 
Audio:     Device-1: Intel 82801I HD Audio vendor: Dell driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
           Device-2: Advanced Micro Devices [AMD/ATI] RV710/730 HDMI Audio [Radeon HD 4000 series] vendor: Dell 
           driver: snd_hda_intel v: kernel bus ID: 01:00.1 
           Sound Server: ALSA v: k5.8.0-55-generic 
Network:   Device-1: Qualcomm Atheros AR9285 Wireless Network Adapter vendor: Foxconn driver: ath9k v: kernel port: 2000 
           bus ID: 04:00.0 
           IF: wlp4s0 state: up mac: <filter> 
           Device-2: Broadcom and subsidiaries NetLink BCM5784M Gigabit Ethernet PCIe vendor: Dell driver: tg3 v: kernel 
           port: 2000 bus ID: 08:00.0 
           IF: enp8s0 state: down mac: <filter> 
           Device-3: Dell Wireless 370 Bluetooth Mini-card type: USB driver: btusb bus ID: 3-1.3:5 
           Device-4: Qualcomm Atheros AR3011 Bluetooth type: USB driver: btusb bus ID: 8-1:3 
Drives:    Local Storage: total: 342.81 GiB used: 96.82 GiB (28.2%) 
           ID-1: /dev/sda vendor: GOODRAM model: N/A size: 223.57 GiB temp: 30 C 
           ID-2: /dev/sdb type: USB vendor: Transcend model: TS128GSSD370S size: 119.24 GiB 
Partition: ID-1: / size: 37.30 GiB used: 6.16 GiB (16.5%) fs: ext4 dev: /dev/sda1 
           ID-2: /home size: 174.00 GiB used: 288.9 MiB (0.2%) fs: ext4 dev: /dev/sda6 
           ID-3: swap-1 size: 7.63 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda5 
Sensors:   System Temperatures: cpu: 63.0 C mobo: N/A gpu: radeon temp: 57 C 
           Fan Speeds (RPM): cpu: 2837 fan-2: 2833 fan-3: 2829 
Info:      Processes: 209 Uptime: 26m Memory: 3.81 GiB used: 1.53 GiB (40.1%) Init: systemd runlevel: 5 Compilers: gcc: N/A 
           Shell: bash v: 5.0.17 inxi: 3.0.38 



```

---

### Post by him610 on 2021-06-22
How about running this from terminal and posting results...
```
dpkg -l | grep Brother 
```

---

### Post by pryb on 2021-06-29
Here it is.

```

ii  brscan-skey                           0.3.1-2                             amd64        Brother Linux scanner S-KEY tool
ii  brscan2                               0.2.5-1                             amd64        Brother Scanner Driver
ii  dcp135ccupswrapper:i386               1.0.1-1                             i386         Brother CUPS Inkjet Printer Definitions
ii  dcp135clpr:i386                       1.0.1-1                             i386         Brother lpr Inkjet Printer Definitions
ii  printer-driver-brlaser                6-1build1                           amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                 1.4.2-3                             amd64        printer driver Brother P-touch label printers



```

---

### Post by kurt18947 on 2021-06-29
I have an old Brother machine, MFC-6490CW that doesn't format pages properly when used with certain apps, particularly outlook in office365. What I need to do in those cases is to print to file (create a pdf file) then open and print the pdf file. Then it prints properly. I also have problems when printing envelopes, I ask for #10 envelope and it selects the next envelope after #10. I do have a couple other printers including a Brother HL-3170 which do work properly. It's a driver problem (from Brother) that I have no hope of being fixed as the machine has been out of production for years.

---

