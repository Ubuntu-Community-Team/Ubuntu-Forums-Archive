---
title: "Making a second monitor visible HDMI-2..."
date: 2024-07-20
forum: Hardware
---

### Post by shantiq on 2024-07-20
I see Ubuntu and Linux reading around do not necessarily output to more than one monitor out-of-the-box
So I get given a 30" monitor for DigitalTV which i merely want to use as a monitor for films but no good at first :]


I do all of the following
inxi -Fxxz //  xrandr --query  // lspci   to find out about specs [see below]
I see some guys talk about going into the Bios    (reluctant is me :)
In the end i run ```
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get autoremove

``` with HDMI-1 and HDMI-2 plugged in PC to both monitors
And then reload PC   I think something happened there in the background; but not sure


Now all is seen both of them operating in unison


Cursor shifts from one to the other if i swipe mouse on mat; actually now it is a straightforward mirror; not sure why it changed but better that way


I leave both outcomes of Preferences/Monitor settings before and after
[[IMG]https://i.postimg.cc/SJ7wtjWz/Screenshot-from-2024-07-20-13-58-30.png[/IMG]]("https://postimg.cc/SJ7wtjWz")


[[IMG]https://i.postimg.cc/VdcxRXb8/Screenshot-from-2024-07-20-15-45-18.png[/IMG]]("https://postimg.cc/VdcxRXb8")





Hope this is of use to others
Will mark as solved






```
inxi -Fxxz
System:
  Kernel: 5.15.0-116-generic x86_64 bits: 64 compiler: gcc v: 11.4.0
    Desktop: LXDE 0.10.1 wm: Openbox dm: LXDM
    Distro: Ubuntu 22.04.4 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop Mobo: Acer model: Aspire XC-780 serial: <superuser required>
    UEFI: American Megatrends v: R01-A1 date: 06/22/2016
CPU:
  Info: dual core model: Intel Core i3-6100 bits: 64 type: MT MCP
    arch: Skylake-S rev: 3 cache: L1: 128 KiB L2: 512 KiB L3: 3 MiB
  Speed (MHz): avg: 1032 high: 1200 min/max: 800/3700 cores: 1: 1200
    2: 1131 3: 900 4: 900 bogomips: 29598
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel HD Graphics 530 vendor: Acer Incorporated ALI driver: i915
    v: kernel ports: active: HDMI-A-1,HDMI-A-2 empty: DP-1 bus-ID: 00:02.0
    chip-ID: 8086:1912
  Device-2: Logitech QuickCam E 3500 type: USB
    driver: snd-usb-audio,uvcvideo bus-ID: 1-4:3 chip-ID: 046d:09a4
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: modesetting
    unloaded: fbdev,vesa gpu: i915 display-ID: :0 screens: 1
  Screen-1: 0 s-res: 3840x1080 s-dpi: 96
  Monitor-1: HDMI-1 mapped: HDMI-A-1 pos: primary,left model: Acer S241HL
    res: 1920x1080 dpi: 92 diag: 609mm (24")
  Monitor-2: HDMI-2 mapped: HDMI-A-2 pos: right model: 32W_LCD_TV
    res: 1920x1080 dpi: 3048 diag: 184mm (7.2")
  OpenGL: renderer: Mesa Intel HD Graphics 530 (SKL GT2)
    v: 4.6 Mesa 23.2.1-1ubuntu3.1~22.04.2 direct render: Yes
Audio:
  Device-1: Intel 100 Series/C230 Series Family HD Audio
    vendor: Acer Incorporated ALI driver: snd_hda_intel v: kernel
    bus-ID: 00:1f.3 chip-ID: 8086:a170
  Device-2: Logitech QuickCam E 3500 type: USB
    driver: snd-usb-audio,uvcvideo bus-ID: 1-4:3 chip-ID: 046d:09a4
  Device-3: DigiTech Lexicon Alpha type: USB driver: snd-usb-audio
    bus-ID: 1-6:7 chip-ID: 1210:000a
  Sound Server-1: ALSA v: k5.15.0-116-generic running: yes
  Sound Server-2: JACK v: 1.9.20 running: no
  Sound Server-3: PulseAudio v: 15.99.1 running: yes
  Sound Server-4: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: Acer Incorporated ALI driver: r8169 v: kernel pcie: speed: 2.5 GT/s
    lanes: 1 port: e000 bus-ID: 01:00.0 chip-ID: 10ec:8168
  IF: enp1s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
  Device-2: Intel Wireless 3165 driver: iwlwifi v: kernel pcie:
    speed: 2.5 GT/s lanes: 1 bus-ID: 02:00.0 chip-ID: 8086:3165
  IF: wlp2s0 state: down mac: <filter>
Bluetooth:
  Device-1: Intel Bluetooth wireless interface type: USB driver: btusb v: 0.8
    bus-ID: 1-10:10 chip-ID: 8087:0a2a
  Report: hciconfig ID: hci0 rfk-id: 1 state: up address: <filter>
    bt-v: 2.1 lmp-v: 4.2 sub-v: 1000
Drives:
  Local Storage: total: 1.36 TiB used: 1.17 TiB (85.6%)
  ID-1: /dev/sda vendor: Toshiba model: DT01ACA100 size: 931.51 GiB
    speed: 6.0 Gb/s serial: <filter>
  ID-2: /dev/sdc type: USB vendor: Seagate model: ST3500630AS
    size: 465.76 GiB serial: <filter>
Partition:
  ID-1: / size: 908.41 GiB used: 779.07 GiB (85.8%) fs: ext4 dev: /dev/sda2
  ID-2: /boot/efi size: 511 MiB used: 6.1 MiB (1.2%) fs: vfat
    dev: /dev/sda1
Swap:
  ID-1: swap-1 type: partition size: 7.92 GiB used: 0 KiB (0.0%) priority: -2
    dev: /dev/sda3
Sensors:
  System Temperatures: cpu: 29.8 C pch: 49.0 C mobo: 27.8 C
  Fan Speeds (RPM): N/A
Info:
  Processes: 251 Uptime: 1h 0m Memory: 15.53 GiB used: 2.71 GiB (17.5%)
  Init: systemd v: 249 runlevel: 5 Compilers: gcc: 11.4.0 alt: 11/5/9
  clang: 14.0.0-1ubuntu1.1 Packages: 4848 note: see --pkg apt: 4804
  flatpak: 14 snap: 30 Shell: Bash v: 5.1.16 running-in: guake inxi: 3.3.13








===================


xrandr --query
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
HDMI-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 16mm x 9mm
   1920x1080i    60.00 +  50.00    59.94  
   1920x1080     24.00    23.98  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    70.07    60.00  
   1440x480i     59.94  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94  
HDMI-2 connected (normal left inverted right x axis y axis)
   1920x1080     60.00 +  50.00    59.94  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     59.88  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x960      60.00  
   1280x800      59.91  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94  
   720x400       70.08  
DP-1 disconnected (normal left inverted right x axis y axis)


=========




======================






lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Host Bridge/DRAM Registers (rev 07)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 530 (rev 06)
00:14.0 USB controller: Intel Corporation 100 Series/C230 Series Chipset Family USB 3.0 xHCI Controller (rev 31)
00:14.2 Signal processing controller: Intel Corporation 100 Series/C230 Series Chipset Family Thermal Subsystem (rev 31)
00:16.0 Communication controller: Intel Corporation 100 Series/C230 Series Chipset Family MEI Controller #1 (rev 31)
00:17.0 SATA controller: Intel Corporation Q170/Q150/B150/H170/H110/Z170/CM236 Chipset SATA Controller [AHCI Mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #5 (rev f1)
00:1c.5 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #6 (rev f1)
00:1f.0 ISA bridge: Intel Corporation H110 Chipset LPC/eSPI Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation 100 Series/C230 Series Chipset Family Power Management Controller (rev 31)
00:1f.3 Audio device: Intel Corporation 100 Series/C230 Series Chipset Family HD Audio Controller (rev 31)
00:1f.4 SMBus: Intel Corporation 100 Series/C230 Series Chipset Family SMBus (rev 31)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)
02:00.0 Network controller: Intel Corporation Wireless 3165 (rev 81)
shan@shan-Aspire-XC-780:~$ 
shan@shan-Aspire-XC-780:~$ sudo lshw -C display
[sudo] password for shan: 
  *-display                 
       description: VGA compatible controller
       product: HD Graphics 530
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 resolution=1920,1080
       resources: irq:129 memory:de000000-deffffff memory:c0000000-cfffffff ioport:f000(size=64) memory:c0000-dffff



```

---

