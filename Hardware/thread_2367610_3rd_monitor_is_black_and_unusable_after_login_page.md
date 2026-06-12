---
title: "3rd monitor is black and unusable after login page"
date: 2017-08-01
forum: Hardware
---

### Post by chrysstyann on 2017-08-01
Hello all,

I'm trying to find a topic related to my issue for a few hours by now and nothing...

I have a Dell Precision M4800 (2 SSDs, 16GB RAM, Quadro K1100)
I have 3 monitors: 2x UZ2315H and 1x P2217H
My laptop is connected to a docking station PR02X which has 3 video ports:
- Video 1: DVI or DisplayPort &#8211; Dell UZ2315H connected; 
- Video 2: DVI or DisplayPort &#8211; Dell UZ2315H connected;
- Video 3: VGA &#8211; Dell P2217H connected;

Ubuntu 16.04 2 LTS - 4.10.0-28-generic #32~16.04.2-Ubuntu SMP Thu Jul 20 10:19:48 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

I am trying to activate all 3 monitors but I'm not able to do that.

Using NVIDIA binary driver &#8211; version 375.66 from nvidia-375 (proprietary, tested)
All Settings &#8594; Displays:
- all monitors are discovered and ON;
- all monitors are set to 1920x1080;

- when I'm in login page I can see all 3 monitors in extended mode (I can move my mouse over all 3 monitors);
- after login, the 3rd one (VGA one) turns black, I can move my mouse over it but I can't use it (no windows to put on it);


Using X.Org X server &#8211; Noveau display driver from xserver-xorg-video-noveau (open source)
All Settings &#8594; Displays:
- all monitors are discovered and ON;
- all monitors are set to 1920x1080;

- when I'm in login page I can see all 3 monitors in extended mode (I can move my mouse over all 3 monitors);
- after login, all monitors are in extended mode but the order is wrong (The logical order is Display2 (DP in Video 1) - Display1 (DP in Video2) - Display3 (VGA in Video3));
-- When I want to change the order everything becomes a mess and there is a short step until my desktop environment can&#8217;t be used anymore on the new &#8220;shape&#8221;;
-- I tried to switch the DP cables between them but after this move one of the monitors becomes black and unusable.

I don&#8217;t know what to do in this situation. Any advice?

Thank you.

lsb_release -a
```
username@username~$ lsb_release -aNo LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

```

From xrandr:
```

DP-3 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 509mm x 286mm <- THIS IS A DP PORT FROM MY DOCKING
   1920x1080 60.00*+ 59.94 50.00 60.05 60.00 50.04 
   ... 
DP-5 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 509mm x 286mm <- THIS IS A DP PORT FROM MY DOCKING
   1920x1080 60.00*+ 59.94 50.00 60.05 60.00 50.04 
   ... 
eDP-1-1 connected (normal left inverted right x axis y axis) <- THIS IS THE LID
   1920x1080 60.04 + 40.03 59.93 
   ...
VGA-1-1 connected (normal left inverted right x axis y axis) <- THIS IS THE MONITOR WHICH IS NOT WORKING
   1920x1080 60.00 +
   ...

```


inxi -Fx
```

username@username:~$ 
System:    Host: username Kernel: 4.10.0-28-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Unity 7.4.0 (Gtk 3.18.9-1ubuntu3.3) Distro: Ubuntu 16.04 xenial
Machine:   System: Dell (portable) product: Precision M4800 v: 01
           Mobo: Dell model: 0WJNC2 v: A00 Bios: Dell v: A10 date: 08/28/2014
CPU:       Quad core Intel Core i7-4810MQ (-HT-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 22348
           clock speeds: max: 3800 MHz 1: 1126 MHz 2: 1160 MHz 3: 1249 MHz 4: 1160 MHz 5: 1237 MHz 6: 1106 MHz
           7: 1125 MHz 8: 1147 MHz
Graphics:  Card-1: Intel 4th Gen Core Processor Integrated Graphics Controller bus-ID: 00:02.0
           Card-2: NVIDIA GK107GLM [Quadro K1100M] bus-ID: 01:00.0
           Display Server: X.Org 1.19.3 driver: nvidia Resolution: 1920x1080@60.00hz, 1920x1080@60.00hz
           GLX Renderer: Quadro K1100M/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 375.66 Direct Rendering: Yes
Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0
           Card-3 GN Netcom driver: USB Audio usb-ID: 003-005
           Sound: Advanced Linux Sound Architecture v: k4.10.0-28-generic
Network:   Card-1: Intel Ethernet Connection I217-LM driver: e1000e v: 3.2.6-k port: f080 bus-ID: 00:19.0
           IF: eno1 state: up speed: 1000 Mbps duplex: full mac: 34:e6:d7:15:7c:bc
           Card-2: Intel Wireless 7260 driver: iwlwifi bus-ID: 03:00.0
           IF: wlp3s0 state: down mac: 48:51:b7:1d:98:c7
Drives:    HDD Total Size: 512.1GB (21.5% used) ID-1: /dev/sda model: SK_hynix_SH920_2 size: 256.1GB temp: 40C
           ID-2: /dev/sdb model: SAMSUNG_SSD_SM84 size: 256.1GB temp: 0C
Partition: ID-1: / size: 61G used: 6.8G (12%) fs: ext4 dev: /dev/sda4
           ID-2: /home size: 166G used: 3.1G (2%) fs: ext4 dev: /dev/sda5
           ID-3: /boot size: 465M used: 183M (42%) fs: ext3 dev: /dev/sda2
           ID-4: swap-1 size: 8.19GB used: 0.00GB (0%) fs: swap dev: /dev/sda3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 52.0C mobo: N/A gpu: 0.0:56C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 333 Uptime: 3:19 Memory: 4998.1/15950.3MB Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35 

```

---

### Post by chrysstyann on 2017-08-01
See pictures attached (before and after login).

---

