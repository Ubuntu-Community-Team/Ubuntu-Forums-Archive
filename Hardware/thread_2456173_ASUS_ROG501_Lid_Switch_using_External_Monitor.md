---
title: "ASUS ROG501 Lid Switch using External Monitor"
date: 2021-01-05
forum: Hardware
---

### Post by kendall-s1999 on 2021-01-05
Hi,
 I'm having issues setting the lid switch to "ignore" on this laptop.
 This laptop is always on the power brick.
 I don't see any settings in Power, or Display to do this.
 Any reason this option is not available?
 I have a monitor connected to the HDMI connector and the display set to Mirror.
 When i close the lid the laptop goes into suspend.
 Laptop info:
 
 ```
 
 System:    Host: ROG-5 Kernel: 5.8.0-34-generic x86_64 bits: 64 Desktop: GNOME 3.38.1 Distro: Ubuntu 20.10 (Groovy Gorilla)
  Machine:   Type: Laptop System: ASUSTeK product: ROG GU501GM v: 1.0 serial: (private) 
            Mobo: ASUSTeK model: GU501GM v: 1.0 serial: (private) UEFI: American Megatrends v: GU501GM.315 
            date: 04/28/2020 
  Battery:   ID-1: BAT0 charge: 49.2 Wh condition: 49.2/55.0 Wh (89%) 
 
 CPU:       Info: 6-Core model: Intel Core i7-8750H bits: 64 type: MT MCP L2 cache: 9216 KiB 
            Speed: 800 MHz min/max: 800/4100 MHz Core speeds (MHz): 1: 800 2: 800 3: 801 4: 800 5: 800 6: 800 7: 800 8: 800 
            9: 800 10: 800 11: 800 12: 800 
 
 Graphics:  Device-1: Intel UHD Graphics 630 driver: i915 v: kernel 
            Device-2: NVIDIA GP106M [GeForce GTX 1060 Mobile] driver: nouveau v: kernel 
            Device-3: IMC Networks USB2.0 HD UVC WebCam type: USB driver: uvcvideo 
            Display: server: X.Org 1.20.9 driver: modesetting unloaded: fbdev,vesa resolution: 1: 1920x1080~120Hz
            2: 1920x1080~60Hz 
            OpenGL: renderer: Mesa Intel UHD Graphics 630 (CFL GT2) v: 4.6 Mesa 20.2.1 
 
 Audio:     Device-1: Intel Cannon Lake PCH cAVS driver: snd_hda_intel 
            Device-2: NVIDIA GP106 High Definition Audio driver: snd_hda_intel 
            Sound Server: ALSA v: k5.8.0-34-generic 
 
 Network:   Device-1: Intel Wireless-AC 9560 [Jefferson Peak] driver: iwlwifi 
            IF: wlo1 state: down mac: c0:b6:f9:5b:5a:f4 
            Device-2: Realtek RTL8153 Gigabit Ethernet Adapter type: USB driver: r8152 
            IF: enxbc14efee4d4c state: up speed: 100 Mbps duplex: full mac: bc:14:ef:ee:4d:4c 
 
 Drives:    Local Storage: total: 465.76 GiB used: 9.32 GiB (2.0%) 
            ID-1: /dev/sda vendor: Western Digital model: WDS500G2B0B-00YS70 size: 465.76 GiB 
 
 Partition: ID-1: / size: 456.96 GiB used: 9.31 GiB (2.0%) fs: ext4 dev: /dev/sda2 
 
 Swap:      ID-1: swap-1 type: file size: 2.00 GiB used: 0 KiB (0.0%) file: /swapfile 
 
 Sensors:   System Temperatures: cpu: 60.0 C mobo: N/A gpu: nouveau temp: 54.0 C 
            Fan Speeds (RPM): cpu: 3300 
 
 Info:      Processes: 283 Uptime: 33m Memory: 15.48 GiB used: 1.25 GiB (8.1%) Shell: Bash inxi: 3.1.07
 
```

---

### Post by kendall-s1999 on 2021-01-05
I have semi resolved this by switching to "Single" Display in display settings.
When i did this at first, the laptop was so un-responsive it was unusable (like the CPU was running at 1Mhz).
I updated to the propriatary nVIDIA drivers and that took care of that.
Not exactly what I wanted, but it will work.

```

Graphics:  Device-1: Intel UHD Graphics 630 driver: i915 v: kernel 
           Device-2: NVIDIA GP106M [GeForce GTX 1060 Mobile] driver: nvidia v: 455.45.01 <------ New Driver
           Device-3: IMC Networks USB2.0 HD UVC WebCam type: USB driver: uvcvideo 
           Display: server: X.Org 1.20.9 driver: modesetting,nvidia unloaded: fbdev,nouveau,vesa 
           resolution: 1920x1080~60Hz 
           OpenGL: renderer: GeForce GTX 1060/PCIe/SSE2 v: 4.6.0 NVIDIA 455.45.01 

```

---

### Post by kendall-s1999 on 2021-01-06
Solved. Installed Unity Desktop. Options are back for Lid shut settings, and it works as it should.

---

