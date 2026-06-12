---
title: "Looking to build an NVR/VMS and need advice on selected hardware compatability"
date: 2020-08-12
forum: Hardware
---

### Post by usersystem10 on 2020-08-12
Hi,

I am looking to build an NVR/VMS Server with Ubuntu and have selected the required components, although I have not yet found a clear definition if they will work with Ubuntu.

The hardware specs for the intended system are:

**CPU:** AMD Ryzen 5 2600 3.4GHz 6 Core (Socket AM4)
**Motherboard:** Asus TUF B450-PLUS GAMING
**Possible Alternative Motherboard:** ASUS ROG STRIX B450-F GAMING
**RAM:** 2x Corsair Vengeance LPX 4GB (1x 4GB) 2400MHz DDR4 CL16
**OS Drive:** Crucial MX500 250 GB
**Footage HDD:** Seagate skyhawk hdd 1tb
**PSU:** Corsair RM550x
**Graphics:** Asus GeForce GT 710 1GB GDDR5
**NIC:** Intel PRO/1000 CT pci e EXPI9301CTBLK

The NVR/VMS software I am looking to use is [Nx Witness]("https://www.networkoptix.com/nx-witness/") from NetworkOptix which [states]("https://support.networkoptix.com/hc/en-us/articles/205313168-Nx-Witness-Operating-System-Support") it works with Ubuntu 18.04 and should work with 20.04

A [Linux Status Report PDF]("https://www.asus.com/websites/global/aboutASUS/OS/Linux-Status-report_201904.pdf") on the ASUS website says the TUF B450-PLUS GAMING works with Ubuntu 18.04 however does not say to what extent and the ROG STRIX B450-F GAMING only says it’s suppose to work with Fedora 28.

When looking for compatibility of The CPU I noticed people said to stay away from the ones with integrated graphics so this chip should be ok in that regard.

I did notice on [this post]("https://community.amd.com/thread/244175") there seems to be a problem with AMD’s Ryzen AGESA or at least AGESA Combo-AM4 1.0.0.1 although I don’t know which version the board will come with. However Asus now offers AGESA 1.0.0.6 which might solve problems. It will be nice if the board is able to take the CPU with out updating the UEFI as the general consensus seems to be don't touch it unless you have to. Plus it seems the update process might need an older spec CPU to do this as well.

If it helps anyone else needing an older CPU just to update the UEFI it seems that AMD will loan a CPU for this purpose. The link for this option is: [https://www.amd.com/en/support/kb/faq/pa-100](https://www.amd.com/en/support/kb/faq/pa-100)

Does anyone have any experience with or know if these components are compatible with ubuntu 18.04 LTS and 20.04 LTS?

---

### Post by TheFu on 2020-08-12
I have a ASUS ROG STRIX B450-F GAMING running 16.04. Once I got the memory timings via xmp correct - had to OC to get the 3200Mhz - it has been rock solid.  Also, it has an onboard intel i211 NIC - well supported.  Can't imagine any reason it won't work w/ newer versions or really any linux.  It isn't like this is an HP system.

Also running a ryzen 2600 here.  No issues with that cpu on that MB as shipped.  Be certain to update the bios. Asus has an internet bios update capability.  Here's that system:
```
$ inxi -Fz
System:    Host: hadar Kernel: 4.15.0-112-generic x86_64 (64 bit) Desktop: N/A
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASUSTeK model: **ROG STRIX B450-F GAMING** v: Rev 1.xx
           Bios: American Megatrends v: 2801 date: 09/18/2019
CPU:       Hexa core AMD **Ryzen 5 2600** Six-Core (-HT-MCP-) cache: 3072 KB 
           clock speeds: max: 3400 MHz 1: 1466 MHz 2: 1394 MHz 3: 3229 MHz
           4: 1574 MHz 5: 3892 MHz 6: 1556 MHz 7: 1283 MHz 8: 1276 MHz
           9: 3331 MHz 10: 1953 MHz 11: 3884 MHz 12: 1556 MHz
Graphics:  Card: NVIDIA GP108 [GeForce GT 1030]
           Display Server: X.Org 1.19.6 driver: nvidia
           Resolution: 1920x1200@60.01hz
           GLX Renderer: N/A GLX Version: N/A
Audio:     Card-1 Advanced Micro Devices [AMD] Family 17h (Models 00h-0fh) HD Audio Controller
           driver: snd_hda_intel
           Card-2 NVIDIA GP108 High Definition Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-112-generic
Network:   Card: [B]Intel I211 Gigabit Network Connection driver: igb
[/B]           IF: enp3s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1262.3GB (45.4% used)
           ID-1: /dev/sda model: Hitachi_HDP72505 size: 500.1GB
           ID-2: /dev/sdb model: **Micron_1100_MTFD** size: 512.1GB
           ID-3: USB /dev/sdd model: 00AAKX size: 250.1GB
Partition: ID-1: / size: 22G used: 12G (56%) fs: ext4 dev: /dev/dm-0
           ID-2: /boot size: 720M used: 256M (38%) fs: ext2 dev: /dev/sdb1
           ID-3: swap-1 size: 4.57GB used: 2.21GB (48%) fs: swap dev: /dev/dm-1
RAID:      Device-1: /dev/md127 - inactive components: online: none spare: sdc2
Sensors:   System Temperatures: cpu: 46.4C mobo: N/A
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 561 **Uptime: 17 days** Memory: 17232.3/32160.7MB
           Client: Shell (bash) inxi: 2.2.35
```
Rock solid.

As for the purpose you intend, IDK.  Mine runs 10 virtual machines and trancodes videos most days, easily. Ryzen 2600 is a beast, with sufficient, fast, RAM.

---

### Post by usersystem10 on 2020-08-20
Thanks Fu for the details on the system it's most appreciated and good to know the main components work well with Ubuntu. I'll have to order the parts and give it a go. :)

---

