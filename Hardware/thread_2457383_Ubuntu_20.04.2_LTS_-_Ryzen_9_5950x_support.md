---
title: "Ubuntu 20.04.2 LTS - Ryzen 9 5950x support"
date: 2021-02-01
forum: Hardware
---

### Post by bsquare on 2021-02-01
Hello everyone,

I'm one of the impatient waiter about Ubuntu 20.04.2 LTS, and I've finally got it installed on my computer yesterday.
Nevertheless:
 - i'm unable to find official Realase Notes of the version 20.04.**2**, are there available somewhere? (I read it was expected to be out later in February 2021)
 - I still have only 5.8.x as newest kernel available; I've understood 5.10.x is needed to fully support Ryzen 9 5950x; do you confirm?

Thanks.

---

### Post by P-I H on 2021-02-01
I'm have a Ryzen 5 5600X and use Hippo Hirsute, development version of Ubuntu 21.04. I enabled Developer Option to get the linux 10 kernel. After the update I turned it off as it's a higher risk of breaks with Developer Option enabled.
It's working fine, but you may get breaks. This is my configuration
```
p-i@pi-tuf-b550m-wifi:~$ inxi -Fz
System:    Kernel: 5.10.0-13-generic x86_64 bits: 64 Desktop: Cinnamon 4.8.6 
           Distro: Ubuntu 21.04 (Hirsute Hippo) 
Machine:   Type: Desktop System: ASUS product: N/A v: N/A serial: <filter> 
           Mobo: ASUSTeK model: TUF GAMING B550M-PLUS (WI-FI) v: Rev X.0x serial: <filter> 
           UEFI: American Megatrends v: 1212 date: 11/04/2020 
CPU:       Info: 6-Core model: AMD Ryzen 5 5600X bits: 64 type: MT MCP L2 cache: 3 MiB 
           Speed: 2192 MHz min/max: 2200/3700 MHz Core speeds (MHz): 1: 2192 2: 2101 3: 2199 4: 2600 
           5: 2197 6: 1898 7: 1968 8: 2239 9: 2137 10: 2118 11: 2199 12: 2192 
Graphics:  Device-1: AMD Navi 10 [Radeon RX 5600 OEM/5600 XT / 5700/5700 XT] driver: amdgpu v: kernel 
           Display: x11 server: X.Org 1.20.9 driver: loaded: amdgpu,ati 
           unloaded: fbdev,modesetting,radeon,vesa resolution: 2560x1440~60Hz 
           OpenGL: renderer: AMD Radeon RX 5700 (NAVI10 DRM 3.40.0 5.10.0-13-generic LLVM 11.0.1) 
           v: 4.6 Mesa 20.3.4 
Audio:     Device-1: AMD Navi 10 HDMI Audio driver: snd_hda_intel 
           Device-2: AMD Starship/Matisse HD Audio driver: snd_hda_intel 
           Device-3: Logitech Webcam C250 type: USB driver: snd-usb-audio,uvcvideo 
           Sound Server: ALSA v: k5.10.0-13-generic 
Network:   Device-1: Intel Wi-Fi 6 AX200 driver: iwlwifi 
           IF: wlp6s0 state: up mac: <filter> 
           Device-2: Realtek RTL8125 2.5GbE driver: r8169 
           IF: enp7s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 1.36 TiB used: 52 GiB (3.7%) 
           ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 970 EVO 500GB size: 465.76 GiB 
           ID-2: /dev/nvme1n1 vendor: Kingston model: SA2000M8500G size: 465.76 GiB 
           ID-3: /dev/sda vendor: Samsung model: SSD 860 EVO 500GB size: 465.76 GiB 
Partition: ID-1: / size: 456.96 GiB used: 51.96 GiB (11.4%) fs: ext4 dev: /dev/nvme0n1p2 
           ID-2: /boot/efi size: 511 MiB used: 37.3 MiB (7.3%) fs: vfat dev: /dev/nvme0n1p1 
Swap:      ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile 
Sensors:   System Temperatures: cpu: 35.6 C mobo: 39.0 C gpu: amdgpu temp: 43.0 C 
           Fan Speeds (RPM): fan-1: 853 fan-2: 865 fan-3: 810 fan-7: 0 gpu: amdgpu fan: 0 
Info:      Processes: 380 Uptime: 4h 01m Memory: 15.54 GiB used: 2.87 GiB (18.5%) Shell: Bash 
           inxi: 3.2.02 
p-i@pi-tuf-b550m-wifi:~$

```

---

### Post by bsquare on 2021-02-02
Thanks for your answer.
By any chance, with this version, do you have good sensors feedbacks? (on my side 0% about CPU and Fans ...).

