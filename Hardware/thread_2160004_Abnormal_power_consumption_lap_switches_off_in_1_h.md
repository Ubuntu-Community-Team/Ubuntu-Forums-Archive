---
title: "Abnormal power consumption lap switches off in 1 hour"
date: 2013-07-05
forum: Hardware
---

### Post by 0c00l on 2013-07-05
My laptop consumes abnormal power and it goes off in 60 minutes. Even mint and mate version also does the same. I searched the forums but  couldnt find an answer. The fan is always blowing and no problem with  windows it gives 3 to 4 hours. Please help me on this. My another  notebook is fine. Here are the hardware specs

[INDENT] System:    Host: mint Kernel: 3.8.0-19-generic x86_64 (64 bit, gcc: 4.7.3) Desktop: Gnome Distro: Linux Mint 15 Olivia
Machine:   System: Hewlett-Packard product: HP Pavilion g6 Notebook PC version: 0792100000205610000610100
           Mobo: Hewlett-Packard model: 184A version: 57.35 Bios: Insyde version: F.26 date: 02/21/2013
CPU:        Quad core AMD A8-4500M APU with Radeon HD Graphics (-MCP-) cache:  8192 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm)  bmips: 15171.8 
           Clock Speeds: 1: 1400.00 MHz 2: 1900.00 MHz 3: 1400.00 MHz 4: 1400.00 MHz
Graphics:  Card-1: Advanced Micro Devices [AMD] nee ATI Trinity [Radeon HD 7640G] bus-ID: 00:01.0 
           Card-2: Advanced Micro Devices [AMD] nee ATI Thames XT [Radeon HD 7670M] bus-ID: 01:00.0 
           X.Org: 1.13.3 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1366x768@60.1hz 
           GLX Renderer: Gallium 0.4 on AMD ARUBA GLX Version: 3.0 Mesa 9.1.1 Direct Rendering: Yes
Audio:     Card-1: Advanced Micro Devices [AMD] FCH Azalia Controller driver: snd_hda_intel bus-ID: 00:14.2
           Card-2: Advanced Micro Devices [AMD] nee ATI Trinity HDMI Audio Controller driver: snd_hda_intel bus-ID: 00:01.1
           Sound: Advanced Linux Sound Architecture ver: k3.8.0-19-generic
Network:   Card-1: Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
           driver: r8169 ver: 2.3LK-NAPI port: 2000 bus-ID: 05:00.0
           IF: eth0 state: down mac: <filter>
           Card-2: Atheros AR9485 Wireless Network Adapter driver: ath9k bus-ID: 02:00.0
           IF: wlan0 state: down mac: <filter>
           Card-3: Atheros usb-ID: 0cf3:311d
           IF: N/A state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: 508.2GB (0.2% used) 1: USB id: /dev/sda model: Transcend_8GB size: 8.1GB temp: 0C 
           2: id: /dev/sdb model: Hitachi_HTS54755 size: 500.1GB temp: 0C 
Partition: ID: / size: 1.7G used: 52M (4%) fs: overlayfs 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 63.8C mobo: N/A gpu: 65.5 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 173 Uptime: 6 min Memory: 411.5/3363.1MB Runlevel: 2 Gcc sys: 4.7.3 Client: Shell inxi: 1.8.4  
[/INDENT]
and I also used tlp stats its of no use tlp 


[INDENT]--- TLP 0.3.9 --------------------------------------------

