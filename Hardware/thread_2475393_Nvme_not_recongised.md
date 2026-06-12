---
title: "Nvme not recongised"
date: 2022-05-25
forum: Hardware
---

### Post by andrewcrawford131 on 2022-05-25
I have a nvme raid card and it not being recognised I have about 2tb of data there so I would like to try get it added any idea I'm guessing deiver can I compile some from Windows drivers

---

### Post by rsteinmetz70112 on 2022-05-25
What doe 
```
$sudo lsblk show?
```

---

### Post by ajgreeny on 2022-05-25
Which version of Ubuntu are you using?
Please show us the output of command ***inxi -Fzx*** which will show us a lot about your hardware and software which may help.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

Bear in mind that updated firmware for the nvme disk may be needed for it to be detected, particularly on anything earlier than the most recent Ubuntu versions.

---

### Post by andrewcrawford131 on 2022-05-26
> **rsteinmetz70112 said:**
> What doe 
```
$sudo lsblk show?
```

```
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0         7:0    0     4K  1 loop /snap/bare/5
loop1         7:1    0  55.5M  1 loop /snap/core18/2409
loop2         7:2    0  61.9M  1 loop /snap/core20/1405
loop3         7:3    0  61.9M  1 loop /snap/core20/1494
loop4         7:4    0  82.9M  1 loop /snap/discord/132
loop5         7:5    0 155.6M  1 loop /snap/firefox/1232
loop6         7:6    0 160.5M  1 loop /snap/firefox/1377
loop7         7:7    0 164.8M  1 loop /snap/gnome-3-28-1804/161
loop8         7:8    0 248.8M  1 loop /snap/gnome-3-38-2004/99
loop9         7:9    0  81.3M  1 loop /snap/gtk-common-themes/1534
loop10        7:10   0 399.4M  1 loop /snap/obs-studio/1284
loop11        7:11   0  43.6M  1 loop /snap/snapd/15177
loop12        7:12   0  44.7M  1 loop /snap/snapd/15904
sda           8:0    0   2.7T  0 disk 
&#9500;&#9472;sda1        8:1    0     1M  0 part 
&#9500;&#9472;sda2        8:2    0   127M  0 part 
&#9492;&#9472;sda3        8:3    0   2.7T  0 part 
sdb           8:16   0   3.6T  0 disk 
&#9500;&#9472;sdb1        8:17   0     1M  0 part 
&#9500;&#9472;sdb2        8:18   0   127M  0 part 
&#9492;&#9472;sdb3        8:19   0   3.6T  0 part 
sdc           8:32   0 232.9G  0 disk 
&#9500;&#9472;sdc1        8:33   0   100M  0 part 
&#9500;&#9472;sdc2        8:34   0     1M  0 part 
&#9500;&#9472;sdc3        8:35   0   127M  0 part 
&#9492;&#9472;sdc4        8:36   0 232.7G  0 part 
sdd           8:48   0 238.5G  0 disk 
&#9500;&#9472;sdd1        8:49   0    16M  0 part 
&#9492;&#9472;sdd2        8:50   0 238.5G  0 part 
sde           8:64   1     0B  0 disk 
sr0          11:0    1  41.8G  0 rom  
sr1          11:1    1  1024M  0 rom  
nvme0n1     259:0    0   3.6T  0 disk 
&#9500;&#9472;nvme0n1p1 259:1    0   512M  0 part /boot/efi
&#9492;&#9472;nvme0n1p2 259:2    0   3.6T  0 part /


```

---

### Post by andrewcrawford131 on 2022-05-26
> **ajgreeny said:**
> Which version of Ubuntu are you using?
Please show us the output of command ***inxi -Fzx*** which will show us a lot about your hardware and software which may help.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

Bear in mind that updated firmware for the nvme disk may be needed for it to be detected, particularly on anything earlier than the most recent Ubuntu versions.

