---
title: "USB headset distorted sound"
date: 2016-04-15
forum: Hardware
---

### Post by Richard_Romick on 2016-04-15
Greetings Ubuntu Forum people,

I have been having a long time issue with my Sound Blaster Rage USB headset.  In certain applications, the sounds becomes distorted as if it was extremely sped up.  The two instances I have had problems with are steam games: Undertale and Invisible Inc.  Other games, such as Civ V, have perfectly good sound.  Do you know where I can start looking to solve the issue?  Thank you,

inxi -Fxz lists the device as: Card-3 Creative driver: USB Audio usb-ID: 001-006

System:    Host: senlis-Galago-UltraPro Kernel: 4.2.0-35-generic x86_64 (64 bit gcc: 5.2.1)
           Desktop: MATE 1.12.1 (Gtk 3.16.7-0ubuntu3) Distro: Ubuntu 15.10 wily
Machine:   Mobo: System76 model: Galago UltraPro v: galu1 Bios: American Megatrends v: 4.6.5 date: 07/09/2013
CPU:       Quad core Intel Core i7-4750HQ (-HT-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 15963
           clock speeds: max: 3200 MHz 1: 2000 MHz 2: 2000 MHz 3: 2499 MHz 4: 2023 MHz 5: 2013 MHz 6: 2938 MHz
           7: 2000 MHz 8: 2000 MHz
Graphics:  Card: Intel Crystal Well Integrated Graphics Controller bus-ID: 00:02.0
           Display Server: X.Org 1.17.2 driver: intel Resolution: 1600x900@60.00hz
           GLX Renderer: Mesa DRI Intel Haswell Mobile GLX Version: 3.0 Mesa 11.0.2 Direct Rendering: Yes
Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Crystal Well HD Audio Controller driver: snd_hda_intel bus-ID: 00:03.0
           Card-3 Creative driver: USB Audio usb-ID: 001-006
           Sound: Advanced Linux Sound Architecture v: k4.2.0-35-generic
Network:   Card-1: Intel Ethernet Connection I217-V driver: e1000e v: 3.2.5-k port: f080 bus-ID: 00:19.0
           IF: enp0s25 state: down mac: <filter>
           Card-2: Intel Wireless 7260 driver: iwlwifi bus-ID: 03:00.0
           IF: wlp3s0 state: up mac: <filter>
Drives:    HDD Total Size: 360.1GB (33.0% used) ID-1: /dev/sda model: Corsair_Force_GS size: 360.1GB
Partition: ID-1: / size: 322G used: 103G (34%) fs: ext4 dev: /dev/dm-1
           ID-2: /boot size: 236M used: 147M (66%) fs: ext2 dev: /dev/sda1
           ID-3: swap-1 size: 8.51GB used: 0.00GB (0%) fs: swap dev: /dev/dm-2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   None detected - is lm-sensors installed and configured?
Info:      Processes: 251 Uptime: 32 min Memory: 1703.4/7907.1MB Init: systemd runlevel: 5 Gcc sys: 5.2.1
           Client: Shell (bash 4.3.421) inxi: 2.2.16

---

### Post by mörgæs on 2016-04-16
> **Richard_Romick said:**
> Kernel: 4.2.0-35-generic x86_64

This indicates that you are running 15.10. Does a live boot of 16.04 work better?

---

### Post by Richard_Romick on 2016-04-16
I can try that, if I can download it on this poor internet. I'm deployed. I'll give it a shot and get back with you.

---

### Post by Richard_Romick on 2016-04-22
Apparently the upgrade to 16.04 fixed my problem.  Thanks for the tips though.

---

