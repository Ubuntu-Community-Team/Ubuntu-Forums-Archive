---
title: "Will Ubuntu 18.04 Mate run okey on this machine?"
date: 2018-04-08
forum: Hardware
---

### Post by eldklot on 2018-04-08
Hi everyone!

I have a rather low spec'd machine which is currently running Linux Mint 18.3 Xfce. I have been thinking to install Ubuntu Mate on it. I wanted to ask your opinion if Mate will run smoothly on the following specifications:

```
Machine: Device: laptop System: ASUSTeK product: E402MA v: 1.0 serial: N/A
Mobo: ASUSTeK model: E402MA v: 1.0 serial: N/A
UEFI: American Megatrends v: E402MA.207 date: 01/28/2016
Battery BAT0: charge: 24.4 Wh 97.5% condition: 25.0/32.2 Wh (78%)
model: ASUSTeK E402-40 status: N/A
CPU: Dual core Intel Celeron N2840 (-MCP-) 
arch: Silvermont rev.8 cache: 1024 KB
flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 8663
clock speeds: max: 2582 MHz 1: 565 MHz 2: 1615 MHz
Graphics: Card: Intel Atom Processor Z36xxx/Z37xxx Series Graphics & Display
bus-ID: 00:02.0
Display Server: x11 (X.Org 1.18.4 )
drivers: intel (unloaded: modesetting,fbdev,vesa)
Resolution: 1366x768@60.06hz, 1920x1080@60.00hz
OpenGL: renderer: Mesa DRI Intel Bay Trail
version: 4.2 Mesa 17.2.8 Direct Render: Yes
Audio: Card Intel Atom Processor Z36xxx/Z37xxx Series High Def. Audio Controller
driver: snd_hda_intel bus-ID: 00:1b.0
Sound: ALSA v: k4.15.12-041512-generic
Network: Card-1: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter
driver: ath9k bus-ID: 02:00.0
IF: wlp2s0 state: up mac: <filter>
Card-2: Realtek RTL8101/2/6E PCIE Fast/Gigabit Ethernet controller
driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 03:00.2
Memory: 1200.5/1875.9MB
```

I Thank you in advance for your suggestions.

---

### Post by Yellow Pasque on 2018-04-08
I don't think MATE is a lot more demanding than xfce. The CPU is not bad at all, and neither is the GPU if you're not gaming. 2GB of memory's probably the worst part of your machine. You may want to see if you can find memory usage figures for xfce and MATE.

---

### Post by kerry_s on 2018-04-09
take a look at elementary os, it should run fine on those specs.

---

### Post by eldklot on 2018-04-09
> **Temüjin said:**
> I don't think MATE is a lot more demanding than xfce. The CPU is not bad at all, and neither is the GPU if you're not gaming. 2GB of memory's probably the worst part of your machine. You may want to see if you can find memory usage figures for xfce and MATE.

Yes, that 2GB of memory is the problem of this machine. It has actually a free slot for adding extra memory. Maybe it's time for me to open the back of the computer and see how it looks and if I can do it by myself. I am not a very tech savvy and handy person so that would be a nice challenge. If I can make it, That would make me very happy. 
Thanks for your confirmation on the MATE. It would certainly be fun to try it with next release of Ubuntu.
Cheers

---

### Post by eldklot on 2018-04-09
> **kerry_s said:**
> take a look at elementary os, it should run fine on those specs.

Thanks kerry_s for your suggestion. I will certainly have a look at Elemantary.
Cheers

---

### Post by Yellow Pasque on 2018-04-09
> It has actually a free slot for adding extra memory

Are you sure that's not the SD card reader? Quick google shows RAM can't be added/upgraded on this model (2GB soldered on the mobo).

---

### Post by eldklot on 2018-04-09
> **Temüjin said:**
> Are you sure that's not the SD card reader? Quick google shows RAM can't be added/upgraded on this model (2GB soldered on the mobo).

You might very well be right. I just had run the following command and iterpreted the output as the system having two slots:
```
sudo lshw -class memory 

``````
 
*-firmware              
       description: BIOS
       vendor: American Megatrends Inc.
       physical id: 0
       version: E402MA.207
       date: 01/28/2016
       size: 64KiB
       capacity: 960KiB
       capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification uefi
  *-memory
       description: System Memory
       physical id: a
       slot: System board or motherboard
       size: 2GiB
     *-bank:0
          description: DIMM DDR3 1333 MHz (0,8 ns)
          product: Array1_PartNumber0
          vendor: A1_Manufacturer0
          physical id: 0
          serial: A1_SerNum0
          slot: A1_DIMM0
          size: 2GiB
          width: 64 bits
          clock: 1333MHz (0.8ns)
     *-bank:1
          description: DIMM [empty]
          product: Array1_PartNumber1
          vendor: A1_Manufacturer1
          physical id: 1
          serial: A1_SerNum1
          slot: A1_DIMM1
  *-cache:0
       description: L1 cache
       physical id: 11
       slot: CPU Internal L1
       size: 112KiB
       capacity: 112KiB
       capabilities: internal write-back
       configuration: level=1
  *-cache:1
       description: L2 cache
       physical id: 12
       slot: CPU Internal L2
       size: 1MiB
       capacity: 1MiB
       capabilities: internal write-back unified
       configuration: level=2



```

---

### Post by eldklot on 2018-04-12
@Temüjin

You are right about the impossibility of memory upgrade for this model. I guess I have to live with it for the time being.
Thanks for your reply!

---