+++ Configured Settings: /etc/default/tlp
TLP_ENABLE=1
DISK_IDLE_SECS_ON_AC=0
DISK_IDLE_SECS_ON_BAT=2
MAX_LOST_WORK_SECS_ON_AC=15
MAX_LOST_WORK_SECS_ON_BAT=60
SCHED_POWERSAVE_ON_AC=0
SCHED_POWERSAVE_ON_BAT=1
NMI_WATCHDOG=0
DISK_DEVICES="sda sdb"
DISK_APM_LEVEL_ON_AC="254 254"
DISK_APM_LEVEL_ON_BAT="128 128"
SATA_LINKPWR_ON_AC=max_performance
SATA_LINKPWR_ON_BAT=min_power
PCIE_ASPM_ON_AC=performance
PCIE_ASPM_ON_BAT=powersave
RADEON_POWER_PROFILE_ON_AC=high
RADEON_POWER_PROFILE_ON_BAT=low
WIFI_PWR_ON_AC=1
WIFI_PWR_ON_BAT=5
WOL_DISABLE=Y
SOUND_POWER_SAVE=1
SOUND_POWER_SAVE_CONTROLLER=Y
BAY_POWEROFF_ON_BAT=0
BAY_DEVICE="sr0"
RUNTIME_PM_ON_AC=on
RUNTIME_PM_ON_BAT=auto
RUNTIME_PM_ALL=0
USB_AUTOSUSPEND=1
RESTORE_DEVICE_STATE_ON_STARTUP=0

+++ System Info
System         = Hewlett-Packard 0792100000205610000610100 HP Pavilion g6 Notebook PC
BIOS           = F.26
Release        = Linux Mint 15 Olivia
Kernel         = 3.8.0-19-generic x86_64
/proc/cmdline   = noprompt cdrom-detect/try-usb=true persistent  file=/cdrom/preseed/mint.seed boot=casper initrd=/casper/initrd.lz quiet  splash -- BOOT_IMAGE=/casper/vmlinuz 

+++ System Status
TLP power save = enabled
power source   = battery

+++ Processor
CPU Model      = AMD A8-4500M APU with Radeon(tm) HD Graphics

/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor  = ondemand
/sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq  =  1400000 [kHz]
/sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq  =  1900000 [kHz]
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies = 1900000 1800000 1700000 1600000 1400000 [kHz]

/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor  = ondemand
/sys/devices/system/cpu/cpu1/cpufreq/scaling_min_freq  =  1400000 [kHz]
/sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq  =  1900000 [kHz]
/sys/devices/system/cpu/cpu1/cpufreq/scaling_available_frequencies = 1900000 1800000 1700000 1600000 1400000 [kHz]

/sys/devices/system/cpu/cpu2/cpufreq/scaling_governor  = ondemand
/sys/devices/system/cpu/cpu2/cpufreq/scaling_min_freq  =  1400000 [kHz]
/sys/devices/system/cpu/cpu2/cpufreq/scaling_max_freq  =  1900000 [kHz]
/sys/devices/system/cpu/cpu2/cpufreq/scaling_available_frequencies = 1900000 1800000 1700000 1600000 1400000 [kHz]

/sys/devices/system/cpu/cpu3/cpufreq/scaling_governor  = ondemand
/sys/devices/system/cpu/cpu3/cpufreq/scaling_min_freq  =  1400000 [kHz]
/sys/devices/system/cpu/cpu3/cpufreq/scaling_max_freq  =  1900000 [kHz]
/sys/devices/system/cpu/cpu3/cpufreq/scaling_available_frequencies = 1900000 1800000 1700000 1600000 1400000 [kHz]

/sys/devices/system/cpu/cpufreq/boost                  = 1
/proc/sys/kernel/nmi_watchdog                          = 0

+++ Undervolting
PHC kernel not available.

+++ Temperatures
Fan speed              = (not available)

+++ File System
/proc/sys/vm/laptop_mode               =     2
/proc/sys/vm/dirty_writeback_centisecs =  6000
/proc/sys/vm/dirty_expire_centisecs    =  6000
/proc/sys/vm/dirty_ratio               =    60
/proc/sys/vm/dirty_background_ratio    =    40
/proc/sys/fs/xfs/age_buffer_centisecs  = (not available)
/proc/sys/fs/xfs/xfssyncd_centisecs    = (not available)
/proc/sys/fs/xfs/xfsbufd_centisecs     = (not available)