---

### Post by P-I H on 2021-02-02
Sensors support depends very much on the motherboard and some settings.
I get this from the sensors command
```
p-i@pi-tuf-b550m-wifi:~$ sensors
amdgpu-pci-0a00
Adapter: PCI adapter
vddgfx:      800.00 mV 
fan1:           0 RPM  (min =    0 RPM, max = 2970 RPM)
edge:         +51.0°C  (crit = +100.0°C, hyst = -273.1°C)
                       (emerg = +105.0°C)
junction:     +51.0°C  (crit = +110.0°C, hyst = -273.1°C)
                       (emerg = +115.0°C)
mem:          +52.0°C  (crit = +105.0°C, hyst = -273.1°C)
                       (emerg = +110.0°C)
power1:        9.00 W  (cap = 180.00 W)


nct6798-isa-0290
Adapter: ISA adapter
in0:                      464.00 mV (min =  +0.00 V, max =  +1.74 V)
in1:                      1000.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in2:                        3.41 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in3:                        3.28 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in4:                        1.02 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:                      688.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in6:                      264.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in7:                        3.41 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in8:                        3.36 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in9:                      912.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in10:                     344.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in11:                     344.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in12:                       1.03 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in13:                     992.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in14:                       1.01 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
fan1:                      854 RPM  (min =    0 RPM)
fan2:                      901 RPM  (min =    0 RPM)
fan3:                      821 RPM  (min =    0 RPM)
fan7:                        0 RPM  (min =    0 RPM)
SYSTIN:                    +44.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
CPUTIN:                    +32.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
AUXTIN0:                   +82.5°C    sensor = thermistor
AUXTIN1:                   +44.0°C    sensor = thermistor
AUXTIN2:                   +44.0°C    sensor = thermistor
AUXTIN3:                   +25.0°C    sensor = thermistor
PECI Agent 0 Calibration:  +32.5°C  
PCH_CHIP_CPU_MAX_TEMP:      +0.0°C  
PCH_CHIP_TEMP:              +0.0°C  
PCH_CPU_TEMP:               +0.0°C  
intrusion0:               ALARM
intrusion1:               ALARM
beep_enable:              disabled


nvme-pci-0100
Adapter: PCI adapter
Composite:    +37.9°C  (low  = -273.1°C, high = +84.8°C)
                       (crit = +84.8°C)
Sensor 1:     +37.9°C  (low  = -273.1°C, high = +65261.8°C)
Sensor 2:     +42.9°C  (low  = -273.1°C, high = +65261.8°C)


iwlwifi_1-virtual-0
Adapter: Virtual device
temp1:        +34.0°C  


k10temp-pci-00c3
Adapter: PCI adapter
Tctl:         +36.5°C  
Tdie:         +36.5°C  


nvme-pci-0500
Adapter: PCI adapter
Composite:    +38.9°C  (low  =  -0.1°C, high = +74.8°C)
                       (crit = +79.8°C)


p-i@pi-tuf-b550m-wifi:~$
``` 
On the linux 5.10  kernel you always get k10temp and some more.
To get all senors on my motherbord I have to edit  /etc/default/grub and add "acpi_enforce_resources=lax"
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax"


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```
I have also to create the config file:/etc/modules-load.d/nct6775.conf with the content 
nct6775
This is to tell systemd to do the same as sudo modprobe -v nct6775

---

### Post by bsquare on 2021-02-03
I didn't know the `inxi` command which seems very nice; this is my output:
```
System:    Kernel: 5.8.0-41-generic x86_64 bits: 64 Desktop: Gnome 3.36.4 Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASUSTeK model: TUF GAMING X570-PLUS (WI-FI) v: Rev X.0x serial: <filter> 
           UEFI: American Megatrends v: 3402 date: 01/13/2021 
Battery:   ID-1: hidpp_battery_0 charge: N/A condition: N/A 
CPU:       Topology: 16-Core model: AMD Ryzen 9 5950X bits: 64 type: MT MCP L2 cache: 8192 KiB 
           Speed: 2193 MHz min/max: 2200/3400 MHz Core speeds (MHz): 1: 2199 2: 2200 3: 2235 4: 2234 5: 2236 6: 2229 7: 2237 
           8: 2238 9: 2192 10: 2200 11: 2172 12: 2194 13: 2196 14: 2191 15: 2190 16: 2191 17: 2200 18: 2788 19: 2238 20: 2238 
           21: 2239 22: 2235 23: 2237 24: 2199 25: 2236 26: 2239 27: 2200 28: 2196 29: 2195 30: 2186 31: 2795 32: 2223 
