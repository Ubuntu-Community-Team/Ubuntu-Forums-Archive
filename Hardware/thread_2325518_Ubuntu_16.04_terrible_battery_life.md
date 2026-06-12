---
title: "Ubuntu 16.04 terrible battery life"
date: 2016-05-23
forum: Hardware
---

### Post by ryszard007 on 2016-05-23
Hi!

I own ThinkPad w530 witn Quadro K2000m and i7-3840QM. On Windows on WiFi, Chrome and 50% of brithness I have ~15 W battery consumption. On Ubuntu I can't go lower than 20 W! I was doing everything and no succes. I've installed newest 361 Nvidia drivers, switch to Intel. Nvidia is OFF. Here is my TLP log:

```
--- TLP 0.8 --------------------------------------------

+++ Configured Settings: /etc/default/tlp
TLP_ENABLE=1
TLP_DEFAULT_MODE=AC
DISK_IDLE_SECS_ON_AC=0
DISK_IDLE_SECS_ON_BAT=2
MAX_LOST_WORK_SECS_ON_AC=15
MAX_LOST_WORK_SECS_ON_BAT=120
CPU_SCALING_GOVERNOR_ON_AC=powersave
CPU_SCALING_GOVERNOR_ON_BAT=powersave
CPU_SCALING_MIN_FREQ_ON_BAT=1200000 [kHz]
CPU_SCALING_MAX_FREQ_ON_BAT=1200000 [kHz]
CPU_MIN_PERF_ON_BAT=0
CPU_MAX_PERF_ON_BAT=32
CPU_BOOST_ON_AC=1
CPU_BOOST_ON_BAT=0
SCHED_POWERSAVE_ON_AC=0
SCHED_POWERSAVE_ON_BAT=1
NMI_WATCHDOG=0
ENERGY_PERF_POLICY_ON_AC=performance
ENERGY_PERF_POLICY_ON_BAT=powersave
DISK_DEVICES="sda sdb"
DISK_APM_LEVEL_ON_AC="254 254"
DISK_APM_LEVEL_ON_BAT="127 127"
DISK_SPINDOWN_TIMEOUT_ON_AC="128 0"
DISK_SPINDOWN_TIMEOUT_ON_BAT="128 0"
DISK_IOSCHED="cfq noop"
SATA_LINKPWR_ON_AC=max_performance
SATA_LINKPWR_ON_BAT=min_power
PCIE_ASPM_ON_AC=performance
PCIE_ASPM_ON_BAT=powersave
RADEON_POWER_PROFILE_ON_AC=high
RADEON_POWER_PROFILE_ON_BAT=low
RADEON_DPM_STATE_ON_AC=performance
RADEON_DPM_STATE_ON_BAT=battery
RADEON_DPM_PERF_LEVEL_ON_AC=auto
RADEON_DPM_PERF_LEVEL_ON_BAT=auto
WIFI_PWR_ON_AC=1
WIFI_PWR_ON_BAT=5
WOL_DISABLE=Y
SOUND_POWER_SAVE_ON_AC=0
SOUND_POWER_SAVE_ON_BAT=1
SOUND_POWER_SAVE_CONTROLLER=Y
BAY_POWEROFF_ON_BAT=0
BAY_DEVICE="sr0"
RUNTIME_PM_ON_AC=on
RUNTIME_PM_ON_BAT=auto
RUNTIME_PM_ALL=1
RUNTIME_PM_DRIVER_BLACKLIST="radeon nouveau"
USB_AUTOSUSPEND=1
USB_BLACKLIST_WWAN=0
USB_WHITELIST="0765:5010"
RESTORE_DEVICE_STATE_ON_STARTUP=0
DEVICES_TO_DISABLE_ON_STARTUP="bluetooth wwan"


+++ System Info
System         = LENOVO ThinkPad W530 244754G
BIOS           = G5ETA5WW (2.65 )
Release        = Ubuntu 16.04 LTS
Kernel         = 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 x86_64
/proc/cmdline  = BOOT_IMAGE=/boot/vmlinuz-4.4.0-22-generic.efi.signed root=UUID=a07f8f8e-14ed-46e2-a55d-b0d413a11f97 ro quiet splash pcie_aspm=force acpi=force acpi_enforce_resources=lax acpi_osi=Linux "acpi_osi=!Windows 2012" vt.handoff=7
Init system    = systemd


+++ System Status
TLP power save = enabled
power source   = battery


+++ Processor
CPU Model      = Intel(R) Core(TM) i7-3840QM CPU @ 2.80GHz


/sys/devices/system/cpu/cpu0/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq  =  1200000 [kHz]
/sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq  =  3800000 [kHz]


/sys/devices/system/cpu/cpu1/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu1/cpufreq/scaling_min_freq  =  1200000 [kHz]
/sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq  =  3800000 [kHz]


/sys/devices/system/cpu/cpu2/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu2/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu2/cpufreq/scaling_min_freq  =  1200000 [kHz]
/sys/devices/system/cpu/cpu2/cpufreq/scaling_max_freq  =  3800000 [kHz]


/sys/devices/system/cpu/cpu3/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu3/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu3/cpufreq/scaling_min_freq  =  1200000 [kHz]
/sys/devices/system/cpu/cpu3/cpufreq/scaling_max_freq  =  3800000 [kHz]


/sys/devices/system/cpu/cpu4/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu4/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu4/cpufreq/scaling_min_freq  =  1200000 [kHz]
/sys/devices/system/cpu/cpu4/cpufreq/scaling_max_freq  =  3800000 [kHz]


/sys/devices/system/cpu/cpu5/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu5/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu5/cpufreq/scaling_min_freq  =  1200000 [kHz]
/sys/devices/system/cpu/cpu5/cpufreq/scaling_max_freq  =  3800000 [kHz]


/sys/devices/system/cpu/cpu6/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu6/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu6/cpufreq/scaling_min_freq  =  1200000 [kHz]
/sys/devices/system/cpu/cpu6/cpufreq/scaling_max_freq  =  3800000 [kHz]


/sys/devices/system/cpu/cpu7/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu7/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu7/cpufreq/scaling_min_freq  =  1200000 [kHz]
/sys/devices/system/cpu/cpu7/cpufreq/scaling_max_freq  =  3800000 [kHz]


/sys/devices/system/cpu/intel_pstate/min_perf_pct      = 31
/sys/devices/system/cpu/intel_pstate/max_perf_pct      = 32
/sys/devices/system/cpu/intel_pstate/no_turbo          = 1


x86_energy_perf_policy.cpu0                            = powersave
x86_energy_perf_policy.cpu1                            = powersave
x86_energy_perf_policy.cpu2                            = powersave
x86_energy_perf_policy.cpu3                            = powersave
x86_energy_perf_policy.cpu4                            = powersave
x86_energy_perf_policy.cpu5                            = powersave
x86_energy_perf_policy.cpu6                            = powersave
x86_energy_perf_policy.cpu7                            = powersave


/proc/sys/kernel/nmi_watchdog                          = 0


+++ Undervolting
PHC kernel not available.


+++ Temperatures
CPU temp               =    51 [°C]
/proc/acpi/ibm/fan     =  1973 [/min]


+++ File System
/proc/sys/vm/laptop_mode               =     2
/proc/sys/vm/dirty_writeback_centisecs =  1500
/proc/sys/vm/dirty_expire_centisecs    = 12000
/proc/sys/vm/dirty_ratio               =    20
/proc/sys/vm/dirty_background_ratio    =    10
/proc/sys/fs/xfs/age_buffer_centisecs  = (not available)
/proc/sys/fs/xfs/xfssyncd_centisecs    = (not available)
/proc/sys/fs/xfs/xfsbufd_centisecs     = (not available)


+++ Storage Devices
/dev/sda:
          Model     = HGST HTS725050A7E630                    
          Firmware  = GH2ZB550
          APM Level = 127
          Status    = standby
          Scheduler = cfq


        SMART info:
            4 Start_Stop_Count          =    10537 
            5 Reallocated_Sector_Ct     =        0 
            9 Power_On_Hours            =     6579 [h]
          193 Load_Cycle_Count          =   159688 
          194 Temperature_Celsius       =       34 (Min/Max 12/48)  [°C]


/dev/sdb:
          Model     = TOSHIBA THNSNH128GMCT                   
          Firmware  = HTGAN102
          APM Level = 127
          Status    = active/idle
          TRIM      = supported
          Scheduler = noop


        SMART info:
            5 Reallocated_Sector_Ct     =        0 
            9 Power_On_Hours            =     6528 [h]
          194 Temperature_Celsius       =       31 (Min/Max 16/59)  [°C]
          241 Total_LBAs_Written        =    0.000 [TB]




+++ SATA Aggressive Link Power Management
/sys/class/scsi_host/host0/link_power_management_policy  = min_power
/sys/class/scsi_host/host1/link_power_management_policy  = min_power
/sys/class/scsi_host/host2/link_power_management_policy  = min_power
/sys/class/scsi_host/host3/link_power_management_policy  = min_power
/sys/class/scsi_host/host4/link_power_management_policy  = min_power
/sys/class/scsi_host/host5/link_power_management_policy  = min_power


+++ PCIe Active State Power Management
/sys/module/pcie_aspm/parameters/policy = powersave


+++ Intel Graphics
/sys/module/i915/parameters/powersave        = (not available)
/sys/module/i915/parameters/enable_rc6       =  3 (enabled + deep)
/sys/module/i915/parameters/enable_fbc       = -1 (use per-chip default)
/sys/module/i915/parameters/lvds_downclock   = (not available)
/sys/module/i915/parameters/semaphores       = -1 (use per-chip default)


+++ Wireless
bluetooth = off (software)
wifi      = on
wwan      = off (software)


wlp3s0(iwlwifi)     : connected, power management = on
wwp0s20u4i6(cdc_ncm): not connected


+++ Audio
/sys/module/snd_hda_intel/parameters/power_save            = 1
/sys/module/snd_hda_intel/parameters/power_save_controller = Y


+++ Docks and Device Bays
/sys/devices/platform/dock.0: battery_bay   = no battery 
/sys/devices/platform/dock.1: ata_bay       = drive present


+++ Runtime Power Management
device classes   = all
device blacklist = (not configured)
driver blacklist = radeon nouveau


/sys/bus/pci/devices/0000:00:00.0/power/control = auto (0x060000, Host bridge, ivb_uncore)
/sys/bus/pci/devices/0000:00:01.0/power/control = auto (0x060400, PCI bridge, pcieport)
/sys/bus/pci/devices/0000:00:02.0/power/control = auto (0x030000, VGA compatible controller, i915)
/sys/bus/pci/devices/0000:00:14.0/power/control = auto (0x0c0330, USB controller, xhci_hcd)
/sys/bus/pci/devices/0000:00:16.0/power/control = auto (0x078000, Communication controller, mei_me)
/sys/bus/pci/devices/0000:00:19.0/power/control = auto (0x020000, Ethernet controller, e1000e)
/sys/bus/pci/devices/0000:00:1a.0/power/control = auto (0x0c0320, USB controller, ehci-pci)
/sys/bus/pci/devices/0000:00:1b.0/power/control = auto (0x040300, Audio device, snd_hda_intel)
/sys/bus/pci/devices/0000:00:1c.0/power/control = auto (0x060400, PCI bridge, pcieport)
/sys/bus/pci/devices/0000:00:1c.1/power/control = auto (0x060400, PCI bridge, pcieport)
/sys/bus/pci/devices/0000:00:1c.2/power/control = auto (0x060400, PCI bridge, pcieport)
/sys/bus/pci/devices/0000:00:1d.0/power/control = auto (0x0c0320, USB controller, ehci-pci)
/sys/bus/pci/devices/0000:00:1f.0/power/control = auto (0x060100, ISA bridge, lpc_ich)
/sys/bus/pci/devices/0000:00:1f.2/power/control = auto (0x010601, SATA controller, ahci)
/sys/bus/pci/devices/0000:00:1f.3/power/control = auto (0x0c0500, SMBus, no driver)
/sys/bus/pci/devices/0000:02:00.0/power/control = auto (0x088001, System peripheral, sdhci-pci)
/sys/bus/pci/devices/0000:02:00.3/power/control = auto (0x0c0010, FireWire (IEEE 1394), firewire_ohci)
/sys/bus/pci/devices/0000:03:00.0/power/control = auto (0x028000, Network controller, iwlwifi)


+++ USB
autosuspend        = enabled
device whitelist   = 0765:5010
device blacklist   = (not configured)
wwan blacklist     = disabled


Bus 002 Device 003 ID 0765:5010 control = auto, autosuspend_delay_ms =  2000 -- X-Rite, Inc.  (usbhid)
Bus 002 Device 002 ID 8087:0024 control = auto, autosuspend_delay_ms =     0 -- Intel Corp. Integrated Rate Matching Hub (hub)
Bus 002 Device 001 ID 1d6b:0002 control = auto, autosuspend_delay_ms =     0 -- Linux Foundation 2.0 root hub (hub)
Bus 001 Device 004 ID 5986:02d2 control = auto, autosuspend_delay_ms =  2000 -- Acer, Inc  (uvcvideo)
Bus 001 Device 003 ID 147e:2020 control = auto, autosuspend_delay_ms =  2000 -- Upek TouchChip Fingerprint Coprocessor (WBF advanced mode) (no driver)
Bus 001 Device 002 ID 8087:0024 control = auto, autosuspend_delay_ms =     0 -- Intel Corp. Integrated Rate Matching Hub (hub)
Bus 001 Device 001 ID 1d6b:0002 control = auto, autosuspend_delay_ms =     0 -- Linux Foundation 2.0 root hub (hub)
Bus 004 Device 001 ID 1d6b:0003 control = auto, autosuspend_delay_ms =     0 -- Linux Foundation 3.0 root hub (hub)
Bus 003 Device 002 ID 0bdb:1926 control = auto, autosuspend_delay_ms =  2000 -- Ericsson Business Mobile Networks BV  (cdc_acm, cdc_wdm, cdc_ncm)
Bus 003 Device 001 ID 1d6b:0002 control = auto, autosuspend_delay_ms =     0 -- Linux Foundation 2.0 root hub (hub)


+++ ThinkPad Extended Battery Functions
tp-smapi   = inactive (kernel module 'tp_smapi' not installed)
tpacpi-bat = active


+++ ThinkPad Battery Status: BAT0 (Main / Internal)
/sys/class/power_supply/BAT0/manufacturer                   = LGC
/sys/class/power_supply/BAT0/model_name                     = 45N1011
/sys/class/power_supply/BAT0/cycle_count                    = (not supported)
/sys/class/power_supply/BAT0/energy_full_design             =  93600 [mWh]
/sys/class/power_supply/BAT0/energy_full                    =  71470 [mWh]
/sys/class/power_supply/BAT0/energy_now                     =  41730 [mWh]
/sys/class/power_supply/BAT0/power_now                      =  21985 [mW]
/sys/class/power_supply/BAT0/status                         = Discharging


tpacpi-bat.BAT0.startThreshold                              =     96 [%]
tpacpi-bat.BAT0.stopThreshold                               =    100 [%]
tpacpi-bat.BAT0.forceDischarge                              =      0



```

Any help or ideas?

---

### Post by Linuxisfast on 2016-05-24
Please install nvidia driver from additional drivers and after reboot, turn off your card via nvidia-settings and then measure the consumption.

---

