---
title: "New PC  Ryzen or Intel"
date: 2020-12-06
forum: Hardware
---

### Post by Quarkrad on 2020-12-06
I'm looking at replacing my pc and so far, since ubuntu 8.04, I've always had intel processors and gigabyte motherboards.  Do I go Ryzen or Intel?  In my limited experience intel seems to work out of the box and I've read some posts that go on and on about getting amd cpu's to work.  What should I do in the 20.04 world?   Also - looking at m2 nvme 3rd gen motherboard, are there any makes one should avoid(?) - as said, I've always found gigabyte a solid performer re linux/ubuntu.

---

### Post by TheFu on 2020-12-06
What's your workload? What level processor are you looking at?  Intel has dropped some of their prices and a Core i3 is faster than a Core i5 from just 2-3 yrs ago.

Do you care about Intel's CPU security issues?  AMD has some, but not all of those.  If you need more cores for workloads that can use those efficiently, there's no question - AMD.
If you are looking at laptops, I think Intel is better with battery management.

AMD Ryzen has 4th generation PCIe available now.

---

### Post by Quarkrad on 2020-12-06
I have suddenly got hours and hours of video editing to be done so my 'would like' in terms of a system upgrade is becoming 'must have'.  Sort of joking aside my set up is ok for surfing and documents but is creaking at editing again and as said, I have many many hours to do.  The past two days has revealed  potential issue(s) with some modern boards and kernel 5.4 that ships with 20.04.  I'm just reading a post that seems to say you can port 5.9 on 20.04 - 5.8/9 appears to address many, if not all of the issues I've read about so far.   This afternoon has led me away from gigabyte - currently looking at msi. My main requirement is m2 nvme 3rd gen - I fear buying one of these modern boards and getting problems (e.g. sound) with Ubuntu.

---

### Post by TheFu on 2020-12-06
> **Quarkrad said:**
> I have suddenly got hours and hours of video editing to be done so my 'would like' in terms of a system upgrade is becoming 'must have'.  Sort of joking aside my set up is ok for surfing and documents but is creaking at editing again and as said, I have many many hours to do.  The past two days has revealed  potential issue(s) with some modern boards and kernel 5.4 that ships with 20.04.  I'm just reading a post that seems to say you can port 5.9 on 20.04 - 5.8/9 appears to address many, if not all of the issues I've read about so far.   This afternoon has led me away from gigabyte - currently looking at msi. My main requirement is m2 nvme 3rd gen - I fear buying one of these modern boards and getting problems (e.g. sound) with Ubuntu.

I do video editing on a 10 yr old laptop. I do video transcoding in a 2 yr old Ryzen 2600.  My editing avoids transcoding or rendering, but I'm not adding transitions or fancy graphics, just removing cuts (i.e. commercials).  Almost always, the cutting is done with mpeg2 video and disk performance matters 1000x more than CPU/RAM.  Once cut, then the transcoding happens and the Ryzen running 12 threads makes a huge difference.  I replaced a Core i7-950 (1st generation) with the Ryzen. Transcode times dropped by 75%.

For video editing, in theory, some GPUs can be used on Linux to speed it up. Looks like NVENC/NVDEC/CUVID is the way for encoding now. [https://trac.ffmpeg.org/wiki/HWAccelIntro](https://trac.ffmpeg.org/wiki/HWAccelIntro) But it just depends on your GPU.

---

### Post by P-I H on 2020-12-06
I built this desktop some week back.
```
p-i@pi-TUF-B550M:~$ inxi -Fz
System:    Kernel: 5.10.0-051000rc3-generic x86_64 bits: 64 Desktop: N/A Distro: Ubuntu 20.10 (Groovy Gorilla) 
Machine:   Type: Desktop System: ASUS product: N/A v: N/A serial: <filter> 
           Mobo: ASUSTeK model: TUF GAMING B550M-PLUS (WI-FI) v: Rev X.0x serial: <filter> UEFI: American Megatrends 
           v: 1212 date: 11/04/2020 
CPU:       Info: 6-Core model: AMD Ryzen 5 5600X bits: 64 type: MT MCP L2 cache: 3072 KiB 
           Speed: 3141 MHz min/max: 2200/3700 MHz Core speeds (MHz): 1: 3141 2: 2056 3: 2057 4: 2057 5: 2928 6: 2056 
           7: 2057 8: 2057 9: 3580 10: 2056 11: 2983 12: 2057 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 [Radeon RX 5600 OEM/5600 XT / 5700/5700 XT] 
           driver: amdgpu v: kernel 
           Display: x11 server: X.Org 1.20.9 driver: amdgpu,ati unloaded: fbdev,modesetting,radeon,vesa 
           resolution: 2560x1440 
           OpenGL: renderer: AMD Radeon RX 5700 (NAVI10 DRM 3.40.0 5.10.0-051000rc3-generic LLVM 11.0.0) 
           v: 4.6 Mesa 20.2.1 
Audio:     Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 HDMI Audio driver: snd_hda_intel 
           Device-2: Advanced Micro Devices [AMD] Starship/Matisse HD Audio driver: snd_hda_intel 
           Sound Server: ALSA v: k5.10.0-051000rc3-generic 
Network:   Device-1: Intel Wi-Fi 6 AX200 driver: iwlwifi 
           IF: wlp6s0 state: up mac: <filter> 
           Device-2: Realtek RTL8125 2.5GbE driver: r8169 
           IF: enp7s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 1.36 TiB used: 86.52 GiB (6.2%) 
           ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 970 EVO 500GB size: 465.76 GiB 
           ID-2: /dev/nvme1n1 vendor: Kingston model: SA2000M8500G size: 465.76 GiB 
           ID-3: /dev/sda vendor: Samsung model: SSD 860 EVO 500GB size: 465.76 GiB 
Partition: ID-1: / size: 456.96 GiB used: 86.49 GiB (18.9%) fs: ext4 dev: /dev/nvme0n1p2 
Swap:      ID-1: swap-1 type: file size: 2.00 GiB used: 0 KiB (0.0%) file: /swapfile 
Sensors:   System Temperatures: cpu: 34.2 C mobo: 37.0 C gpu: amdgpu temp: 46.0 C 
           Fan Speeds (RPM): fan-1: 817 fan-2: 836 fan-3: 821 fan-7: 0 gpu: amdgpu fan: 0 
Info:      Processes: 341 Uptime: 1h 49m Memory: 15.54 GiB used: 2.11 GiB (13.6%) Shell: Bash inxi: 3.1.07 
p-i@pi-TUF-B550M:~$
```
It runs about 10% faster compared to my earlier Ryzen 7 1700@3.75 GHz when testing witith Handbrake and code this video SES.Astra.UHD.Test.1.2160p.UHDTV.AAC.HEVC.x265-LiebeIst.mkv to SES.Astra.UHD.Test.1.2160p.UHDTV.AAC.HEVC.x265-LiebeIst.m4v.. Average FPS is 47.10.
I use Avidemux to edit recorded TV recordings, but this don't put much requiirement on the system. 
The motherboard is an Asus TUF B550M (WIFI). Many of the new B550 motherbords use 2.5 Gb Network interface which is a problem at least with the Realtek chip. I use the 5.10 linux kernel as the Realtek chip is supported and also because it contains improved for Zen 3.

---

### Post by mastablasta on 2020-12-07
for video editing use Ryzen. costs less, gives more output (or same).

i can confirm Asus works well. i have a "non gaming" motherboard and worked out of the box. you may want to add at least entry level gaming GPU card, but again depends what kind of stuff you are doing. for video editing pack it with fast RAM.

intel is also OK.

---