```
System:
  Kernel: 5.15.0-33-generic x86_64 bits: 64 compiler: gcc v: 11.2.0
    Desktop: Xfce 4.16.0 Distro: Ubuntu 22.04 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop Mobo: Gigabyte model: X99-Designare EX-CF serial: N/A
    UEFI: American Megatrends v: F2 date: 05/22/2016
CPU:
  Info: 6-core model: Intel Core i7-6850K bits: 64 type: MT MCP
    arch: Broadwell rev: 1 cache: L1: 384 KiB L2: 1.5 MiB L3: 15 MiB
  Speed (MHz): avg: 1344 high: 2070 min/max: 1200/4000 cores: 1: 1200
    2: 1201 3: 1201 4: 1861 5: 1200 6: 1396 7: 1200 8: 1201 9: 1201 10: 2070
    11: 1200 12: 1201 bogomips: 86400
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: NVIDIA GK104 [GeForce GTX 760] vendor: eVga.com. driver: nvidia
    v: 470.129.06 bus-ID: 4f:00.0
  Device-2: NVIDIA GK104 [GeForce GTX 760] vendor: eVga.com. driver: nvidia
    v: 470.129.06 bus-ID: 50:00.0
  Display: server: X.Org v: 1.21.1.3 driver: X: loaded: nvidia
    unloaded: fbdev,modesetting,nouveau,vesa gpu: nvidia,nvidia
    resolution: 1920x1080~60Hz
  OpenGL: renderer: NVIDIA GeForce GTX 760/PCIe/SSE2
    v: 4.6.0 NVIDIA 470.129.06 direct render: Yes
Audio:
  Device-1: Intel C610/X99 series HD Audio vendor: Gigabyte
    driver: snd_hda_intel v: kernel bus-ID: 00:1b.0
  Device-2: NVIDIA GK104 HDMI Audio vendor: eVga.com. driver: snd_hda_intel
    v: kernel bus-ID: 4f:00.1
  Device-3: NVIDIA GK104 HDMI Audio vendor: eVga.com. driver: snd_hda_intel
    v: kernel bus-ID: 50:00.1
  Sound Server-1: ALSA v: k5.15.0-33-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Intel Ethernet I218-V vendor: Gigabyte driver: e1000e v: kernel
    port: f020 bus-ID: 00:19.0
  IF: eno1 state: up speed: 1000 Mbps duplex: full mac: <filter>
  Device-2: Intel I211 Gigabit Network vendor: Gigabyte driver: igb
    v: kernel port: c000 bus-ID: 52:00.0
  IF: enp82s0 state: down mac: <filter>
  Device-3: Intel Wireless 8260 driver: iwlwifi v: kernel bus-ID: 53:00.0
  IF: wlp83s0 state: down mac: <filter>
Bluetooth:
  Device-1: Intel Bluetooth wireless interface type: USB driver: btusb v: 0.8
    bus-ID: 3-3:2
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter>
    bt-v: 2.1 lmp-v: 4.2
Drives:
  Local Storage: total: 10.47 TiB used: 12.49 GiB (0.1%)
  ID-1: /dev/nvme0n1 vendor: Corsair model: Corsair MP400 size: 3.64 TiB
    temp: 25.9 C
  ID-2: /dev/sda vendor: Western Digital model: WD30EZRX-00AZ6B0
    size: 2.73 TiB
  ID-3: /dev/sdb vendor: Seagate model: ST4000DX001-1CE168 size: 3.64 TiB
  ID-4: /dev/sdc vendor: Samsung model: SSD 840 EVO 250GB size: 232.89 GiB
  ID-5: /dev/sdd vendor: Samsung model: SSD 850 PRO 256GB size: 238.47 GiB
Partition:
  ID-1: / size: 3.58 TiB used: 12.48 GiB (0.3%) fs: ext4 dev: /dev/nvme0n1p2
  ID-2: /boot/efi size: 511 MiB used: 5.2 MiB (1.0%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 53.0 C mobo: N/A gpu: nvidia temp: 35 C
  Fan Speeds (RPM): N/A gpu: nvidia fan: 47%
Info:
  Processes: 331 Uptime: 3m Memory: 62.65 GiB used: 1.78 GiB (2.8%)
  Init: systemd runlevel: 5 Compilers: gcc: N/A Packages: 1766 Shell: Sudo
  v: 1.9.9 inxi: 3.3.13

```

it recongises one of the nvme which is on the motherboard the other 4 are on raid card it doesnt see them

---

### Post by rsteinmetz70112 on 2022-05-26
What is the RAID Card? does it show up in ```
$ sudo lspci
```

---

### Post by andrewcrawford131 on 2022-05-27
> **rsteinmetz70112 said:**
> What is the RAID Card? does it show up in ```
$ sudo lspci
```

