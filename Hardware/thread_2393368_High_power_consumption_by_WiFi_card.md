---
title: "High power consumption by WiFi card"
date: 2018-06-02
forum: Hardware
---

### Post by mick.lynch on 2018-06-02
I'm running a clean install of Ubuntu 18.04 on a Xiaomi Air 13 2017. Since my fresh install, I'm having issues with high power consumption by my wifi card.

The output from ```
lspci | grep -i wireless
``` is
```

02:00.0 Network controller: Intel Corporation Wireless 8265 / 8275 (rev 78)

```

When I run ```
modinfo iwlwifi
```, I get:
```

filename:       /lib/modules/4.15.0-22-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
<snip>

```

When I run powertop, WiFi is the top consumer of power:
```

The battery reports a discharge rate of 12.4 W
The power consumed was 250 J
The estimated remaining time is 1 hours, 28 minutes


Summary: 783.8 wakeups/second,  0.0 GPU ops/seconds, 0.0 VFS ops/sec and 8.8% CPU use


Power est.              Usage       Events/s    Category       Description
  6.17 W      0.8 pkts/s                Device         Network interface: wlp2s0 (iwlwifi)
  2.08 W     15.0%                      Device         Display backlight
  591 mW      0.7 ms/s     140.1        Interrupt      [17] idma64.1
  399 mW     11.4 ms/s      87.8        Process        [PID 2266] /opt/google/chrome/chrome
  325 mW     22.8 ms/s      59.6        Process        [PID 1818] /usr/bin/gnome-shell
  266 mW      7.6 ms/s      60.0        Process        [PID 2851] /opt/google/chrome/chrome --type=renderer --field-trial-handle=16265
  236 mW      1.3 ms/s      55.6        Timer          tick_sched_timer



```

I've been on the search for a solution for the past few months..but no joy. In the end, I've booted into Windows 10 if I'm not coding and need to conserve battery.

Any tips would be greatly appreciated.

---

### Post by mick.lynch on 2018-06-04
There is something that I've just noticed on Powertop...when I go to the Tunables tab, I get the following list:
```

PowerTOP v2.9     Overview   Idle stats   Frequency stats   Device stats   Tunables     


   Good          Enable SATA link power management for host0
   Good          Enable SATA link power management for host1
   Good          VM writeback timeout
   Good          Enable Audio codec power management
   Good          NMI watchdog should be turned off
   Good          Bluetooth device interface status
   Good          Runtime PM for I2C Adapter i2c-10 (nvkm-0000:01:00.0-aux-0004)
   Good          Runtime PM for I2C Adapter i2c-9 (nvkm-0000:01:00.0-bus-0004)
   Good          Runtime PM for I2C Adapter i2c-12 (nvkm-0000:01:00.0-aux-0005)
   Good          Runtime PM for I2C Adapter i2c-8 (nvkm-0000:01:00.0-bus-0002)
   Good          Autosuspend for USB device XiaoMi USB 2.0 Webcam [Chicony]
   Good          Runtime PM for I2C Adapter i2c-7 (nvkm-0000:01:00.0-bus-0001)
   Good          I2C Device i2c-ELAN2301:00 has no runtime power management
   Good          Runtime PM for I2C Adapter i2c-0 (i915 gmbus dpc)
   Good          Runtime PM for I2C Adapter i2c-1 (i915 gmbus dpb)
   Good          Runtime PM for I2C Adapter i2c-11 (nvkm-0000:01:00.0-bus-0005)
   Good          Autosuspend for USB device xHCI Host Controller [usb2]
   Good          Runtime PM for I2C Adapter i2c-6 (Synopsys DesignWare I2C adapter)
   Good          Autosuspend for USB device ELAN:Fingerprint [ELAN]
   Good          Autosuspend for USB device xHCI Host Controller [usb1]
   Good          Autosuspend for unknown USB device 1-7 (8087:0a2b)
   Good          Runtime PM for I2C Adapter i2c-5 (Synopsys DesignWare I2C adapter)
   Good          Runtime PM for I2C Adapter i2c-2 (i915 gmbus dpd)
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0
   Good          Runtime PM for PCI Device NVIDIA Corporation Device 1d12
   Good          Runtime PM for PCI Device Intel Corporation HD Graphics 620
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP HD Audio
   Good          Runtime PM for PCI Device Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP PCI Express Root Port #9
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP PCI Express Root Port #5
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode]
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP SMBus
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP CSME HECI #1
   Good          Runtime PM for PCI Device Intel Corporation Wireless 8265 / 8275
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP LPC Controller
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP PCI Express Root Port
   Good          Runtime PM for PCI Device Samsung Electronics Co Ltd NVMe SSD Controller SM961/PM961
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP PMC
>> Good          Wake-on-lan status for device wlp2s0                                                                   



```