+++ Storage Devices
/dev/sdb:
          Model     = Hitachi HTS547550A9E384                 
          Firmware  = JE3OA50A
          APM Level = 128
          Status    = standby
          scheduler = deadline

        SMART info:
            4 Start_Stop_Count          =      911 
            5 Reallocated_Sector_Ct     =        0 
            9 Power_On_Hours            =     1003 [h]
          190 Airflow_Temperature_Cel   =       38 [°C]
          193 Load_Cycle_Count          =    10055 


+++ SATA Aggressive Link Power Management
/sys/class/scsi_host/host1/link_power_management_policy  = min_power
/sys/class/scsi_host/host2/link_power_management_policy  = min_power

+++ PCIe Active State Power Management
/sys/module/pcie_aspm/parameters/policy = powersave

+++ Radeon Graphics
/sys/class/drm/card0/device/power_method = profile
/sys/class/drm/card0/device/power_profile = low

+++ Wireless
bluetooth = off (software)
wifi      = off (software)
wwan      = none (no device)

wlan0(ath9k): power management = on

+++ Audio
/sys/module/snd_hda_intel/parameters/power_save            = 1
/sys/module/snd_hda_intel/parameters/power_save_controller = Y

+++ Battery Status
/sys/class/power_supply/BAT0/manufacturer                   = Hewlett-Packard
/sys/class/power_supply/BAT0/model_name                     = Primary
/sys/class/power_supply/BAT0/cycle_count                    = (not supported)
/sys/class/power_supply/BAT0/charge_full_design             =   3904 [mAh]
/sys/class/power_supply/BAT0/charge_full                    =   3904 [mAh]
/sys/class/power_supply/BAT0/charge_now                     =   2080 [mAh]
/sys/class/power_supply/BAT0/current_now                    =   3889 [mA]
/sys/class/power_supply/BAT0/status                         = Discharging

+++ Runtime Power Management
/sys/bus/pci/devices/0000:00:00.0/power/control = auto (0x060000 Host bridge)
/sys/bus/pci/devices/0000:00:01.0/power/control = on   (0x030000 VGA compatible controller)
/sys/bus/pci/devices/0000:00:01.1/power/control = auto (0x040300 Audio device)
/sys/bus/pci/devices/0000:00:02.0/power/control = on   (0x060400 PCI bridge)
/sys/bus/pci/devices/0000:00:04.0/power/control = on   (0x060400 PCI bridge)
/sys/bus/pci/devices/0000:00:10.0/power/control = on   (0x0c0330 USB controller)
/sys/bus/pci/devices/0000:00:10.1/power/control = on   (0x0c0330 USB controller)
/sys/bus/pci/devices/0000:00:11.0/power/control = on   (0x010601 SATA controller)
/sys/bus/pci/devices/0000:00:12.0/power/control = on   (0x0c0310 USB controller)
/sys/bus/pci/devices/0000:00:12.2/power/control = on   (0x0c0320 USB controller)
/sys/bus/pci/devices/0000:00:13.0/power/control = on   (0x0c0310 USB controller)
/sys/bus/pci/devices/0000:00:13.2/power/control = on   (0x0c0320 USB controller)
/sys/bus/pci/devices/0000:00:14.0/power/control = on   (0x0c0500 SMBus)
/sys/bus/pci/devices/0000:00:14.2/power/control = auto (0x040300 Audio device)
/sys/bus/pci/devices/0000:00:14.3/power/control = on   (0x060100 ISA bridge)
/sys/bus/pci/devices/0000:00:14.4/power/control = on   (0x060401 PCI bridge)
/sys/bus/pci/devices/0000:00:15.0/power/control = on   (0x060400 PCI bridge)
/sys/bus/pci/devices/0000:00:15.1/power/control = on   (0x060400 PCI bridge)
/sys/bus/pci/devices/0000:00:18.0/power/control = auto (0x060000 Host bridge)
/sys/bus/pci/devices/0000:00:18.1/power/control = auto (0x060000 Host bridge)
/sys/bus/pci/devices/0000:00:18.2/power/control = auto (0x060000 Host bridge)
/sys/bus/pci/devices/0000:00:18.3/power/control = auto (0x060000 Host bridge)
/sys/bus/pci/devices/0000:00:18.4/power/control = auto (0x060000 Host bridge)
/sys/bus/pci/devices/0000:00:18.5/power/control = auto (0x060000 Host bridge)
/sys/bus/pci/devices/0000:01:00.0/power/control = on   (0x030000 VGA compatible controller)
/sys/bus/pci/devices/0000:02:00.0/power/control = auto (0x028000 Network controller)
/sys/bus/pci/devices/0000:04:00.0/power/control = on   (0xff0000 Unassigned class [ff00])
/sys/bus/pci/devices/0000:05:00.0/power/control = auto (0x020000 Ethernet controller)