```
[sudo] password for andy: 
00:00.0 Host bridge: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DMI2 (rev 01)
00:01.0 PCI bridge: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D PCI Express Root Port 1 (rev 01)
00:01.1 PCI bridge: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D PCI Express Root Port 1 (rev 01)
00:02.0 PCI bridge: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D PCI Express Root Port 2 (rev 01)
00:03.0 PCI bridge: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D PCI Express Root Port 3 (rev 01)
00:05.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Map/VTd_Misc/System Management (rev 01)
00:05.1 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D IIO Hot Plug (rev 01)
00:05.2 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D IIO RAS/Control Status/Global Errors (rev 01)
00:11.0 Unassigned class [ff00]: Intel Corporation C610/X99 series chipset SPSR (rev 05)
00:11.4 SATA controller: Intel Corporation C610/X99 series chipset sSATA Controller [AHCI mode] (rev 05)
00:14.0 USB controller: Intel Corporation C610/X99 series chipset USB xHCI Host Controller (rev 05)
00:16.0 Communication controller: Intel Corporation C610/X99 series chipset MEI Controller #1 (rev 05)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection (2) I218-V (rev 05)
00:1a.0 USB controller: Intel Corporation C610/X99 series chipset USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation C610/X99 series chipset HD Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation C610/X99 series chipset PCI Express Root Port #1 (rev d5)
00:1c.5 PCI bridge: Intel Corporation C610/X99 series chipset PCI Express Root Port #6 (rev d5)
00:1c.7 PCI bridge: Intel Corporation C610/X99 series chipset PCI Express Root Port #8 (rev d5)
00:1d.0 USB controller: Intel Corporation C610/X99 series chipset USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation C610/X99 series chipset LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation C610/X99 series chipset 6-Port SATA Controller [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation C610/X99 series chipset SMBus Controller (rev 05)
02:00.0 PCI bridge: Intel Corporation DSL6540 Thunderbolt 3 Bridge [Alpine Ridge 4C 2015]
03:00.0 PCI bridge: Intel Corporation DSL6540 Thunderbolt 3 Bridge [Alpine Ridge 4C 2015]
03:01.0 PCI bridge: Intel Corporation DSL6540 Thunderbolt 3 Bridge [Alpine Ridge 4C 2015]
03:02.0 PCI bridge: Intel Corporation DSL6540 Thunderbolt 3 Bridge [Alpine Ridge 4C 2015]
03:04.0 PCI bridge: Intel Corporation DSL6540 Thunderbolt 3 Bridge [Alpine Ridge 4C 2015]
04:00.0 System peripheral: Intel Corporation DSL6540 Thunderbolt 3 NHI [Alpine Ridge 4C 2015]
49:00.0 USB controller: Intel Corporation DSL6540 USB 3.1 Controller [Alpine Ridge]
4b:00.0 PCI bridge: PLX Technology, Inc. PEX 8747 48-Lane, 5-Port PCI Express Gen 3 (8.0 GT/s) Switch (rev ca)
4c:08.0 PCI bridge: PLX Technology, Inc. PEX 8747 48-Lane, 5-Port PCI Express Gen 3 (8.0 GT/s) Switch (rev ca)
4c:09.0 PCI bridge: PLX Technology, Inc. PEX 8747 48-Lane, 5-Port PCI Express Gen 3 (8.0 GT/s) Switch (rev ca)
4c:10.0 PCI bridge: PLX Technology, Inc. PEX 8747 48-Lane, 5-Port PCI Express Gen 3 (8.0 GT/s) Switch (rev ca)
4d:00.0 Non-Volatile memory controller: Phison Electronics Corporation E12 NVMe Controller (rev 01)
4f:00.0 VGA compatible controller: NVIDIA Corporation GK104 [GeForce GTX 760] (rev a1)
4f:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)
50:00.0 VGA compatible controller: NVIDIA Corporation GK104 [GeForce GTX 760] (rev a1)
50:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)
52:00.0 Ethernet controller: Intel Corporation I211 Gigabit Network Connection (rev 03)
53:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)
ff:0b.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D R3 QPI Link 0/1 (rev 01)
ff:0b.1 Performance counters: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D R3 QPI Link 0/1 (rev 01)
ff:0b.2 Performance counters: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D R3 QPI Link 0/1 (rev 01)
ff:0b.3 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D R3 QPI Link Debug (rev 01)
ff:0c.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0c.1 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0c.2 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0c.3 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0c.4 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0c.5 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0f.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0f.1 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0f.4 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0f.5 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:0f.6 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Caching Agent (rev 01)
ff:10.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D R2PCIe Agent (rev 01)
ff:10.1 Performance counters: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D R2PCIe Agent (rev 01)
ff:10.5 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Ubox (rev 01)
ff:10.6 Performance counters: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Ubox (rev 01)
ff:10.7 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Ubox (rev 01)
ff:12.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Home Agent 0 (rev 01)
ff:12.1 Performance counters: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Home Agent 0 (rev 01)
ff:13.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 0 - Target Address/Thermal/RAS (rev 01)
ff:13.1 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 0 - Target Address/Thermal/RAS (rev 01)
ff:13.2 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 0 - Channel Target Address Decoder (rev 01)
ff:13.3 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 0 - Channel Target Address Decoder (rev 01)
ff:13.4 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 0 - Channel Target Address Decoder (rev 01)
ff:13.5 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 0 - Channel Target Address Decoder (rev 01)
ff:13.6 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Channel 0/1 Broadcast (rev 01)
ff:13.7 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Global Broadcast (rev 01)
ff:14.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 0 - Channel 0 Thermal Control (rev 01)
ff:14.1 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 0 - Channel 1 Thermal Control (rev 01)
ff:14.2 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 0 - Channel 0 Error (rev 01)
ff:14.3 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 0 - Channel 1 Error (rev 01)
ff:14.4 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Channel 0/1 Interface (rev 01)
ff:14.5 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Channel 0/1 Interface (rev 01)
ff:14.6 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Channel 0/1 Interface (rev 01)
ff:14.7 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Channel 0/1 Interface (rev 01)
ff:15.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 0 - Channel 2 Thermal Control (rev 01)
ff:15.1 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 0 - Channel 3 Thermal Control (rev 01)
ff:15.2 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 0 - Channel 2 Error (rev 01)
ff:15.3 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 0 - Channel 3 Error (rev 01)
ff:16.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Target Address/Thermal/RAS (rev 01)
ff:16.6 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Channel 2/3 Broadcast (rev 01)
ff:16.7 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Global Broadcast (rev 01)
ff:17.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Memory Controller 1 - Channel 0 Thermal Control (rev 01)
ff:17.4 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Channel 2/3 Interface (rev 01)
ff:17.5 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Channel 2/3 Interface (rev 01)
ff:17.6 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Channel 2/3 Interface (rev 01)
ff:17.7 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D DDRIO Channel 2/3 Interface (rev 01)
ff:1e.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Power Control Unit (rev 01)
ff:1e.1 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Power Control Unit (rev 01)
ff:1e.2 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Power Control Unit (rev 01)
ff:1e.3 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Power Control Unit (rev 01)
ff:1e.4 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Power Control Unit (rev 01)
ff:1f.0 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Power Control Unit (rev 01)
ff:1f.2 System peripheral: Intel Corporation Xeon E7 v4/Xeon E5 v4/Xeon E3 v4/Xeon D Power Control Unit (rev 01)


```

