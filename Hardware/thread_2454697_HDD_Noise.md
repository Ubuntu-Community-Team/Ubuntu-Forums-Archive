---
title: "HDD Noise"
date: 2020-12-04
forum: Hardware
---

### Post by marco-kk on 2020-12-04
Hello everyone, 

I have installed Ubuntu 20.10 on my new laptop. Occasionally (really not very often) my HDD makes some noise when it is busy. This does not occur on Windows. 

Since the laptop is new, I would like to avoid this behavior, because I believe it might lead to damage the disk if it continues. Do you agree? 

I have tried to run hdparm to change the acoustics of the disk. 

But I get the following error 

```
 HDIO_DRIVE_CMD:ACOUSTIC failed: Inappropriate ioctl for device
 HDIO_DRIVE_CMD(identify) failed: Inappropriate ioctl for device


```

So it seems that one cannot use hdparm to change the settings of this particular disk. 

If there is anything that you need to know about my machine or some command outputs, please let me know! 

I would like to know your opinion about:


[LIST=1]
[*]Can this behavior cause some problems in the long run (since it is new laptop)? 
[*]Do you know how to help me solving this? 
[/LIST]

Many thanks in advance!




```


System:
  Kernel: 5.8.0-31-generic x86_64 bits: 64 compiler: gcc v: 10.2.0 
  Desktop: N/A Distro: Ubuntu 20.10 (Groovy Gorilla) 
Machine:
  Type: Laptop System: ASUSTeK product: VivoBook_ASUSLaptop X512DA_X512DA 
  v: 1.0 serial: <filter> 
  Mobo: ASUSTeK model: X512DA v: 1.0 serial: <filter> 
  UEFI: American Megatrends v: X512DA.313 date: 08/24/2020 
Battery:
  ID-1: BAT0 charge: 36.6 Wh condition: 36.6/37.1 Wh (99%) 
  model: ASUSTeK ASUS Battery status: Not charging 
CPU:
  Info: Quad Core model: AMD Ryzen 5 3500U with Radeon Vega Mobile Gfx 
  bits: 64 type: MT MCP arch: Zen+ rev: 1 L2 cache: 2048 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm 
  bogomips: 33538 
  Speed: 1222 MHz min/max: 1400/2100 MHz boost: enabled Core speeds (MHz): 
  1: 1253 2: 1239 3: 1396 4: 1396 5: 1396 6: 1396 7: 1396 8: 1397 
Graphics:
  Device-1: AMD Picasso vendor: ASUSTeK driver: amdgpu v: kernel 
  bus ID: 03:00.0 
  Device-2: IMC Networks USB2.0 Hub type: USB driver: uvcvideo 
  bus ID: 3-2.2:5 
  Display: x11 server: X.Org 1.20.9 driver: amdgpu,ati 
  unloaded: fbdev,modesetting,vesa resolution: 1920x1080~60Hz 
  OpenGL: renderer: AMD RAVEN (DRM 3.38.0 5.8.0-31-generic LLVM 11.0.0) 
  v: 4.6 Mesa 20.2.1 direct render: Yes 
Audio:
  Device-1: AMD Raven/Raven2/Fenghuang HDMI/DP Audio driver: snd_hda_intel 
  v: kernel bus ID: 03:00.1 
  Device-2: AMD Raven/Raven2/FireFlight/Renoir Audio Processor driver: N/A 
  bus ID: 03:00.5 
  Device-3: AMD Family 17h HD Audio vendor: ASUSTeK driver: snd_hda_intel 
  v: kernel bus ID: 03:00.6 
  Sound Server: ALSA v: k5.8.0-31-generic 
Network:
  Device-1: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter 
  vendor: AzureWave driver: ath10k_pci v: kernel bus ID: 01:00.0 
  IF: wlp1s0 state: up mac: <filter> 
Drives:
  Local Storage: total: 238.47 GiB used: 9.13 GiB (3.8%) 
  ID-1: /dev/nvme0n1 vendor: Kingston model: RBUSNS8154P3256GJ3 
  size: 238.47 GiB 
Partition:
  ID-1: / size: 95.62 GiB used: 9.10 GiB (9.5%) fs: ext4 dev: /dev/nvme0n1p4 
Swap:
  ID-1: swap-1 type: file size: 2.00 GiB used: 0 KiB (0.0%) file: /swapfile 
Sensors:
  System Temperatures: cpu: 53.0 C mobo: N/A gpu: amdgpu temp: 53.0 C 
  Fan Speeds (RPM): cpu: 2400 
Info:
  Processes: 274 Uptime: 49m Memory: 5.81 GiB used: 2.33 GiB (40.2%) 
  Init: systemd runlevel: 5 Compilers: gcc: N/A Packages: 1714 Shell: Bash 
  v: 5.0.17 inxi: 3.1.07 


```

---

### Post by ajgreeny on 2020-12-04
I presume from your terminal output that it is a Kingston SSD?

That will be making no mechanical noise, so what noise is it making?

---

### Post by marco-kk on 2020-12-04
Thanks. 

Well, I assumed that it was the SSD, but it could also be something also. I share a registration of the sound the it makes when Ubuntu starts. 

It might be because I deleted the original EFI partition present in disk and created a new one when installing ubuntu (I first created an EFI partition, then Windows, then Ubuntu). Could that be the reason? I doubt about that, but I am just considering options. 


In any case, here is the audio: 

[https://sndup.net/3tbf](https://sndup.net/3tbf)

Starting from second 5, you can hear some kind of scratching. It looks like the sound of a malfunctioning HDD, but yes my laptop has actually an SSD (Could it be the GPU and some incompatibility with AMD?). Right now, the sound is very low and it does appear very often. But there should be no sound at all...

---

### Post by marco-kk on 2020-12-04
Yes, upon reflection, I realized that it a coil whine problem of the GPU or something else (maybe some power management issue). 

To reiterate, I have tried to watch a 4K 60fps video on Ubuntu, and indeed the sound appears. It does not appear on Windows, even in the same situation. 

It mainly appears when Ubuntu starts and when it shuts down. So, it is not just the GPU, but a power issue in general, I believe. 

What do you think?

---

### Post by ajgreeny on 2020-12-04
Those grinding sounds can also be made by dry cooling fan bearings that are running badly; I have had that a long time ago in a PSU fan which took me a while to diagnose correctly.
It was, thankfully, easy to repair.

---

### Post by marco-kk on 2020-12-04
That is indeed a possibility, because the sound started to appear also on Windows. 

It is really mystery. I have manually upgraded to the most recent version of the kernel (5.10). It looks like the start-up noise improved, but sometimes it reappears (again, it is really not loud). 

Now I do not know what to do. I have bought this laptop during black friday (roughly 480 euros). It was not a bargain, but still a good price for the device. But if these are the premises... I have until the 31st of January to ship it back. I will play with it for a bit and then I will decide. 

I do not think that you can really help me anymore here. But it was really helpful. I think that we managed to find some possible causes of the problem.

---

