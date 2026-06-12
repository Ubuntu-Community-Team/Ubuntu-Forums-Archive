---
title: "No driver for Intel integrated graphics, Ubuntu 22.04.04 LTS"
date: 2024-03-11
forum: Hardware
---

### Post by nehc0 on 2024-03-11
I bought a laptop "Lenovo ThinkBook 14+" recently. This is a newly released machine version. Its original OS is Windows 11 and I freshly install a Ubuntu 22.04.04 LTS on it. However, it seems that there is no available driver for my laptop's integrated graphics in linux distro. The CPU is Intel Core Ultra 5 125H, which was released just several months ago. 

Now it's using the llvmpipe for graphics. I can't change the resolution and fresh rate of the "Unknown Display". My question is that is it my only choice to wait for a higher version of Ubuntu, e.g., 24.04? If so, is there any harm for my laptop to keep using the llvmpipe for graphics?

Machine config:
```

System:
  Host: chen-laptop Kernel: 6.5.0-25-generic x86_64 bits: 64
    Desktop: GNOME 42.9 Distro: Ubuntu 22.04.4 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: LENOVO product: 21LD v: ThinkBook 14 G6+ IMH
    serial: <superuser required>
  Mobo: LENOVO model: LNVNB161216 v: SDK0T76479 WIN
    serial: <superuser required> UEFI: LENOVO v: NJCN28WW date: 01/08/2024
Battery:
  ID-1: BAT1 charge: 88.0 Wh (100.0%) condition: 88.0/85.0 Wh (103.5%)
CPU:
  Info: 14-core (4-mt/10-st) Intel Core Ultra 5 125H [MST AMCP] speed (MHz):
    avg: 829 min/max: 400/4400:3600:2500
Graphics:
  Device-1: Intel driver: N/A
  Device-2: Luxvisions Innotech Integrated RGB Camera type: USB
    driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: vesa
    unloaded: fbdev,modesetting gpu: N/A resolution: 3072x1920~90Hz
  OpenGL: renderer: llvmpipe (LLVM 15.0.7 256 bits)
    v: 4.5 Mesa 23.2.1-1ubuntu3.1~22.04.2
Network:
  Device-1: Intel driver: iwlwifi
  Device-2: Intel driver: e1000e
Drives:
  Local Storage: total: 953.87 GiB used: 11.59 GiB (1.2%)
Info:
  Processes: 372 Uptime: 18m Memory: 30.95 GiB used: 2.94 GiB (9.5%)
  Shell: Bash inxi: 3.3.13

```

---

