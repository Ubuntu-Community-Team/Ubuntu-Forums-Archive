---
title: "fn not working asus"
date: 2019-06-18
forum: Hardware
---

### Post by dragon-killer on 2019-06-18
not working fn-keys (not only on ubuntu).
dmesg | grep -i asus
[    0.000000] DMI: ASUSTeK COMPUTER INC. X555LJ/X555LJ, BIOS X555LJ.602 05/06/2016
[    0.009758] ACPI: RSDP 0x000000009368B000 000024 (v02 _ASUS_)
[    0.009761] ACPI: XSDT 0x000000009368B0B8 0000EC (v01 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.009766] ACPI: FACP 0x00000000936A6498 00010C (v05 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.009771] ACPI: DSDT 0x000000009368B240 01B256 (v02 _ASUS_ Notebook 01072009 INTL 20120913)
[    0.009776] ACPI: APIC 0x00000000936A65A8 000084 (v03 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.009778] ACPI: FPDT 0x00000000936A6630 000044 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.009780] ACPI: FIDT 0x00000000936A6678 00009C (v01 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.009783] ACPI: ECDT 0x00000000936A6718 0000C1 (v01 _ASUS_ Notebook 01072009 AMI. 00000005)
[    0.009785] ACPI: MCFG 0x00000000936A67E0 00003C (v01 _ASUS_ Notebook 01072009 MSFT 00000097)
[    0.009787] ACPI: HPET 0x00000000936A6820 000038 (v01 _ASUS_ Notebook 01072009 AMI. 0005000A)
[    0.009829] ACPI: BGRT 0x00000000936B33A8 000038 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
[    3.685619] input: Asus Wireless Radio Control as /devices/LNXSYSTM:00/LNXSYBUS:00/ATK4002:00/input/input17
[    3.994781] asus_wmi: ASUS WMI generic driver loaded
[    3.999097] asus_wmi: Initialization: 0x1
[    3.999178] asus_wmi: BIOS WMI version: 7.9
[    3.999271] asus_wmi: SFUN value: 0xa0077
[    4.010301] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input25
[    4.038235] asus_wmi: Number of fans: 0

---

### Post by TheFu on 2019-06-18
To get help, please be specific about 
a) the hardware
b) the OS used, which release
c) the desktop environment
d) the exact issue(s), assuming they are related

Not sure what the dmesg output is trying to show.

Something like **inxi -Fz** would be much more helpful. Please post using code-tags so the post here looks like it does in a terminal.  Adv Reply (#)   If the info isn't readable, fewer people will try to help.

I have an Asus laptop, but haven't bothered trying to make all the Fn keys work. I suspect Fn keys are hardwired into the BIOS and might not be something any OS can control. [https://askubuntu.com/questions/827925/remapping-the-fn-key](https://askubuntu.com/questions/827925/remapping-the-fn-key) says the same.

---

### Post by dragon-killer on 2019-06-19
Thanks for answer!

```

dragon@killer:~$ inxi -Fz 
System:    Host: killer Kernel: 5.1.11-050111-generic x86_64 bits: 64 Desktop: Gnome 3.32.0 Distro: Ubuntu 19.04 (Disco Dingo) 
Machine:   Type: Laptop System: ASUSTeK product: X555LJ v: 1.0 serial: <filter> 
           Mobo: ASUSTeK model: X555LJ v: 1.0 serial: <filter> UEFI: American Megatrends v: X555LJ.602 date: 05/06/2016 
Battery:   ID-1: BAT0 charge: 17.0 Wh condition: 17.6/37.3 Wh (47%) 
CPU:       Topology: Dual Core model: Intel Core i5-5200U bits: 64 type: MT MCP L2 cache: 3072 KiB 
           Speed: 799 MHz min/max: 500/2700 MHz Core speeds (MHz): 1: 799 2: 799 3: 799 4: 799 
Graphics:  Device-1: Intel HD Graphics 5500 driver: i915 v: kernel 
           Device-2: NVIDIA GK208BM [GeForce 920M] driver: N/A 
           Display: x11 server: X.Org 1.20.4 driver: modesetting,nvidia unloaded: fbdev,nouveau,vesa resolution: 1360x768~60Hz 
           OpenGL: renderer: Mesa DRI Intel HD Graphics 5500 (Broadwell GT2) v: 4.5 Mesa 19.0.2 
Audio:     Device-1: Intel Broadwell-U Audio driver: snd_hda_intel 
           Device-2: Intel Wildcat Point-LP High Definition Audio driver: snd_hda_intel 
           Sound Server: ALSA v: k5.1.11-050111-generic 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169 
           IF: enp2s0 state: down mac: <filter> 
           Device-2: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter driver: ath9k 
           IF: wlp3s0 state: up mac: <filter> 
Drives:    Local Storage: total: 1.14 TiB used: 41.92 GiB (3.6%) 
           ID-1: /dev/sda vendor: Samsung model: SSD 860 EVO 250GB size: 232.89 GiB 
           ID-2: /dev/sdb vendor: Seagate model: ST1000LM024 HN-M101MBB size: 931.51 GiB 
Partition: ID-1: / size: 227.74 GiB used: 41.92 GiB (18.4%) fs: ext4 dev: /dev/sda2 
Sensors:   System Temperatures: cpu: 50.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Info:      Processes: 264 Uptime: 14h 26m Memory: 11.63 GiB used: 2.89 GiB (24.9%) Shell: bash inxi: 3.0.33 


```

also

```

dragon@killer:~$ sudo acpi_listen
^[[15~^[[17~^[[18~^[[24~

```

when i clicked fn+{f5, f6, f7, f12}.

Could be variants except physical damage?

---

### Post by TheFu on 2019-06-19
I tested my Asus laptop and some of the Fn keys work. It is definitely the BIOS handling them.  
Mute, Vol-, Vol+ work.  I don't have an external HDMI connected, so the screen mirroring wasn't tested. I worked on my prior laptops.  
Screen brightness controls DO NOT work through the Fn keys. I've mapped the Super-F5/F6 keys to that. It is important for laptops on battery to turn the brightness down.
The Sleep/Standby mode key works. I don't use it, since just closing the lid does that.  I don't have any issues with it waking. Wired network reconnects.
Airplane-mode hasn't been tested. Suspect it would only work to disable wifi/BT stuff anyways.  The BIOS doesn't know about my USB3 GigE NIC.  Let me start a ping and test it... it had zero impact on the wired ethernet connection. I don't use wifi much, so that test will have to wait.

---