Graphics:  Device-1: NVIDIA TU106 [GeForce RTX 2060 SUPER] driver: nvidia v: 450.102.04 
           Display: x11 server: X.Org 1.20.9 driver: nvidia unloaded: fbdev,modesetting,nouveau,vesa tty: N/A 
           OpenGL: renderer: GeForce RTX 2060 SUPER/PCIe/SSE2 v: 4.6.0 NVIDIA 450.102.04 
Audio:     Device-1: NVIDIA TU106 High Definition Audio driver: snd_hda_intel 
           Device-2: Advanced Micro Devices [AMD] Starship/Matisse HD Audio driver: snd_hda_intel 
           Device-3: Realtek Full HD webcam type: USB driver: snd-usb-audio,uvcvideo 
           Sound Server: ALSA v: k5.8.0-41-generic 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169 
           IF: enp4s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 1.38 TiB used: 355.28 GiB (25.1%) 
           ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 970 PRO 1TB size: 953.87 GiB 
           ID-2: /dev/sda vendor: Kingston model: SHSS37A240G size: 223.57 GiB 
           ID-3: /dev/sdb vendor: Samsung model: SSD 850 PRO 256GB size: 238.47 GiB 
Partition: ID-1: / size: 914.76 GiB used: 254.61 GiB (27.8%) fs: ext4 dev: /dev/dm-0 
           ID-2: swap-1 size: 976.0 MiB used: 0 KiB (0.0%) fs: swap dev: /dev/dm-1 
Sensors:   System Temperatures: cpu: 0.0 C mobo: N/A gpu: nvidia temp: 52 C 
           Fan Speeds (RPM): N/A gpu: nvidia fan: 0% 
Info:      Processes: 552 Uptime: 5h 38m Memory: 31.34 GiB used: 10.36 GiB (33.1%) Shell: bash inxi: 3.0.38 

```

This is my very poor `sensors` output (of course after a complete detect):
```
nvme-pci-0100
Adapter: PCI adapter
Composite:    +42.9°C  (low  = -273.1°C, high = +80.8°C)
                       (crit = +80.8°C)
Sensor 1:     +42.9°C  (low  = -273.1°C, high = +65261.8°C)
Sensor 2:     +49.9°C  (low  = -273.1°C, high = +65261.8°C)

hidpp_battery_0-hid-3-8
Adapter: HID adapter
in0:           3.99 V  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +0.0°C  (high = +70.0°C)
```

The sensors-detect already update my /etc/modules file with:
```
nct6775
```

I guess it is equivalent to yours, acting lsmod confirms nct6775 is loaded.

I'm very excited about the `"acpi_enforce_resources=lax"` option I do not know; I guess it should work with my Asus MB too? ^^

---

### Post by P-I H on 2021-02-03
Try it I suppose it will work, if not it's easy to change. After a change of /etc/default/grub you have to run sudo update-grub and reboot.
When you use Ubuntu with Gnome, you may also use a gnome extension called vitals. Vitals presents fan speeds, cpu frequency, temps and more in the panel. You select what you want to see.
You may have to run sudo modprobe -v nct6775.
In case you don't want to try the development version of Ubuntu, you may present temps of CPUTIN or SYSTIN. They don't provide the same value as k10temp. These are the values I have right now.
```
p-i@pi-tuf-b550m-wifi:~$ sensors
amdgpu-pci-0a00
Adapter: PCI adapter
vddgfx:      775.00 mV 
fan1:           0 RPM  (min =    0 RPM, max = 2970 RPM)
edge:         +39.0°C  (crit = +100.0°C, hyst = -273.1°C)
                       (emerg = +105.0°C)
junction:     +39.0°C  (crit = +110.0°C, hyst = -273.1°C)
                       (emerg = +115.0°C)
mem:          +42.0°C  (crit = +105.0°C, hyst = -273.1°C)
                       (emerg = +110.0°C)
power1:        9.00 W  (cap = 180.00 W)


nct6798-isa-0290
Adapter: ISA adapter
in0:                      288.00 mV (min =  +0.00 V, max =  +1.74 V)
in1:                      1000.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in2:                        3.41 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in3:                        3.30 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in4:                        1.02 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:                      776.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in6:                      224.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in7:                        3.41 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in8:                        3.36 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in9:                      912.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in10:                     384.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in11:                     384.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in12:                       1.03 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in13:                     992.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in14:                       1.01 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
fan1:                      845 RPM  (min =    0 RPM)
fan2:                      858 RPM  (min =    0 RPM)
fan3:                      806 RPM  (min =    0 RPM)
fan7:                        0 RPM  (min =    0 RPM)
SYSTIN:                    +38.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
CPUTIN:                    +30.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
AUXTIN0:                   +88.5°C    sensor = thermistor
AUXTIN1:                   +38.0°C    sensor = thermistor
AUXTIN2:                   +38.0°C    sensor = thermistor
AUXTIN3:                   +25.0°C    sensor = thermistor
PECI Agent 0 Calibration:  +30.5°C  
PCH_CHIP_CPU_MAX_TEMP:      +0.0°C  
PCH_CHIP_TEMP:              +0.0°C  
PCH_CPU_TEMP:               +0.0°C  
intrusion0:               ALARM
intrusion1:               ALARM
beep_enable:              disabled