+++ USB
tlp usb autosuspend = enabled
tlp usb blacklist   = (not configured)

Bus 001 Device 002 ID 8564:1000 control = auto, autosuspend_delay_ms =  2000 -- <unknown> (usb-storage)
Bus 001 Device 003 ID 064e:e289 control = auto, autosuspend_delay_ms =  2000 -- Suyin Corp.  (uvcvideo)
Bus 004 Device 002 ID 0cf3:311d control = auto, autosuspend_delay_ms =  2000 -- Atheros Communications, Inc.  (btusb)
Bus 005 Device 003 ID 04e8:6863 control = auto, autosuspend_delay_ms =  2000 -- Samsung Electronics Co., Ltd  (rndis_host)
Bus 001 Device 001 ID 1d6b:0002 control = auto, autosuspend_delay_ms =  2000 -- Linux Foundation 2.0 root hub (hub)
Bus 002 Device 001 ID 1d6b:0002 control = auto, autosuspend_delay_ms =  2000 -- Linux Foundation 2.0 root hub (hub)
Bus 003 Device 001 ID 1d6b:0001 control = auto, autosuspend_delay_ms =  2000 -- Linux Foundation 1.1 root hub (hub)
Bus 004 Device 001 ID 1d6b:0001 control = auto, autosuspend_delay_ms =  2000 -- Linux Foundation 1.1 root hub (hub)
Bus 005 Device 001 ID 1d6b:0002 control = auto, autosuspend_delay_ms =  2000 -- Linux Foundation 2.0 root hub (hub)
Bus 006 Device 001 ID 1d6b:0003 control = auto, autosuspend_delay_ms =  2000 -- Linux Foundation 3.0 root hub (hub)
Bus 007 Device 001 ID 1d6b:0002 control = auto, autosuspend_delay_ms =  2000 -- Linux Foundation 2.0 root hub (hub)
Bus 008 Device 001 ID 1d6b:0003 control = auto, autosuspend_delay_ms =  2000 -- Linux Foundation 3.0 root hub (hub)

[/INDENT]
I am a new bee please help me soon and get my ubuntu be good..

---

### Post by dino99 on 2013-07-05
is the "ondemand" working ? or is it up locked ?

try with that option : acpi_osi=linux

> sudo gedit /etc/default/grub
GRUB_CMDLINE_LINUX="acpi_osi=linux"

then update grub:
> sudo update-grub

close your apps, and reboot:
> sudo shutdown -h now

---

### Post by 0c00l on 2013-07-08
> **dino99 said:**
> is the "ondemand" working ? or is it up locked ?

try with that option : acpi_osi=linux


GRUB_CMDLINE_LINUX="acpi_osi=linux"

then update grub:


close your apps, and reboot:

It got ok. Driver was the problem due to dual gpu of AMD. So I changed the driver from driver manager to fgrlx and then after reboot it is fine and good.

---