### Post by Yellow Pasque on 2024-03-11
You can try force probe kernel option, or you can run the latest kernel: [https://www.phoronix.com/news/Intel-MTL-Graphics-Linux-Stable](https://www.phoronix.com/news/Intel-MTL-Graphics-Linux-Stable)

---

### Post by MAFoElffen on 2024-03-11
Unfortunately, the kernel that supports your CPU is minimum version 6.6. Mantic 23.10's current (today) is still in the 6.5 series.

DEV Noble beta is fairly stable right now. Expect there will be many changes before it's release next month... But it does have kernel 6.8. which supports that CPU and it's internal ARC iGPU.

Usually I would not recommend a daily build ISO to a normal user, but your hardware is not supported by anything else out yet:
RE: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

We're trying.

---

### Post by MAFoElffen on 2024-03-11
Just a further note...

I would say maybe to install the 3rd party Intel ARC Driver's from Intel... But I can tell you that I'm already working with two upstream Intel Graphics Support Engineer Teams on their 3rd party graphic driver "issues", so you would have to upgrade your kernel to at least 6.6 to use them for that CPU/iGPU combination...

---

### Post by nehc0 on 2024-03-12
Thanks for your information and your work! I will just wait for the 24.04 to see whether it would work for me.

---

### Post by MAFoElffen on 2024-03-12
The release date is set for next month, April 24th, 2024.

---

### Post by Yellow Pasque on 2024-03-12
You could always install a mainline kernel into your current 23.10: [https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[https://kernel.ubuntu.com/mainline/v6.7.9/](https://kernel.ubuntu.com/mainline/v6.7.9/)
Remember, you have to turn off SecureBoot in the BIOS/EFI or sign the kernel yourself.

The other option is to use force probe on the current 6.5 kernel and see if it's stable. If you're confused about that, give the output of lspci:
```
sudo update-pciids
lspci
```

As to whether it's harmful to use llvmpipe, probably not. It cetainly harms graphics performance and it may make your CPU run warmer since graphics tasks are now being done less efficiently. As long as your system cooler is sufficient, it shouldn't be harmful.

---

### Post by nehc0 on 2024-03-13
the output of lspci:
```

00:00.0 Host bridge: Intel Corporation Device 7d14 (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Meteor Lake-P [Intel Arc Graphics] (rev 08)
00:04.0 Signal processing controller: Intel Corporation Device 7d03 (rev 04)
00:06.0 PCI bridge: Intel Corporation Device 7e4d (rev 20)
00:06.2 PCI bridge: Intel Corporation Device 7ecb (rev 10)
00:07.0 PCI bridge: Intel Corporation Meteor Lake-P Thunderbolt 4 PCI Express Root Port #2 (rev 10)
00:08.0 System peripheral: Intel Corporation Device 7e4c (rev 20)
00:0a.0 Signal processing controller: Intel Corporation Device 7d0d (rev 01)
00:0b.0 Processing accelerators: Intel Corporation Meteor Lake NPU (rev 04)
00:0d.0 USB controller: Intel Corporation Meteor Lake-P Thunderbolt 4 USB Controller (rev 10)
00:0d.3 USB controller: Intel Corporation Meteor Lake-P Thunderbolt 4 NHI #1 (rev 10)
00:12.0 Serial controller: Intel Corporation Device 7e45 (rev 20)
00:14.0 USB controller: Intel Corporation Meteor Lake-P USB 3.2 Gen 2x1 xHCI Host Controller (rev 20)
00:14.2 RAM memory: Intel Corporation Device 7e7f (rev 20)
00:14.3 Network controller: Intel Corporation Device 7e40 (rev 20)
00:15.0 Serial bus controller: Intel Corporation Meteor Lake-P Serial IO I2C Controller #0 (rev 20)
00:15.2 Serial bus controller: Intel Corporation Meteor Lake-P Serial IO I2C Controller #2 (rev 20)
00:15.3 Serial bus controller: Intel Corporation Meteor Lake-P Serial IO I2C Controller #3 (rev 20)
00:16.0 Communication controller: Intel Corporation Device 7e70 (rev 20)
00:19.0 Serial bus controller: Intel Corporation Meteor Lake-P Serial IO I2C Controller #4 (rev 20)
00:19.1 Serial bus controller: Intel Corporation Meteor Lake-P Serial IO I2C Controller #5 (rev 20)
00:1c.0 PCI bridge: Intel Corporation Device 7e39 (rev 20)
00:1f.0 ISA bridge: Intel Corporation Device 7e02 (rev 20)
00:1f.3 Multimedia audio controller: Intel Corporation Meteor Lake-P HD Audio Controller (rev 20)
00:1f.4 SMBus: Intel Corporation Meteor Lake-P SMBus Controller (rev 20)
00:1f.5 Serial bus controller: Intel Corporation Meteor Lake-P SPI Controller (rev 20)
00:1f.6 Ethernet controller: Intel Corporation Device 550b (rev 20)
06:00.0 Non-Volatile memory controller: Shenzhen Unionmemory Information System Ltd. Device 6b14 (rev 03)
31:00.0 SD Host controller: O2 Micro, Inc. SD/MMC Card Reader Controller (rev 01)

```

---

### Post by Yellow Pasque on 2024-03-13
```
echo "options i915 force_probe=7d55" | sudo tee -a /etc/modprobe.d/i915.conf
```
Reboot. Keep in mind that this isn't "officially stable" according to Intel, so if you have issues, revert the change (by deleting the file you created) and reboot.
```
sudo rm /etc/modprobe.d/i915.conf
```

---

### Post by Yellow Pasque on 2024-03-13
> **Yellow Pasque said:**
> ```
echo "options i915 force_probe=7d55" | sudo tee -a /etc/modprobe.d/i915.conf
```
Reboot. Keep in mind that this isn't "officially stable" according to Intel, so if you have issues, revert the change (by deleting the file you created) and reboot.
```
sudo rm /etc/modprobe.d/i915.conf
```

Sorry, I botched the command I gave in the previous post.

---

### Post by nehc0 on 2024-03-14
Thanks! It seems working! Now I have a driver for graphics and the fresh rate and resolution can be adjusted~
```

Graphics:
  Device-1: Intel Meteor Lake-P [Intel Arc Graphics] driver: i915 v: kernel
  Device-2: Luxvisions Innotech Integrated RGB Camera type: USB
    driver: uvcvideo
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell v: 42.9 driver: X: loaded: vesa
    unloaded: fbdev,modesetting gpu: i915 resolution: 3072x1920~120Hz
  OpenGL: renderer: Mesa Intel Arc Graphics (MTL)
    v: 4.6 Mesa 23.2.1-1ubuntu3.1~22.04.2

```

---

