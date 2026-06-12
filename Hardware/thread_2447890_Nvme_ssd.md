---
title: "Nvme ssd"
date: 2020-07-28
forum: Hardware
---

### Post by MaximB on 2020-07-28
Does Linux\Ubuntu supports NVME SSD well? Like if I install the OS on that disk.
Is getting NVME SSD vs regular SSD worth the price? what's the pros cons? (thinking about buying Samsung 2TB NVME SSD for the new PC).

---

### Post by P-I H on 2020-07-28
I have 3 nvme ssd:s on this computer. None that big. I have 1 with Fedora 32, 1 with Ubuntu 20.04 and 1 with W10.
Nvme1 is installed on a Delock PCIExpress x4 card. The other 2 are installed on the motherboard's nvme interfaces.
Performance is cheched with the Disk utility.
Average read rate on Nvme0 is 1,6 GB/s (100 samples)
Average read rate on Nvme1 is 1,7 GB/s (100 samples)
Average read rate on Nvme2 is 3,0 GB/s (100 samples)

I have had no problems so far.
```
p-i@asus-b450-f:~$ inxi -Fz
System:    Kernel: 5.7.7-050707-generic x86_64 bits: 64 Desktop: Gnome 3.36.4 Distro: Ubuntu 20.04.1 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx serial: <filter> 
           UEFI: American Megatrends v: 2704 date: 08/23/2019 
CPU:       Topology: 8-Core model: AMD Ryzen 7 1700 bits: 64 type: MT MCP L2 cache: 4096 KiB 
           Speed: 1373 MHz min/max: 1550/3750 MHz Core speeds (MHz): 1: 1379 2: 1374 3: 1375 4: 1375 5: 1374 6: 1375 
           7: 1374 8: 1372 9: 1373 10: 1373 11: 1373 12: 1375 13: 1375 14: 1375 15: 1375 16: 1375 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 [Radeon RX 5600 OEM/5600 XT / 5700/5700 XT] 
           driver: amdgpu v: kernel 
           Display: x11 server: X.Org 1.20.8 driver: amdgpu resolution: 2560x1440~60Hz 
           OpenGL: renderer: AMD Radeon RX 5700 (NAVI10 DRM 3.37.0 5.7.7-050707-generic LLVM 10.0.0) 
           v: 4.6 Mesa 20.0.8 
Audio:     Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 HDMI Audio driver: snd_hda_intel 
           Device-2: Advanced Micro Devices [AMD] Family 17h HD Audio driver: snd_hda_intel 
           Device-3: Logitech Webcam C250 type: USB driver: snd-usb-audio,uvcvideo 
           Sound Server: ALSA v: k5.7.7-050707-generic 
Network:   Device-1: Intel I211 Gigabit Network driver: igb 
           IF: enp4s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 698.65 GiB used: 67.46 GiB (9.7%) 
           ID-1: /dev/nvme0n1 vendor: Kingston model: SA1000M8480G size: 447.13 GiB 
           ID-2: /dev/nvme1n1 vendor: Kingston model: SA2000M8500G size: 465.76 GiB 
           ID-3: /dev/nvme2n1 vendor: Samsung model: SSD 960 EVO 250GB size: 232.89 GiB 
           ID-4: /dev/sda vendor: Samsung model: SSD 850 EVO 250GB size: 232.89 GiB 
Partition: ID-1: / size: 456.96 GiB used: 67.41 GiB (14.8%) fs: ext4 dev: /dev/nvme1n1p2 
Sensors:   System Temperatures: cpu: 34.1 C mobo: 36.0 C gpu: amdgpu temp: 44 C 
           Fan Speeds (RPM): cpu: 554 case-1: 889 case-2: 834 case-3: 495 gpu: amdgpu fan: 0 
Info:      Processes: 376 Uptime: 5h 12m Memory: 15.56 GiB used: 1.95 GiB (12.5%) Shell: bash inxi: 3.0.38 
p-i@asus-b450-f:~$ 

```

---

### Post by rbmorse on 2020-07-28
My machine has two, a 512Gb Samsung 970 pro that holds operating systems and the system ESP and a 2Tb IBM P660 that holds user data (separate partitions for Windows and Linux docs and pics et.al.,) that I bought on impulse when NewEgg offered them on sale $150.   Both work fine.

---

### Post by Dennis N on 2020-07-28
It depends on your computer's UEFI firmware. You may need to upgrade the firmware to use the NVMe and to boot from it. Check with manufacturer for details. 

To support NVMe booting on my Asus h97 motherboard (2014), a firmware update was required. After that, it works.

---

### Post by kurt18947 on 2020-08-13
I too have an NVMe on my desktop, HP 920 512GB. It seems to work as advertised. I'm not sure though how much of a benefit NVMe is on an ordinary desktop machine. My impression is that NVMe really shines in continuous high throughput situations such as servers or cloud infrastructure. Another benefit of NVMe is size, they're small for compact devices. My impression could be wrong, I'm not a pro.

---