its a asus hyper m2 x16 card v2

it looks like it there

---

### Post by rsteinmetz70112 on 2022-05-27
Look at this:

[https://www.asus.com/support/FAQ/1037507](https://www.asus.com/support/FAQ/1037507)

It appears that different motherboards, Intel chipsets and GPUs support different configurations.
I think it's time for a deep dive into the Gigabyte model: X99-Designare EX-CF motherboard and the NVIDIA GK104 [GeForce GTX 760] GPU.
It looks like when the on-board M.2 or U.2 slots are used the associated PCIe slot is reduced in capability and when an i7-5820K or i7-6800K CPU is installed, the U2_32G_1 connector becomes unavailable. I'm not sure if that also applies to the i7-6850K.

Possibly swapping the card around might help.

I'm afraid this is over my head.
Good luck.

---

### Post by andrewcrawford131 on 2022-05-27
> **rsteinmetz70112 said:**
> Look at this:

[https://www.asus.com/support/FAQ/1037507](https://www.asus.com/support/FAQ/1037507)

It appears that different motherboards, Intel chipsets and GPUs support different configurations.
I think it's time for a deep dive into the Gigabyte model: X99-Designare EX-CF motherboard and the NVIDIA GK104 [GeForce GTX 760] GPU.
It looks like when the on-board M.2 or U.2 slots are used the associated PCIe slot is reduced in capability and when an i7-5820K or i7-6800K CPU is installed, the U2_32G_1 connector becomes unavailable. I'm not sure if that also applies to the i7-6850K.

Possibly swapping the card around might help.

I'm afraid this is over my head.
Good luck.

Going on that taking the 2nd graphic card out might help will post the results when I'm home

---

### Post by andrewcrawford131 on 2022-05-28
Taking out the graphics card the 2nd one means i can now see one of the drives im guessing that is all i will be able to see because of hardware limations or can i do anything to bring the other 3 online

---