Looks good. However, when I click on the 'Wake-on-lan status for device wlp2s0' I get a '>> null' just under the Powertop menu:
```

PowerTOP v2.9     Overview   Idle stats   Frequency stats   Device stats   Tunables                                     
>> (null)


   Good          Enable SATA link power management for host0
   Good          Enable SATA link power management for host1
   Good          VM writeback timeout
   Good          Enable Audio codec power management
   Good          NMI watchdog should be turned off
   Good          Bluetooth device interface status
   Good          Runtime PM for I2C Adapter i2c-10 (nvkm-0000:01:00.0-aux-0004)
   Good          Runtime PM for I2C Adapter i2c-9 (nvkm-0000:01:00.0-bus-0004)
   Good          Runtime PM for I2C Adapter i2c-12 (nvkm-0000:01:00.0-aux-0005)
   Good          Runtime PM for I2C Adapter i2c-8 (nvkm-0000:01:00.0-bus-0002)
   Good          Autosuspend for USB device XiaoMi USB 2.0 Webcam [Chicony]
   Good          Runtime PM for I2C Adapter i2c-7 (nvkm-0000:01:00.0-bus-0001)
   Good          I2C Device i2c-ELAN2301:00 has no runtime power management
   Good          Runtime PM for I2C Adapter i2c-0 (i915 gmbus dpc)
   Good          Runtime PM for I2C Adapter i2c-1 (i915 gmbus dpb)
   Good          Runtime PM for I2C Adapter i2c-11 (nvkm-0000:01:00.0-bus-0005)
   Good          Autosuspend for USB device xHCI Host Controller [usb2]
   Good          Runtime PM for I2C Adapter i2c-6 (Synopsys DesignWare I2C adapter)
   Good          Autosuspend for USB device ELAN:Fingerprint [ELAN]
   Good          Autosuspend for USB device xHCI Host Controller [usb1]
   Good          Autosuspend for unknown USB device 1-7 (8087:0a2b)
   Good          Runtime PM for I2C Adapter i2c-5 (Synopsys DesignWare I2C adapter)
   Good          Runtime PM for I2C Adapter i2c-2 (i915 gmbus dpd)
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0
   Good          Runtime PM for PCI Device NVIDIA Corporation Device 1d12
   Good          Runtime PM for PCI Device Intel Corporation HD Graphics 620
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP HD Audio
   Good          Runtime PM for PCI Device Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP PCI Express Root Port #9
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP PCI Express Root Port #5
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode]
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP SMBus
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP CSME HECI #1
   Good          Runtime PM for PCI Device Intel Corporation Wireless 8265 / 8275
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP LPC Controller
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP PCI Express Root Port
   Good          Runtime PM for PCI Device Samsung Electronics Co Ltd NVMe SSD Controller SM961/PM961
   Good          Runtime PM for PCI Device Intel Corporation Sunrise Point-LP PMC
>> Good          Wake-on-lan status for device wlp2s0                                                                   



```

To me, this might mean that it is trying to change something that doesn't exist. 

I'm also running TLP and it doesn't seem to have an issue.

