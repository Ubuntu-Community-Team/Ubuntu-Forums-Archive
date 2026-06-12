---
title: "Low resolution after executing some commands"
date: 2017-06-04
forum: Hardware
---

### Post by sujitjadhav on 2017-06-04
Hi,

After executing following commands graphics turned to low resolution. 

```
sudo apt-get purge virtualbox-dkms
sudo apt-get install virtualbox-dkms
sudo modprobe vboxdrv
```

I was asked by virtualbox to execute above commands after a virtual machine failed to start.

While executing above commands I was shown a message which said something which meant that UEFI secure boot was on and that it could create some problem to some drivers. It recommended that I disable UEFI secure boot. It also asked me to create an 8 character password to use when system reboot to authenticate to disable UEFI secure boot. The system did not reboot automatically after the command execution completed. So I manually restarted the system and found that graphics resolution turned to 1024X768 and that was the only available resolution.

```
sudo lshw -C video
[sudo] password for dfs: 
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: Mars [Radeon HD 8730M]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller cap_list
       configuration: latency=0
       resources: memory:a0000000-afffffff memory:c0000000-c003ffff ioport:3000(size=256) memory:c0040000-c005ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:c1000000-c13fffff memory:b0000000-bfffffff ioport:4000(size=64) memory:c0000-dffff

```

```
lspci -nnk | egrep -i '3d|aphics|display|nouveau|nvidia|radeon|trident|vesa|vga'
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: Dell 3rd Gen Core processor Graphics Controller [1028:05b8]
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Mars [Radeon HD 8730M] [1002:6601]
    Subsystem: Dell Mars [Radeon HD 8730M] [1028:05b8]
    Kernel modules: radeon

```

```
uname -a
Linux sujit-Inspiron-3521 4.8.0-52-generic #55-Ubuntu SMP Fri Apr 28 13:28:50 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


```

```
Xorg -version


X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
Current Operating System: Linux sujit-Inspiron-3521 4.8.0-52-generic #55-Ubuntu SMP Fri Apr 28 13:28:50 UTC 2017 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.8.0-52-generic.efi.signed root=UUID=d7a9908c-8178-44a1-ad9e-d52a9d3364d8 ro recovery nomodeset
Build Date: 02 November 2016  10:06:55PM
xorg-server 2:1.18.4-1ubuntu6.1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.33.6
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.



```


```
inxi -F
System:    Host: sujit-Inspiron-3521 Kernel: 4.8.0-52-generic x86_64 (64 bit) Desktop: KDE Plasma 5
           Distro: Ubuntu 16.10
Machine:   System: Dell (portable) product: Inspiron 5521 v: A05
           Mobo: Dell model: Type2 - Board Product Name1 v: Type2 - Board Version
           UEFI: Dell v: A05 date: 01/03/2013
Battery    BAT1: charge: 27.4 Wh 68.4% condition: 40.1/60.0 Wh (67%)
CPU:       Dual core Intel Core i5-3337U (-HT-MCP-) cache: 3072 KB 
           clock speeds: max: 2700 MHz 1: 1203 MHz 2: 873 MHz 3: 1488 MHz 4: 813 MHz
Graphics:  Card-1: Intel 3rd Gen Core processor Graphics Controller
           Card-2: Advanced Micro Devices [AMD/ATI] Mars [Radeon HD 8730M]
           Display Server: X.Org 1.18.4 drivers: fbdev (unloaded: vesa) Resolution: 1024x768@76.00hz
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.8, 256 bits) GLX Version: 3.0 Mesa 12.0.6
Audio:     Card Intel 7 Series/C216 Family High Definition Audio Controller driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.8.0-52-generic
Network:   Card-1: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller driver: r8169
           IF: enp7s0 state: down mac: f0:1f:af:16:7e:2d
           Card-2: Intel Centrino Wireless-N 2230 driver: iwlwifi
           IF: wlp8s0 state: up mac: 60:6c:66:27:44:71
Drives:    HDD Total Size: 1000.2GB (15.4% used) ID-1: /dev/sda model: ST1000LM024_HN size: 1000.2GB
Partition: ID-1: / size: 144G used: 132G (97%) fs: ext4 dev: /dev/sda7
           ID-2: swap-1 size: 8.55GB used: 0.69GB (8%) fs: swap dev: /dev/sda8
           ID-3: swap-2 size: 5.24GB used: 0.00GB (0%) fs: swap dev: /dev/sda13
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 55.0C mobo: N/A
           Fan Speeds (in rpm): cpu: 5100
Info:      Processes: 289 Uptime: 1:49 Memory: 3186.5/3820.2MB Client: Shell (bash) inxi: 2.3.1

```

```
dmesg | egrep 'drm|radeon'
[    2.052546] [drm] Initialized drm 1.1.0 20060810
[    2.112171] [drm] VGACON disable radeon kernel modesetting.
[    2.112927] [drm:radeon_init [radeon]] *ERROR* No UMS support in radeon module!
[   28.599123] [drm] VGACON disable radeon kernel modesetting.
[   28.599165] [drm:radeon_init [radeon]] *ERROR* No UMS support in radeon module!

```

Please help me restore graphics mode to higher resolution. Thanks in advance.

---

