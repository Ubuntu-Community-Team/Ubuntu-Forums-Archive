---
title: "older Lenovo sl500 laptop support"
date: 2020-12-09
forum: Hardware
---

### Post by ArthurPeale on 2020-12-09
Last Summer, at a yard sale, I found a guy selling some older hardware. I took a shine to this Lenovo laptop.

I only just found a power adapter to be able to test it, yesterday.

It came with Windows 7, but I resized the partition to its minimum and installed 20.08 on the larger portion.

So far it's running very well, but I've had issues with some of the hardware.

1) the cameras - there are two, right above the monitor. I can not figure out how to get them to turn on. I would have thought a fn hotkey, but there doesn't appear to be one. 

2) Bluetooth support - not sure if there is a Bluetooth adapter in here, but it /seems/ that's the case. More research (opening the case) is necessary. I don't get any errors when I load the btusb module.


I think someone must have shoehorned a newer wireless adapter in it - unless 5G wlan was available in 2009?

```
arthur@ThinkPad:~$ inxi -Fxz
System:
  Kernel: 5.4.0-56-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 
  Desktop: Gnome 3.36.4 Distro: Ubuntu 20.04.1 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: LENOVO product: 2746MLU v: ThinkPad SL 
  serial: <filter> 
  Mobo: LENOVO model: 2746MLU v: LENOVO 6AET57WW serial: <filter> 
  BIOS: LENOVO v: 6AET57WW date: 04/01/2009 
Battery:
  ID-1: BAT0 charge: 41.7 Wh condition: 43.4/51.8 Wh (84%) 
  model: SANYO 42T4670 status: Unknown 
CPU:
  Topology: Dual Core model: Intel Core2 Duo T5870 bits: 64 type: MCP 
  arch: Core Merom rev: D L2 cache: 2048 KiB 
  flags: lm nx pae sse sse2 sse3 ssse3 bogomips: 7980 
  Speed: 2091 MHz min/max: 800/2001 MHz Core speeds (MHz): 1: 2079 2: 1995 
Graphics:
  Device-1: Intel Mobile 4 Series Integrated Graphics vendor: Lenovo 
  driver: i915 v: kernel bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.8 driver: i915 resolution: 1280x800~60Hz 
  OpenGL: renderer: Mesa DRI Mobile Intel GM45 Express (CTG) 
  v: 2.1 Mesa 20.0.8 direct render: Yes 
Audio:
  Device-1: Intel 82801I HD Audio vendor: Lenovo ThinkPad T400 
  driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Sound Server: ALSA v: k5.4.0-56-generic 
Network:
  Device-1: Intel PRO/Wireless 5100 AGN [Shiloh] Network driver: iwlwifi 
  v: kernel port: 4400 bus ID: 02:00.0 
  IF: wlp2s0 state: up mac: <filter> 
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Lenovo driver: r8169 v: kernel port: e800 bus ID: 0c:00.0 
  IF: enp12s0 state: down mac: <filter> 
arthur@ThinkPad:~$ inxi -Fxz
System:
  Kernel: 5.4.0-56-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 
  Desktop: Gnome 3.36.4 Distro: Ubuntu 20.04.1 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: LENOVO product: 2746MLU v: ThinkPad SL 
  serial: <filter> 
  Mobo: LENOVO model: 2746MLU v: LENOVO 6AET57WW serial: <filter> 
  BIOS: LENOVO v: 6AET57WW date: 04/01/2009 
Battery:
  ID-1: BAT0 charge: 41.7 Wh condition: 43.4/51.8 Wh (84%) 
  model: SANYO 42T4670 status: Unknown 
CPU:
  Topology: Dual Core model: Intel Core2 Duo T5870 bits: 64 type: MCP 
  arch: Core Merom rev: D L2 cache: 2048 KiB 
  flags: lm nx pae sse sse2 sse3 ssse3 bogomips: 7980 
  Speed: 2091 MHz min/max: 800/2001 MHz Core speeds (MHz): 1: 2079 2: 1995 
Graphics:
  Device-1: Intel Mobile 4 Series Integrated Graphics vendor: Lenovo 
  driver: i915 v: kernel bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.8 driver: i915 resolution: 1280x800~60Hz 
  OpenGL: renderer: Mesa DRI Mobile Intel GM45 Express (CTG) 
  v: 2.1 Mesa 20.0.8 direct render: Yes 
Audio:
  Device-1: Intel 82801I HD Audio vendor: Lenovo ThinkPad T400 
  driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Sound Server: ALSA v: k5.4.0-56-generic 
Network:
  Device-1: Intel PRO/Wireless 5100 AGN [Shiloh] Network driver: iwlwifi 
  v: kernel port: 4400 bus ID: 02:00.0 
  IF: wlp2s0 state: up mac: <filter> 
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Lenovo driver: r8169 v: kernel port: e800 bus ID: 0c:00.0 
  IF: enp12s0 state: down mac: <filter> 
arthur@ThinkPad:~$ inxi -Fxz
System:
  Kernel: 5.4.0-56-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 
  Desktop: Gnome 3.36.4 Distro: Ubuntu 20.04.1 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: LENOVO product: 2746MLU v: ThinkPad SL 
  serial: <filter> 
  Mobo: LENOVO model: 2746MLU v: LENOVO 6AET57WW serial: <filter> 
  BIOS: LENOVO v: 6AET57WW date: 04/01/2009 
Battery:
  ID-1: BAT0 charge: 41.7 Wh condition: 43.4/51.8 Wh (84%) 
  model: SANYO 42T4670 status: Unknown 
CPU:
  Topology: Dual Core model: Intel Core2 Duo T5870 bits: 64 type: MCP 
  arch: Core Merom rev: D L2 cache: 2048 KiB 
  flags: lm nx pae sse sse2 sse3 ssse3 bogomips: 7980 
  Speed: 2091 MHz min/max: 800/2001 MHz Core speeds (MHz): 1: 2079 2: 1995 
Graphics:
  Device-1: Intel Mobile 4 Series Integrated Graphics vendor: Lenovo 
  driver: i915 v: kernel bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.8 driver: i915 resolution: 1280x800~60Hz 
  OpenGL: renderer: Mesa DRI Mobile Intel GM45 Express (CTG) 
  v: 2.1 Mesa 20.0.8 direct render: Yes 
Audio:
  Device-1: Intel 82801I HD Audio vendor: Lenovo ThinkPad T400 
  driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Sound Server: ALSA v: k5.4.0-56-generic 
Network:
  Device-1: Intel PRO/Wireless 5100 AGN [Shiloh] Network driver: iwlwifi 
  v: kernel port: 4400 bus ID: 02:00.0 
  IF: wlp2s0 state: up mac: <filter> 
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Lenovo driver: r8169 v: kernel port: e800 bus ID: 0c:00.0 
  IF: enp12s0 state: down mac: <filter> 
Drives:
  Local Storage: total: 232.89 GiB used: 9.67 GiB (4.2%) 
  ID-1: /dev/sda vendor: Western Digital model: WD2500BEVS-08VAT2 
  size: 232.89 GiB 
Partition:
  ID-1: / size: 200.14 GiB used: 9.67 GiB (4.8%) fs: ext4 dev: /dev/sda5 
Sensors:
  System Temperatures: cpu: 42.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 

arthur@ThinkPad:~$ dmesg | grep uvc
[   12.213087] usbcore: registered new interface driver uvcvideo

arthur@ThinkPad:~$ sudo lsmod | grep uvcvideo
[sudo] password for arthur: 
uvcvideo               98304  0
videobuf2_vmalloc      20480  1 uvcvideo
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_common       49152  2 videobuf2_v4l2,uvcvideo
videodev              225280  3 videobuf2_v4l2,uvcvideo,videobuf2_common
mc                     53248  4 videodev,videobuf2_v4l2,uvcvideo,videobuf2_common
```

