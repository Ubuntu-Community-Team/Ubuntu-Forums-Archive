---
title: "Hot southbridge chip and graphics card"
date: 2014-03-04
forum: Hardware
---

### Post by dave102 on 2014-03-04
Hello, new to the forums, not to Ubuntu. 

I recently installed Ubuntu Server 12.04 LTS on some hardware I had and noticed that the southbridge chip's heatsink and graphics card heatsink were quite hot to the touch, which surprised me since I don't even have a GUI installed. I tried all sorts of power saving features/tweaks thinking something might not be going into the correct powersaving mode. I tried powertop, pm-utils, installing XFCE4 (to see if it had some graphics drivers), and followed this [https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks](https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks). Nothing has changed the temperature or power usage. 

Here's my hardware:
[Intel DP43TF]("http://ark.intel.com/products/36461/Intel-Desktop-Board-DP43TF")  motherboard
Xeon L5420 2.5GHz quad
8GB Samsung DDR2-800
GeForce 7600 GS (also tried a Radeon HD 5450 card, same results)
Hitachi 120GB 2.5in SATA HD (temporary) 

I found this output from powertop interesting considering the machine is 99.9% idle:
```
             Usage     Device name
            6553846%      CPU use
            100.0%        PCI Device: LSI Corporation FW322/323 [TrueFire] 1394a Controller
            100.0%        PCI Device: JMicron Technology Corp. JMB368 IDE controller
            100.0%        PCI Device: NVIDIA Corporation G73 [GeForce 7600 GS]
            100.0%        PCI Device: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
            100.0%        PCI Device: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
            100.0%        PCI Device: Intel Corporation 82801 PCI Bridge
            100.0%        PCI Device: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4
            100.0%        PCI Device: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
            100.0%        PCI Device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
            100.0%        PCI Device: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
            100.0%        PCI Device: Intel Corporation 82567V-2 Gigabit Network Connection
            100.0%        PCI Device: Intel Corporation 4 Series Chipset HECI Controller
            100.0%        PCI Device: Intel Corporation 4 Series Chipset PCI Express Root Port
             20.1 pkts/s  Network interface: eth0 (e1000e)
              0.0%        USB device: UHCI Host Controller
              0.0%        USB Device: usb-device-0b38-0010
              0.0%        USB device: EHCI Host Controller
              0.0%        USB device: Microsoft 3-Button Mouse with IntelliEye(TM) (Microsoft)
              0.0%        PCI Device: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
              0.0%        USB device: EHCI Host Controller
              0.0%        PCI Device: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
              0.0%        PCI Device: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
              0.0%        USB device: UHCI Host Controller
              0.0%        PCI Device: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
              0.0%        PCI Device: Intel Corporation 4 Series Chipset DRAM Controller
              0.0%        USB device: UHCI Host Controller
              0.0%        PCI Device: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
              0.0%        PCI Device: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
              0.0%        USB device: UHCI Host Controller
              0.0%        Audio codec hwC0D2: Realtek
              0.0%        PCI Device: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
              0.0%        USB device: UHCI Host Controller
              0.0%        PCI Device: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
              0.0%        USB device: UHCI Host Controller
```

Anyone have any ideas I can try?

---

### Post by Yellow Pasque on 2014-03-04
What driver are you using for the nvidia card (opensource nouveau or propietary nvidia)? Does the card have a fan?
If you're not sure what driver you're using, look at lspci:
```
sudo update-pciids
lspci -k
```

As for the southbridge, I wouldn't worry too much. Those things are made to run hot.

---

### Post by tgalati4 on 2014-03-04
I have an older version of that board (DP35) and the southbridge does run hot, without a heat sink.  So you can either put one on, use some heat paste and just stick it on or try this:  Remove all but 2GB of RAM.  It's possible that running at maximum RAM (8 GB) is causing your southbridge to work extra hard.  Can you keep your finger on it for 30 seconds?  If not, then it is probably higher than 135F and it will degrade over time.  Also, the southbridge also runs networking and multichannel sound.  So streaming music will cause that chip to get toasty--not a great design for home use or for server workloads.

Update the BIOS if available and look for some instrumentation to see what the temperatures are:

```
sensors
```

tgalati4@Mint14-Extensa ~ $ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +57.0°C  (crit = +95.0°C)
temp2:        +57.0°C  (crit = +105.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +51.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:       +55.0°C  (high = +100.0°C, crit = +100.0°C)

Graphics chips always run hot.  See if there is a "dynamic clock" setting to throttle the GPU clock when not in use.  The specifications show no on-board video, so if this is running headless or text console try finding an older/smaller video card.  Or go commando, and just remove it.

---

### Post by dave102 on 2014-03-04
After some more investigating, I guess this is just how this board runs. I suppose I'll have to update my case fans. Both graphics cards I tried have passive heatsinks and the southbridge chip has a little passive heatsink as well. 

I decided to try installing some different OSs to see if they had any magic drivers or settings and apparently they don't. I also made sure the BIOS is at the latest version available. I plugged in my kill-a-watt and here are the results: 

Ubuntu Server 12.04 - about 70-75w while idle

Ubuntu Server 13.10 - about 65-70w while idle

Windows 7 Pro - about 75-80w while idle

---

### Post by Yellow Pasque on 2014-03-04
> **tgalati4 said:**
> Remove all but 2GB of RAM.  It's possible that running at maximum RAM (8 GB) is causing your southbridge to work extra hard

LOL NO, the southbridge is not connected to RAM...

---