My TLP output is:
```

--- TLP 1.1 --------------------------------------------


+++ Configured Settings: /etc/default/tlp
TLP_ENABLE=1
TLP_DEFAULT_MODE=BAT
TLP_PERSISTENT_DEFAULT=0
DISK_IDLE_SECS_ON_AC=0
DISK_IDLE_SECS_ON_BAT=2
MAX_LOST_WORK_SECS_ON_AC=15
MAX_LOST_WORK_SECS_ON_BAT=60
CPU_HWP_ON_AC=balance_performance
CPU_HWP_ON_BAT=power
SCHED_POWERSAVE_ON_AC=0
SCHED_POWERSAVE_ON_BAT=1
NMI_WATCHDOG=0
ENERGY_PERF_POLICY_ON_AC=performance
ENERGY_PERF_POLICY_ON_BAT=power
DISK_DEVICES="sda sdb"
DISK_APM_LEVEL_ON_AC="254 254"
DISK_APM_LEVEL_ON_BAT="128 128"
SATA_LINKPWR_ON_AC="med_power_with_dipm max_performance"
SATA_LINKPWR_ON_BAT="med_power_with_dipm min_power"
AHCI_RUNTIME_PM_TIMEOUT=15
PCIE_ASPM_ON_AC=performance
PCIE_ASPM_ON_BAT=powersave
RADEON_POWER_PROFILE_ON_AC=high
RADEON_POWER_PROFILE_ON_BAT=low
RADEON_DPM_STATE_ON_AC=performance
RADEON_DPM_STATE_ON_BAT=battery
RADEON_DPM_PERF_LEVEL_ON_AC=auto
RADEON_DPM_PERF_LEVEL_ON_BAT=auto
WIFI_PWR_ON_AC=off
WIFI_PWR_ON_BAT=on
WOL_DISABLE=Y
SOUND_POWER_SAVE_ON_AC=0
SOUND_POWER_SAVE_ON_BAT=1
SOUND_POWER_SAVE_CONTROLLER=Y
BAY_POWEROFF_ON_AC=0
BAY_POWEROFF_ON_BAT=0
BAY_DEVICE="sr0"
RUNTIME_PM_ON_AC=on
RUNTIME_PM_ON_BAT=auto
USB_AUTOSUSPEND=1
USB_BLACKLIST_BTUSB=0
USB_BLACKLIST_PHONE=0
USB_BLACKLIST_PRINTER=1
USB_BLACKLIST_WWAN=1
RESTORE_DEVICE_STATE_ON_STARTUP=1


+++ System Info
System         = Timi XMAKB3M0P0304 TM1604
BIOS           = XMAKB3M0P0304
Release        = Ubuntu 18.04 LTS
Kernel         = 4.15.0-22-generic #24-Ubuntu SMP Wed May 16 12:15:17 UTC 2018 x86_64
/proc/cmdline  = BOOT_IMAGE=/boot/vmlinuz-4.15.0-22-generic root=UUID=76f73454-29be-4ae0-8fbc-bc2542d2d241 ro quiet splash nouveau.runpm=0 vt.handoff=1
Init system    = systemd v237
Boot mode      = UEFI


+++ TLP Status
State          = enabled
Last run       = 06:04:50 PM,   2503 sec(s) ago
Mode           = battery
Power source   = battery


+++ Processor
CPU model      = Intel(R) Core(TM) i5-7200U CPU @ 2.50GHz


/sys/devices/system/cpu/cpu0/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors = performance powersave
/sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq  =   400000 [kHz]
/sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq  =  3100000 [kHz]
/sys/devices/system/cpu/cpu0/cpufreq/energy_performance_preference = power
/sys/devices/system/cpu/cpu0/cpufreq/energy_performance_available_preferences = default performance balance_performance balance_power power 


/sys/devices/system/cpu/cpu1/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu1/cpufreq/scaling_available_governors = performance powersave
/sys/devices/system/cpu/cpu1/cpufreq/scaling_min_freq  =   400000 [kHz]
/sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq  =  3100000 [kHz]
/sys/devices/system/cpu/cpu1/cpufreq/energy_performance_preference = power
/sys/devices/system/cpu/cpu1/cpufreq/energy_performance_available_preferences = default performance balance_performance balance_power power 


/sys/devices/system/cpu/cpu2/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu2/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu2/cpufreq/scaling_available_governors = performance powersave
/sys/devices/system/cpu/cpu2/cpufreq/scaling_min_freq  =   400000 [kHz]
/sys/devices/system/cpu/cpu2/cpufreq/scaling_max_freq  =  3100000 [kHz]
/sys/devices/system/cpu/cpu2/cpufreq/energy_performance_preference = power
/sys/devices/system/cpu/cpu2/cpufreq/energy_performance_available_preferences = default performance balance_performance balance_power power 


/sys/devices/system/cpu/cpu3/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu3/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu3/cpufreq/scaling_available_governors = performance powersave
/sys/devices/system/cpu/cpu3/cpufreq/scaling_min_freq  =   400000 [kHz]
/sys/devices/system/cpu/cpu3/cpufreq/scaling_max_freq  =  3100000 [kHz]
/sys/devices/system/cpu/cpu3/cpufreq/energy_performance_preference = power
/sys/devices/system/cpu/cpu3/cpufreq/energy_performance_available_preferences = default performance balance_performance balance_power power 


/sys/devices/system/cpu/intel_pstate/min_perf_pct      =  12 [%]
/sys/devices/system/cpu/intel_pstate/max_perf_pct      = 100 [%]
/sys/devices/system/cpu/intel_pstate/no_turbo          =   0
/sys/devices/system/cpu/intel_pstate/turbo_pct         =  22 [%]
/sys/devices/system/cpu/intel_pstate/num_pstates       =  28


x86_energy_perf_policy.cpu0                            = power 
x86_energy_perf_policy.cpu0                            = HWP_REQ: min
x86_energy_perf_policy.cpu0                            = HWP_CAP: low
x86_energy_perf_policy.cpu1                            = power 
x86_energy_perf_policy.cpu1                            = HWP_REQ: min
x86_energy_perf_policy.cpu1                            = HWP_CAP: low
x86_energy_perf_policy.cpu2                            = power 
x86_energy_perf_policy.cpu2                            = HWP_REQ: min
x86_energy_perf_policy.cpu2                            = HWP_CAP: low
x86_energy_perf_policy.cpu3                            = power 
x86_energy_perf_policy.cpu3                            = HWP_REQ: min
x86_energy_perf_policy.cpu3                            = HWP_CAP: low


/sys/module/workqueue/parameters/power_efficient       = Y
/proc/sys/kernel/nmi_watchdog                          = 0


+++ Undervolting
PHC kernel not available.


+++ Temperatures
CPU temp               =    49 [°C]
Fan speed              = (not available)


+++ File System
/proc/sys/vm/laptop_mode               =     2
/proc/sys/vm/dirty_writeback_centisecs =  1500
/proc/sys/vm/dirty_expire_centisecs    =  6000
/proc/sys/vm/dirty_ratio               =    20
/proc/sys/vm/dirty_background_ratio    =    10


+++ Storage Devices


+++ AHCI Link Power Management (ALPM)
/sys/class/scsi_host/host0/link_power_management_policy  = min_power
/sys/class/scsi_host/host1/link_power_management_policy  = min_power


+++ AHCI Host Controller Runtime Power Management
/sys/bus/pci/devices/0000:00:17.0/ata1/power/control = on
/sys/bus/pci/devices/0000:00:17.0/ata2/power/control = on


+++ PCIe Active State Power Management
/sys/module/pcie_aspm/parameters/policy = default (using bios preferences)


+++ Intel Graphics
/sys/module/i915/parameters/enable_rc6       =  1 (enabled)
/sys/module/i915/parameters/enable_dc        = -1 (use per-chip default)
/sys/module/i915/parameters/enable_fbc       =  1 (enabled)
/sys/module/i915/parameters/enable_psr       =  0 (disabled)
/sys/module/i915/parameters/modeset          = -1 (use per-chip default)
/sys/module/i915/parameters/semaphores       =  0 (disabled)


+++ Wireless
bluetooth = off (software)
wifi      = on
wwan      = none (no device)


hci0(btusb)                   : bluetooth, not connected
wlp2s0(iwlwifi)               : wifi, connected, power management = on


+++ Audio
/sys/module/snd_hda_intel/parameters/power_save            = 1
/sys/module/snd_hda_intel/parameters/power_save_controller = Y


+++ Runtime Power Management
Device blacklist = (not configured)
Driver blacklist = amdgpu nouveau nvidia radeon (default)


/sys/bus/pci/devices/0000:00:00.0/power/control = auto (0x060000, Host bridge, no driver)
/sys/bus/pci/devices/0000:00:02.0/power/control = auto (0x030000, VGA compatible controller, i915)
/sys/bus/pci/devices/0000:00:14.0/power/control = auto (0x0c0330, USB controller, xhci_hcd)
/sys/bus/pci/devices/0000:00:15.0/power/control = auto (0x118000, Signal processing controller, intel-lpss)
/sys/bus/pci/devices/0000:00:15.1/power/control = auto (0x118000, Signal processing controller, intel-lpss)
/sys/bus/pci/devices/0000:00:16.0/power/control = auto (0x078000, Communication controller, mei_me)
/sys/bus/pci/devices/0000:00:17.0/power/control = auto (0x010601, SATA controller, ahci)
/sys/bus/pci/devices/0000:00:1c.0/power/control = auto (0x060400, PCI bridge, pcieport)
/sys/bus/pci/devices/0000:00:1c.4/power/control = auto (0x060400, PCI bridge, pcieport)
/sys/bus/pci/devices/0000:00:1d.0/power/control = auto (0x060400, PCI bridge, pcieport)
/sys/bus/pci/devices/0000:00:1f.0/power/control = auto (0x060100, ISA bridge, no driver)
/sys/bus/pci/devices/0000:00:1f.2/power/control = auto (0x058000, Memory controller, no driver)
/sys/bus/pci/devices/0000:00:1f.3/power/control = auto (0x040300, Audio device, snd_hda_intel)
/sys/bus/pci/devices/0000:00:1f.4/power/control = auto (0x0c0500, SMBus, no driver)
/sys/bus/pci/devices/0000:01:00.0/power/control = auto (0x030200, 3D controller, nouveau)
/sys/bus/pci/devices/0000:02:00.0/power/control = auto (0x028000, Network controller, iwlwifi)
/sys/bus/pci/devices/0000:03:00.0/power/control = auto (0x010802, Non-Volatile memory controller, nvme)


+++ USB
Autosuspend         = enabled
Device whitelist    = (not configured)
Device blacklist    = (not configured)
Bluetooth blacklist = disabled
Phone blacklist     = disabled
WWAN blacklist      = enabled


Bus 002 Device 001 ID 1d6b:0003 control = auto, autosuspend_delay_ms =     0 -- Linux Foundation 3.0 root hub (hub)
Bus 001 Device 004 ID 8087:0a2b control = auto, autosuspend_delay_ms =  2000 -- Intel Corp.  (btusb)
Bus 001 Device 003 ID 04f3:0c1a control = auto, autosuspend_delay_ms =  2000 -- Elan Microelectronics Corp.  (no driver)
Bus 001 Device 002 ID 04f2:b5a3 control = auto, autosuspend_delay_ms =  2000 -- Chicony Electronics Co., Ltd  (uvcvideo)
Bus 001 Device 001 ID 1d6b:0002 control = auto, autosuspend_delay_ms =     0 -- Linux Foundation 2.0 root hub (hub)


+++ Battery Status
/sys/class/power_supply/BAT0/manufacturer                   = LGC
/sys/class/power_supply/BAT0/model_name                     = R13B02W
/sys/class/power_supply/BAT0/cycle_count                    = (not supported)
/sys/class/power_supply/BAT0/charge_full_design             =   5132 [mAh]
/sys/class/power_supply/BAT0/charge_full                    =   4910 [mAh]
/sys/class/power_supply/BAT0/charge_now                     =   3857 [mAh]
/sys/class/power_supply/BAT0/current_now                    =   1429 [mA]
/sys/class/power_supply/BAT0/status                         = Discharging


Charge                                                      =   78.6 [%]
Capacity                                                    =   95.7 [%]


+++ Suggestions
* Install smartmontools for disk drive health info



```