---

### Post by wildmanne39 on 2020-12-09
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by ArthurPeale on 2020-12-09
> **wildmanne39 said:**
> Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

thank you for that. I looked, but couldn't identify it on my screen.

---

### Post by ArthurPeale on 2020-12-24
Tried putting Windows 7 on a separate partition, to see if I could get the cameras to come on.

The drivers that I pulled off the Lenovo website didn't want to install. So, now I don't know where to go. 

I started to take it apart, to check the cameras themselves, but it seemed that I was going to break something, so I stopped.

---

### Post by kurt18947 on 2020-12-25
Happy Holidays Arthur
I don't see any indication the in inxi output of a bluetooth device. Sometimes bluetooth and WiFi are supplied by the same device, I don't know that this is the case on your machine. Something to be aware of on Thinkpads - they whitelist wifi adapters and perhaps other devices. This means that only devices listed in the manual are supported by the BIOS so I doubt you could buy a newer wifi/bluetooth device, plug it in and expect it to work. If you do a bit of searching you can probably find the maintenance manual for your machine. That will list which accessories are supported plus other useful items.

I'm surprised the cameras don't just work. I have a couple Thinkpads, purchased for a very good price off Ebay and the cameras just work. I don't use them but I used Cheese to verify their operation.

---

### Post by Yellow Pasque on 2020-12-25
> Intel PRO/Wireless 5100 AGN

From quick googling, it looks like this wifi chip does not have bluetooth built in. Maybe you have a separate adapter.
Check:
```
lsusb
```

---

### Post by ArthurPeale on 2020-12-25
I'm fairly sure there isn't a Bluetooth adapter in here. I was at first. Not really worried about it.

The camera issue, OTOH, is a thing that I'd like to solve, if possible. My mom's alone a lot of the time, and being able to video chat with her would be good for her morale.

---

### Post by ArthurPeale on 2020-12-25
> **kurt18947 said:**
> I'm surprised the cameras don't just work. I have a couple Thinkpads, purchased for a very good price off Ebay and the cameras just work. I don't use them but I used Cheese to verify their operation.

I'm also surprised it doesn't work. These days, especially with older hardware, things usually just WORK. The only two things I can think of are:

1) a hardware switch that I'm missing, or

2) the camera is broken. It doesn't appear in lspci or lsusb, and it should appear in lsusb.

---

### Post by ArthurPeale on 2020-12-25
Starting to think there isn't a camera inside. It LOOKS like I can see the lenses, but....

[https://linux-hardware.org/?probe=f9be11da76](https://linux-hardware.org/?probe=f9be11da76)

---

### Post by kurt18947 on 2020-12-27
I'm using a Thinkpad T410 now and yes the camera does appear with lsusb
```

Bus 001 Device 004: ID 17ef:480f Lenovo Integrated Webcam [R5U877]
Bus 001 Device 003: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor

```

---

### Post by rsteinmetz70112 on 2020-12-30
ThinkPads generally come in a lot of different configurations. See if you can check the exact model number - you should be able to find exactly what is in there. There are likely multiple versions of the SL500, typically there is a 4 digit additional number on the label on the back.

---