nvme-pci-0500
Adapter: PCI adapter
Composite:    +33.9°C  (low  =  -0.1°C, high = +74.8°C)
                       (crit = +79.8°C)


iwlwifi_1-virtual-0
Adapter: Virtual device
temp1:        +30.0°C  


k10temp-pci-00c3
Adapter: PCI adapter
Tctl:         +34.5°C  
Tdie:         +34.5°C  


nvme-pci-0100
Adapter: PCI adapter
Composite:    +32.9°C  (low  = -273.1°C, high = +84.8°C)
                       (crit = +84.8°C)
Sensor 1:     +32.9°C  (low  = -273.1°C, high = +65261.8°C)
Sensor 2:     +37.9°C  (low  = -273.1°C, high = +65261.8°C)


p-i@pi-tuf-b550m-wifi:~$
```

---

### Post by bsquare on 2021-02-03
Many many thanks!

It is just a great success:
[HTML]hidpp_battery_0-hid-3-8
Adapter: HID adapter
in0:           3.98 V  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +0.0°C  (high = +70.0°C)

nvme-pci-0100
Adapter: PCI adapter
Composite:    +41.9°C  (low  = -273.1°C, high = +80.8°C)
                       (crit = +80.8°C)
Sensor 1:     +41.9°C  (low  = -273.1°C, high = +65261.8°C)
Sensor 2:     +47.9°C  (low  = -273.1°C, high = +65261.8°C)

nct6798-isa-0290
Adapter: ISA adapter
in0:                      936.00 mV (min =  +0.00 V, max =  +1.74 V)
in1:                        1.02 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in2:                        3.41 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in3:                        3.34 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in4:                        1.02 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:                      768.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in6:                        1.02 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in7:                        3.41 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in8:                        3.30 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in9:                      912.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in10:                     240.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in11:                     496.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in12:                       1.03 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in13:                     1000.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in14:                       1.01 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
fan1:                      828 RPM  (min =    0 RPM)
fan2:                      506 RPM  (min =    0 RPM)
fan3:                      784 RPM  (min =    0 RPM)
fan4:                        0 RPM  (min =    0 RPM)
fan5:                     2716 RPM  (min =    0 RPM)
fan6:                        0 RPM  (min =    0 RPM)
fan7:                      604 RPM  (min =    0 RPM)
SYSTIN:                    +38.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
CPUTIN:                    +37.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
AUXTIN0:                   +25.0°C    sensor = thermistor
AUXTIN1:                   +59.0°C    sensor = thermistor
AUXTIN2:                   +26.0°C    sensor = thermistor
AUXTIN3:                   +26.0°C    sensor = thermistor
PECI Agent 0 Calibration:  +37.0°C  
SMBUSMASTER 1:             +67.0°C  
PCH_CHIP_CPU_MAX_TEMP:      +0.0°C  
PCH_CHIP_TEMP:              +0.0°C  
intrusion0:               ALARM
intrusion1:               ALARM
beep_enable:              disabled

[/HTML]

My main issue right now is to understand which sensor correspond to what :D
CPUTIN is supposed to be the "true" CPU Temperature?

I use the **gnome-shell-extension-system-monitor** gnome extension for that, but I'm eager to test Vitals one (but it is not available in official Ubuntu packages).

Nevertheless, I read the `acpi_enforce_resources=lax` option can be risky ... what do you know about that?

---

### Post by P-I H on 2021-02-03
I have used that for some time and haven't seen any problem. The log is also quite empty.
The src/profile......... is related to bluetooth. I get this when I disconnect the headphones.
We were woken up.... is related to pulseaudio.
_common_interrupt... is related to the Ryzen CPU.
None of these are related to any serious problem.

---

### Post by bsquare on 2021-02-03
It is very nice!

I'm testing Vitals, and I find it very interesting :)

Thanks for your answer, I do NOT need any more, and thus I won't take any stability risks trying any other Kernel version & co, before true integration in Ubuntu LTS Release ;)

---