---

### Post by mick.lynch on 2018-06-04
Hmmmm, sorry for all the posts. Turns out my WiFi might not be the issue after all. 

I toggled my wifi off [FONT=courier new]'wifi toggle' [/FONT]and wifi did not appear as my top power consumer:
```

PowerTOP v2.9     Overview   Idle stats   Frequency stats   Device stats   Tunables                                     


The battery reports a discharge rate of 11.2 W
The power consumed was 228 J
The estimated remaining time is 2 hours, 18 minutes


Summary: 552.1 wakeups/second,  0.0 GPU ops/seconds, 0.0 VFS ops/sec and 14.8% CPU use


Power est.              Usage       Events/s    Category       Description
  3.35 W      5.0%                      Device         Display backlight
  321 mW     20.5 ms/s      78.9        Process        [PID 9092] /opt/google/chrome/chrome
  212 mW     14.3 ms/s      51.6        Process        [PID 9148] /opt/google/chrome/chrome --type=gpu-process --field-trial-handle=12299435127877341279,16471080677723092154,131072 -
  192 mW     21.9 ms/s      42.4        Process        [PID 1621] /usr/bin/gnome-shell
  176 mW      1.3 ms/s      47.8        Timer          tick_sched_timer
  174 mW     11.0 ms/s      42.7        Process        [PID 9227] /opt/google/chrome/chrome --type=renderer --field-trial-handle=12299435127877341279,16471080677723092154,131072 --se
  170 mW     24.8 ms/s      35.0        Process        [PID 9210] /opt/google/chrome/chrome --type=renderer --field-trial-handle=12299435127877341279,16471080677723092154,131072 --se
  130 mW      7.6 ms/s      32.3        Process        [PID 9125] /opt/google/chrome/chrome
  111 mW      4.3 ms/s      28.5        Process        [PID 9218] /opt/google/chrome/chrome --type=renderer --field-trial-handle=12299435127877341279,16471080677723092154,131072 --se
  104 mW    412.1 µs/s      28.4        Process        [PID 8] [rcu_sched]
 90.9 mW      5.0 ms/s      22.7        Process        [PID 1647] ibus-daemon --xim --panel disable
 80.7 mW     11.5 ms/s      16.8        Process        [PID 1489] /usr/lib/xorg/Xorg vt2 -displayfd 3 -auth /run/user/1000/gdm/Xauthority -background none -noreset -keeptty -verbose
 48.1 mW      1.9 ms/s      12.4        Process        [PID 1753] /usr/lib/gnome-settings-daemon/gsd-color
 42.6 mW      3.3 ms/s      10.2        Interrupt      [0] HI_SOFTIRQ
 35.7 mW      1.9 ms/s       8.9        Process        [PID 1853] /usr/lib/ibus/ibus-engine-simple
 35.0 mW     87.9 µs/s       9.6        Timer          intel_uncore_fw_release_timer
 34.0 mW    238.5 µs/s       9.3        Process        [PID 1] /sbin/init splash
 26.9 mW      2.5 ms/s       6.2        Process        [PID 1645] ibus-daemon --xim --panel disable
 23.7 mW      0.7 ms/s       6.2        Interrupt      [128] i915
 22.7 mW      2.1 ms/s       5.3        Process        [PID 9229] /opt/google/chrome/chrome --type=renderer --field-trial-handle=12299435127877341279,16471080677723092154,131072 --se
 20.3 mW    116.6 µs/s       5.5        Process        [PID 195] [i915/signal:0]
 15.5 mW      1.1 ms/s       3.8        Interrupt      [7] sched(softirq)
 14.6 mW      0.8 ms/s       3.6        Process        [PID 1851] /usr/lib/ibus/ibus-engine-simple
 14.6 mW    397.2 µs/s       3.8        Process        [PID 778] /usr/sbin/acpid
 14.1 mW     24.4 µs/s       3.9        kWork          console_callback
 12.4 mW      0.8 ms/s       3.0        Process        [PID 9446] /opt/google/chrome/chrome --type=renderer --field-trial-handle=12299435127877341279,16471080677723092154,131072 --se
 12.1 mW    606.6 µs/s       3.0        Timer          hrtimer_wakeup
 11.6 mW     10.6 µs/s       3.2        kWork          intel_atomic_helper_free_state_
 10.8 mW      0.0 µs/s       3.0        kWork          intel_atomic_commit_work
 10.7 mW      0.2 µs/s       2.9        kWork          intel_fbc_work_fn
 8.06 mW      1.1 ms/s       1.7        Process        [PID 9212] /opt/google/chrome/chrome --type=renderer --field-trial-handle=12299435127877341279,16471080677723092154,131072 --se
 7.77 mW      0.8 ms/s       1.7        Process        [PID 9330] /opt/google/chrome/chrome --type=renderer --field-trial-handle=12299435127877341279,16471080677723092154,131072 --se
 6.94 mW    250.1 µs/s       1.8        Process        [PID 1221] /usr/lib/colord/colord
 4.83 mW    287.9 µs/s       1.2        Process        [PID 635] /lib/systemd/systemd-resolved
 3.79 mW    104.8 µs/s       1.0        Process        [PID 1140] /usr/lib/gnome-settings-daemon/gsd-color
 3.45 mW     11.6 µs/s       0.9        kWork          pci_pme_list_scan
 3.26 mW      4.9 µs/s       0.9        Timer          sched_rt_period_timer
 3.16 mW     49.0 µs/s       0.8        Interrupt      [135] nvkm
 2.46 mW    170.4 µs/s       0.6        Process        [PID 1216] /usr/lib/colord/colord
 2.37 mW     11.3 µs/s       0.6        kWork          vmstat_shepherd
 1.90 mW    263.2 µs/s       0.4        Process        [PID 8741] /usr/lib/gnome-terminal/gnome-terminal-server
 1.81 mW      0.0 µs/s       0.5        kWork          i915_gem_idle_work_handler
 1.49 mW     23.1 µs/s       0.4        kWork          i915_gem_retire_work_handler



``` 

But my power consumption is way higher than it should be.

---

