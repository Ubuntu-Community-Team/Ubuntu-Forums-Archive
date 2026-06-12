---
title: "GPU fans keep spinning&#8252;"
date: 2017-12-20
forum: Hardware
---

### Post by qakcnyn on 2017-12-20
I bought a new video card few days ago. The GPU fans should stop when low temperature. And so do it when running Windows or before booting into Ubuntu. After entering Ubuntu, fans start and keep spinning. What should I do to stop the fans.
I didn't install any AMD drivers for GPU. The system is just fresh installed.

CPU: AMD Ryzen 1600
GPU: Asus ROG Strix RX580-T8G-GAMING
Motherboard: Asus Strix B350-F GAMING

---

### Post by #&amp;thj^% on 2017-12-20
Install the correct Video Driver for your New Video card.
It would help us to help you with more complete information.
1.Type of video card.
2.System installed.
3.Computer Specs etc.etc.
Otherwise we are just guessing.

---

### Post by sccman on 2017-12-20
Yeah the first step would be to install the graphics drivers so your computer can better manage your graphics card.

You can install them at the manufacturer's webpage. Your graphics card is an AMD Radeon RX 580:

[http://support.amd.com/en-us/download](http://support.amd.com/en-us/download)

---

### Post by QIII on 2017-12-20
What release of Ubuntu are you using?  Despite the fact that a driver is available, the kernel must also support the hardware/driver combination.  Had that been the case, AMDGPU would have been installed by default.  If the kernel is older, the RX580 may not have been released yet and so would not be recognized.  In that case, the Radeon driver would have been installed and fan control might not be available.

In any case, the release and kernel being used would be nice to know in order to continue.

---

### Post by qakcnyn on 2017-12-21
Ubuntu 17.10 is installed. And default amdgpu driver is been used. I have read some reviews that saying amdgpu-pro is not recommended as amdgpu. I'll try, but I still want a solution without amdgpu-pro.
Thanks.

Using latest amdgpu-pro (17.50) results failing to enter desktop. Using latest amdgpu (17.50) makes no difference as system default. And when failing to load amdgpu driver (when secure boot is on, it causes resolution back to 1024*768), the fans stop as expected. So the real suspect that makes fans unstoppable is amdgpu?

---

### Post by Yellow Pasque on 2017-12-21
Try the latest kernel to try the latest version of amdgpu: [https://wiki.ubuntu.com/Kernel/MainlineBuilds#Installing_upstream_kernels_.28manually.29](https://wiki.ubuntu.com/Kernel/MainlineBuilds#Installing_upstream_kernels_.28manually.29)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.15-rc4/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.15-rc4/)
I recommend first uninstalling everything that you installed with AMD's driver installer. I'm not sure exactly what it does to your system when you install the open source driver using their installer. That's a feature they just added in 17.50.

---

### Post by qakcnyn on 2017-12-22
Still not working. It seems nothing I can do to stop the fans. Unless not using amdgpu driver.

---

### Post by Autodave on 2017-12-22
Are the fans running at high speed or at very low speed? Being that this is a desktop, if the fans were running slowly, I would not have a problem at all with that.  Running at higher speeds would be an issue.

---

### Post by Yellow Pasque on 2017-12-22
Hmm. Try booting with "amdgpu.dc=1" in kernel parameter.
Also, check dmesg for complaints about firmware:
```
dmesg | grep -i firm
```

If it still doesn't work with latest upstream kernel, it seems like a bug. [https://bugs.freedesktop.org/enter_bug.cgi?product=DRI&component=DRM%2FAMDgpu](https://bugs.freedesktop.org/enter_bug.cgi?product=DRI&component=DRM%2FAMDgpu)

---

### Post by Yellow Pasque on 2017-12-22
> **Autodave said:**
> Are the fans running at high speed or at very low speed? Being that this is a desktop, if the fans were running slowly, I would not have a problem at all with that.  Running at higher speeds would be an issue.

It's an Asus Strix card, so the fans should stop completely at low temps (55C for this card). Maybe OP can check sensors. I think they would be supported with new kernel:
```
sensors
```

---

### Post by qakcnyn on 2017-12-23
Not work.

And ```
dmesg | grep -i firm
``` got these:

```
[    0.069007] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.087493] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.760686] [Firmware Bug]: ACPI MWAIT C-state 0x0 not supported by HW (0x0)
[    0.760801] [Firmware Bug]: ACPI MWAIT C-state 0x0 not supported by HW (0x0)
[    0.760879] [Firmware Bug]: ACPI MWAIT C-state 0x0 not supported by HW (0x0)
[    0.761000] [Firmware Bug]: ACPI MWAIT C-state 0x0 not supported by HW (0x0)
[    0.761114] [Firmware Bug]: ACPI MWAIT C-state 0x0 not supported by HW (0x0)
[    0.761182] [Firmware Bug]: ACPI MWAIT C-state 0x0 not supported by HW (0x0)
[    0.761311] [Firmware Bug]: ACPI MWAIT C-state 0x0 not supported by HW (0x0)
[    0.761446] [Firmware Bug]: ACPI MWAIT C-state 0x0 not supported by HW (0x0)
[    0.761610] [Firmware Bug]: ACPI MWAIT C-state 0x0 not supported by HW (0x0)
[    0.761737] [Firmware Bug]: ACPI MWAIT C-state 0x0 not supported by HW (0x0)
[    0.761871] [Firmware Bug]: ACPI MWAIT C-state 0x0 not supported by HW (0x0)
[    0.762001] [Firmware Bug]: ACPI MWAIT C-state 0x0 not supported by HW (0x0)
[    0.993179] amdgpu 0000:09:00.0: Direct firmware load for amdgpu/polaris10_pfp_2.bin failed with error -2
[    0.993200] amdgpu 0000:09:00.0: Direct firmware load for amdgpu/polaris10_me_2.bin failed with error -2
[    0.993216] amdgpu 0000:09:00.0: Direct firmware load for amdgpu/polaris10_ce_2.bin failed with error -2
[    0.993244] amdgpu 0000:09:00.0: Direct firmware load for amdgpu/polaris10_mec_2.bin failed with error -2
[    0.993294] amdgpu 0000:09:00.0: Direct firmware load for amdgpu/polaris10_mec2_2.bin failed with error -2
[    0.994152] [drm] Found UVD firmware Version: 1.79 Family ID: 16
[    0.994467] [drm] Found VCE firmware Version: 52.4 Binary ID: 3

```

---

### Post by Yellow Pasque on 2017-12-23
```
[    0.993179] amdgpu 0000:09:00.0: Direct firmware load for amdgpu/polaris10_pfp_2.bin failed with error -2
[    0.993200] amdgpu 0000:09:00.0: Direct firmware load for amdgpu/polaris10_me_2.bin failed with error -2
[    0.993216] amdgpu 0000:09:00.0: Direct firmware load for amdgpu/polaris10_ce_2.bin failed with error -2
[    0.993244] amdgpu 0000:09:00.0: Direct firmware load for amdgpu/polaris10_mec_2.bin failed with error -2
[    0.993294] amdgpu 0000:09:00.0: Direct firmware load for amdgpu/polaris10_mec2_2.bin failed with error -2
```

I would grab the missing firmware files (and put them in /lib/firmware/amdgpu)
[https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/amdgpu](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/amdgpu)

---

### Post by P-I H on 2017-12-23
Haven't thought about this until I read this post.
Copied and past the required firmware files, but i get the same messages.
However I'm using kernel 4.15-RC3 with GRUB_CMDLINE_LINUX="amdgpu.dc=1"

The gpu fan spins with about 1100 rpm, but I can't hear them.
```
p-i@pi-MS-7A34:~$ sensors
nct6793-isa-0a20
Adapter: ISA adapter
in0:                    +0.74 V  (min =  +0.00 V, max =  +1.74 V)
in1:                    +1.01 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in2:                    +3.47 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in3:                    +3.33 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in4:                    +1.03 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:                    +0.15 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in6:                    +0.75 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in7:                    +3.46 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in8:                    +3.41 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in9:                    +1.85 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in10:                   +0.00 V  (min =  +0.00 V, max =  +0.00 V)
in11:                   +1.06 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in12:                   +0.92 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in13:                   +0.68 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in14:                   +1.54 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
fan1:                   511 RPM  (min =    0 RPM)
fan2:                   415 RPM  (min =    0 RPM)
fan3:                   997 RPM  (min =    0 RPM)
fan4:                     0 RPM  (min =    0 RPM)
fan5:                   759 RPM  (min =    0 RPM)
SYSTIN:                 +36.0°C  (high = +127.0°C, hyst =  +0.0°C)  sensor = CPU diode
CPUTIN:                 +33.0°C  (high = +127.0°C, hyst = +105.0°C)  sensor = thermistor
AUXTIN0:                +40.0°C  (high = +127.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
AUXTIN1:               -128.0°C    sensor = thermistor
AUXTIN2:                +23.0°C    sensor = thermistor
AUXTIN3:                 -3.0°C    sensor = thermistor
SMBUSMASTER 0:          +30.0°C  (high = +127.0°C, hyst = +105.0°C)
PCH_CHIP_CPU_MAX_TEMP:   +0.0°C  
PCH_CHIP_TEMP:           +0.0°C  
PCH_CPU_TEMP:            +0.0°C  
intrusion0:            ALARM
intrusion1:            ALARM
beep_enable:           disabled


amdgpu-pci-2400
Adapter: PCI adapter
fan1:        1174 RPM
temp1:        +28.0°C  (crit =  +0.0°C, hyst =  +0.0°C)


k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +30.0°C  (high = +70.0°C)


p-i@pi-MS-7A34:~$
```

```
p-i@pi-MS-7A34:~$ dmesg | grep -i firm
[    0.076996] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.090927] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.995064] amdgpu 0000:24:00.0: Direct firmware load for amdgpu/polaris10_pfp_2.bin failed with error -2
[    0.995080] amdgpu 0000:24:00.0: Direct firmware load for amdgpu/polaris10_me_2.bin failed with error -2
[    0.995092] amdgpu 0000:24:00.0: Direct firmware load for amdgpu/polaris10_ce_2.bin failed with error -2
[    0.995114] amdgpu 0000:24:00.0: Direct firmware load for amdgpu/polaris10_mec_2.bin failed with error -2
[    0.995155] amdgpu 0000:24:00.0: Direct firmware load for amdgpu/polaris10_mec2_2.bin failed with error -2
[    0.995891] [drm] Found UVD firmware Version: 1.79 Family ID: 16
[    0.996236] [drm] Found VCE firmware Version: 52.4 Binary ID: 3
p-i@pi-MS-7A34:~$ 



```

---

### Post by Yellow Pasque on 2017-12-23
> Copied and past the required firmware files, but i get the same messages.

Thanks for confirming that. I guess the firmware files aren't necessary. I know AMD put out updated files (the ones with "_2" in the name), but I don't remember what the difference was, or if they even said what it was.

> The gpu fan spins with about 1100 rpm, but I can't hear them.

Are you using the same Strix RX580 card as the OP?

---

### Post by P-I H on 2017-12-23
I'm using a MSI Tomahawk B350, with a MSI Radeon RX 580 Gaming X 2xHDMI 2xDP 8GB
These are my specifications
```
p-i@pi-MS-7A34:~$ inxi -F
System:    Host: pi-MS-7A34 Kernel: 4.15.0-041500rc3-generic x86_64 bits: 64
           Desktop: Gnome 3.26.2
           Distro: Ubuntu Bionic Beaver (development branch)
Machine:   Device: desktop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0 serial: N/A
           UEFI: American Megatrends v: 1.90 date: 09/19/2017
CPU:       Octa core AMD Ryzen 7 1700 Eight-Core (-HT-MCP-) cache: 4096 KB
           clock speeds: max: 3560 MHz 1: 3003 MHz 2: 3027 MHz 3: 3018 MHz
           4: 3560 MHz 5: 3017 MHz 6: 3027 MHz 7: 3019 MHz 8: 3005 MHz
           9: 3002 MHz 10: 3000 MHz 11: 3004 MHz 12: 3028 MHz 13: 3000 MHz
           14: 2981 MHz 15: 3013 MHz 16: 3031 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 470/480]
           Display Server: wayland (X.Org 1.19.5 ) driver: amdgpu
           Resolution: 1920x1200@59.88hz
           OpenGL: renderer: Radeon RX 580 Series (AMD POLARIS10 / DRM 3.23.0 / 4.15.0-041500rc3-generic, LLVM 5.0.0)
           version: 4.5 Mesa 17.2.4
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 580]
           driver: snd_hda_intel
           Card-2 C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso
           Card-3 Logitech Webcam C250 driver: USB Audio
           Sound: ALSA v: k4.15.0-041500rc3-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp33s0 state: up speed: 1000 Mbps duplex: full
Drives:    HDD Total Size: 740.2GB (13.4% used)
           ID-1: /dev/nvme0n1 model: Samsung_SSD_960_EVO_250GB size: 250.1GB
           ID-2: /dev/sda model: SanDisk_Ultra_II size: 240.1GB
           ID-3: /dev/sdb model: Samsung_SSD_850 size: 250.1GB
Partition: ID-1: / size: 219G used: 93G (45%) fs: ext4 dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 35.0C mobo: 37.0C gpu: 30.0
           Fan Speeds (in rpm): cpu: N/A fan-1: 505 fan-2: 420 fan-3: 1002 fan-4: 0 fan-5: 802
Info:      Processes: 373 Uptime: 5:32 Memory: 3939.4/16056.5MB
           Client: Shell (bash) inxi: 2.3.45 
p-i@pi-MS-7A34:~$ 

```

---

### Post by qakcnyn on 2017-12-25
Still not work!

But, how stupid I am!!!

I have used fancontrol and pwmconfig to solve this. No new kernel, no additional firmware, no new driver. Just fancontrol.

But another problem occured.

The GPU temperature will keep going high. Until hit the MINTEMP of fancontrol, and fans spin.  After few seconds, the temperature drop below MINTEMP, fans stop. And then again and again.
This won't happen when using Windows.

---

