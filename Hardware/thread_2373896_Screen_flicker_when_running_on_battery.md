---
title: "Screen flicker when running on battery"
date: 2017-10-10
forum: Hardware
---

### Post by ati.atas93 on 2017-10-10
Hi everyone!

After reading dozens of 'unhelpful' posts on this issue, I post my issue here: I have a Lenovo Yoga 500-14acl 80na (AMD A8 version) and I solely use Ubuntu 16.04LTS (new to Ubuntu though, please have mercy :D). When plugged in, the laptop works fine but when running on battery, the screen flickers (on any brightness setting). This flicker seems to be tied to CPU usage and the battery is apparently not calibrated (0% indicated but it is certainly charged as it keeps on working). I installed TLP but changing the parameters any possible way, did not help either. Graphics are handled by an AMD Mullins integrated chip, with the supported radeon drivers installed.

If any further information is needed, please tell me so I can learn and help you to help me :)

--- TLP 1.0 --------------------------------------------


+++ Configured Settings: /etc/default/tlp
TLP_ENABLE=1
TLP_DEFAULT_MODE=AC
TLP_PERSISTENT_DEFAULT=0
DISK_IDLE_SECS_ON_AC=0
DISK_IDLE_SECS_ON_BAT=2
MAX_LOST_WORK_SECS_ON_AC=15
MAX_LOST_WORK_SECS_ON_BAT=60
CPU_HWP_ON_AC=balance_performance
CPU_HWP_ON_BAT=balance_performance
SCHED_POWERSAVE_ON_AC=0
SCHED_POWERSAVE_ON_BAT=1
NMI_WATCHDOG=0
ENERGY_PERF_POLICY_ON_AC=performance
ENERGY_PERF_POLICY_ON_BAT=performance
DISK_DEVICES="sda sdb"
DISK_APM_LEVEL_ON_AC="254 254"
DISK_APM_LEVEL_ON_BAT="128 128"
SATA_LINKPWR_ON_AC=max_performance
SATA_LINKPWR_ON_BAT=medium_power
AHCI_RUNTIME_PM_TIMEOUT=15
PCIE_ASPM_ON_AC=performance
PCIE_ASPM_ON_BAT=performance
RADEON_POWER_PROFILE_ON_AC=high
RADEON_POWER_PROFILE_ON_BAT=auto
RADEON_DPM_STATE_ON_AC=performance
RADEON_DPM_STATE_ON_BAT=performance
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
USB_AUTOSUSPEND=0
USB_BLACKLIST_BTUSB=0
USB_BLACKLIST_PHONE=0
USB_BLACKLIST_WWAN=1
RESTORE_DEVICE_STATE_ON_STARTUP=0



sudo tlp-stat -b
--- TLP 1.0 --------------------------------------------


+++ Battery Status
/sys/class/power_supply/BAT0/manufacturer = (not available)
/sys/class/power_supply/BAT0/model_name = (not available)
/sys/class/power_supply/BAT0/cycle_count = (not supported)
/sys/class/power_supply/BAT0/charge_full_design = (not available) 
/sys/class/power_supply/BAT0/charge_full = (not available) 
/sys/class/power_supply/BAT0/charge_now = 2820 [mAh]
/sys/class/power_supply/BAT0/current_now = 0 [mA]
/sys/class/power_supply/BAT0/status = Charging

---

