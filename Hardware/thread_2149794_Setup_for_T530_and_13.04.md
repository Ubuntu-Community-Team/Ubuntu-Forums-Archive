---
title: "Setup for T530 and 13.04"
date: 2013-05-29
forum: Hardware
---

### Post by amdemas on 2013-05-29
Hey Everyone,

Well I recently just picked up a T530 and I am in the process of setting everything up. Some of the issues I am experiencing I couldn't find.

Issues:

  1. Mute button doesn't seem to work (doesn't light up when pressed.)
  2. Ethernet does not connect after resume from suspend. 
  3. HDAPSD doesn't seem to work (Anyone find a work around?)

I am also looking for some recommendations on how to go about utilizing the NVIDIA Optimus. I have seen post about bumblebee and some posts about NVIDIA providing drivers now. What is the best? Also I seem to be getting around 3hrs or less on a 9 cell battery. Any have better luck with tuning down resources to make this better?

Any help is appreciated.

---

### Post by Yellow Pasque on 2013-05-30
Use Bumblebee.
The official Optimus support from Nvidia is not what most people expect (transparent load-based switching between the integrated and discrete cards, like in Windows). Instead, it just uses the nvidia card to do everything, which is a big drain on the battery. (Discussion: [http://phoronix.com/forums/showthread.php?79655-NVIDIA-Has-Major-New-Linux-Driver-Optimus-RandR-1-4](http://phoronix.com/forums/showthread.php?79655-NVIDIA-Has-Major-New-Linux-Driver-Optimus-RandR-1-4) )

> Mute button doesn't seem to work
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1125452](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1125452)

> Ethernet does not connect after resume from suspend. 
Try reloading the module:
```
sudo modprobe -r e1000e
sudo modprobe -v e1000e
```

---

### Post by amdemas on 2013-05-30
> **Temüjin said:**
> 

Try reloading the module:
```
sudo modprobe -r e1000e
sudo modprobe -v e1000e
```


I tried that and still a no go.... Only remedy is to reboot the system. :(

---

### Post by linrunner on 2013-05-30
Hi,

1) The mute button works, you mean the **mic** mute button – see [http://askubuntu.com/questions/125367/enabling-mic-mute-button-and-light-on-lenovo-thinkpads](http://askubuntu.com/questions/125367/enabling-mic-mute-button-and-light-on-lenovo-thinkpads) (led needs patched kernel)
2) Try the test kernel from [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1181622](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1181622)
3) No workaround available atm (tp-smapi doesn't work at all on the *30)

---

### Post by amdemas on 2013-06-02
> **linrunner said:**
> Hi,

1) The mute button works, you mean the **mic** mute button – see [http://askubuntu.com/questions/125367/enabling-mic-mute-button-and-light-on-lenovo-thinkpads](http://askubuntu.com/questions/125367/enabling-mic-mute-button-and-light-on-lenovo-thinkpads) (led needs patched kernel)
2) Try the test kernel from [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1181622](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1181622)
3) No workaround available atm (tp-smapi doesn't work at all on the *30)


1) That worked perfectly! Thank you
2) I haven't been able to test it yet, but I will be in my office tomorrow to try it out. Thanks for the suggestion and I will update with my findings.
3) :( I hope they fix this HDAPS is something I could live with out, but the added protection would be awesome. 

After tweaking the power settings using TLP I am getting about 4.5 hours, but would love to see another hour added somehow. Any other suggestions? I followed this post about power tweaks [HERE]("http://askubuntu.com/questions/285434/is-there-a-power-saving-application-similar-to-jupiter")

---

### Post by akulbe on 2013-06-02
I know you're asking about a T530, and they may not be the same... but I'm just mentioning this in the case that you might the same option in your EFI has the same option that I do on my W530. I can go into the Display menu and set the graphics adapter option to the Intel (Integrated), the Nvidia (Discrete), or have system switch between the two. (I think this option was called Dynamic... I'm not 100% sure.)

If you want to maximize battery life, and don't need/use the high-end graphics.... stick with Integrated.
If you want the best graphics and battery life isn't your highest priority, go with Discrete. (and use the proprietary driver from Nvidia)

Hopefully you have that option.

---

### Post by linrunner on 2013-06-03
@amdemas: show me
```
sudo tlp-stat
```
and we shall see about further optimizations.

If your T530 happens to have Optimus Hybrid Graphics (no good choice for Linux) then you may try one of akulbe's suggestions or you [install Bumblebee]("https://wiki.ubuntu.com/Bumblebee") to use switchable mode ("Optimus" in BIOS).

---

### Post by amdemas on 2013-06-03
> **amdemas said:**
> 1) That worked perfectly! Thank you
2) I haven't been able to test it yet, but I will be in my office tomorrow to try it out. Thanks for the suggestion and I will update with my findings.
3) :( I hope they fix this HDAPS is something I could live with out, but the added protection would be awesome. 

After tweaking the power settings using TLP I am getting about 4.5 hours, but would love to see another hour added somehow. Any other suggestions? I followed this post about power tweaks [HERE]("http://askubuntu.com/questions/285434/is-there-a-power-saving-application-similar-to-jupiter")


UPDATE: 

2) Works great with that updated kernel

---

### Post by amdemas on 2013-06-03
> **linrunner said:**
> @amdemas: show me
```
sudo tlp-stat
```
and we shall see about further optimizations.

If your T530 happens to have Optimus Hybrid Graphics (no good choice for Linux) then you may try one of akulbe's suggestions or you [install Bumblebee]("https://wiki.ubuntu.com/Bumblebee") to use switchable mode ("Optimus" in BIOS).


Here you go!

```
--- TLP 0.3.9 --------------------------------------------

+++ Configured Settings: /etc/default/tlp
TLP_ENABLE=1
DISK_IDLE_SECS_ON_AC=0
DISK_IDLE_SECS_ON_BAT=5
MAX_LOST_WORK_SECS_ON_AC=15
MAX_LOST_WORK_SECS_ON_BAT=60
CPU_SCALING_GOVERNOR_ON_AC=ondemand
CPU_SCALING_GOVERNOR_ON_BAT=powersave
CPU_BOOST_ON_AC=1
sCPU_BOOST_ON_BAT=0
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
BAY_POWEROFF_ON_BAT=1
BAY_DEVICE="sr0"
RUNTIME_PM_ON_AC=on
RUNTIME_PM_ON_BAT=auto
RUNTIME_PM_ALL=1
USB_AUTOSUSPEND=1
RESTORE_DEVICE_STATE_ON_STARTUP=0
DEVICES_TO_DISABLE_ON_STARTUP="bluetooth"
DEVICES_TO_ENABLE_ON_STARTUP="wifi wwan"
DEVICES_TO_ENABLE_ON_RADIOSW="wifi wwan"
DISABLE_TPACPIBAT=1


+++ System Info
System         = LENOVO ThinkPad T530 23924BU
BIOS           = G4ET37WW (1.12 )
Release        = Ubuntu 13.04
Kernel         = 3.8.0-24-generic x86_64
/proc/cmdline  = BOOT_IMAGE=/vmlinuz-3.8.0-24-generic root=/dev/mapper/ubuntu--vg-root ro quiet nox2apic splash pcie_aspm=force i915.i915_enable_fbc=1 i915.lvds_downclock=1 drm.vblankoffdelay=1 i915.semaphores=1


+++ System Status
TLP power save = enabled
power source   = ac


+++ Processor
CPU Model      = Intel(R) Core(TM) i7-3520M CPU @ 2.90GHz


/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor  = ondemand
/sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq  =  1200000 [kHz]
/sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq  =  2901000 [kHz]
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies = 2901000 2900000 2800000 2700000 2500000 2400000 2300000 2200000 2000000 1900000 1800000 1700000 1600000 1400000 1300000 1200000 [kHz]


/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor  = ondemand
/sys/devices/system/cpu/cpu1/cpufreq/scaling_min_freq  =  1200000 [kHz]
/sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq  =  2901000 [kHz]
/sys/devices/system/cpu/cpu1/cpufreq/scaling_available_frequencies = 2901000 2900000 2800000 2700000 2500000 2400000 2300000 2200000 2000000 1900000 1800000 1700000 1600000 1400000 1300000 1200000 [kHz]


/sys/devices/system/cpu/cpu2/cpufreq/scaling_governor  = ondemand
/sys/devices/system/cpu/cpu2/cpufreq/scaling_min_freq  =  1200000 [kHz]
/sys/devices/system/cpu/cpu2/cpufreq/scaling_max_freq  =  2901000 [kHz]
/sys/devices/system/cpu/cpu2/cpufreq/scaling_available_frequencies = 2901000 2900000 2800000 2700000 2500000 2400000 2300000 2200000 2000000 1900000 1800000 1700000 1600000 1400000 1300000 1200000 [kHz]


/sys/devices/system/cpu/cpu3/cpufreq/scaling_governor  = ondemand
/sys/devices/system/cpu/cpu3/cpufreq/scaling_min_freq  =  1200000 [kHz]
/sys/devices/system/cpu/cpu3/cpufreq/scaling_max_freq  =  2901000 [kHz]
/sys/devices/system/cpu/cpu3/cpufreq/scaling_available_frequencies = 2901000 2900000 2800000 2700000 2500000 2400000 2300000 2200000 2000000 1900000 1800000 1700000 1600000 1400000 1300000 1200000 [kHz]


/sys/devices/system/cpu/cpufreq/boost                  = 1
/proc/sys/kernel/nmi_watchdog                          = 0


+++ Undervolting
PHC kernel not available.


+++ Temperatures
CPU temp               =    49 [°C]
/proc/acpi/ibm/fan     =     0 [/min]


+++ File System
/proc/sys/vm/laptop_mode               =     0
/proc/sys/vm/dirty_writeback_centisecs =  1500
/proc/sys/vm/dirty_expire_centisecs    =  1500
/proc/sys/vm/dirty_ratio               =    10
/proc/sys/vm/dirty_background_ratio    =     5
/proc/sys/fs/xfs/age_buffer_centisecs  = (not available)
/proc/sys/fs/xfs/xfssyncd_centisecs    = (not available)
/proc/sys/fs/xfs/xfsbufd_centisecs     = (not available)


+++ Storage Devices
/dev/sda:
          Model     = HITACHI HTS725050A7E630                 
          Firmware  = GH2ZB390
          APM Level = 254
          Status    = active/idle
          scheduler = deadline


        SMART info:
            4 Start_Stop_Count          =      205 
            5 Reallocated_Sector_Ct     =        0 
            9 Power_On_Hours            =       93 [h]
          193 Load_Cycle_Count          =     2797 
          194 Temperature_Celsius       =       34 (Min/Max 21/47)  [°C]




+++ SATA Aggressive Link Power Management
/sys/class/scsi_host/host0/link_power_management_policy  = max_performance
/sys/class/scsi_host/host1/link_power_management_policy  = max_performance
/sys/class/scsi_host/host2/link_power_management_policy  = max_performance
/sys/class/scsi_host/host3/link_power_management_policy  = max_performance
/sys/class/scsi_host/host4/link_power_management_policy  = max_performance
/sys/class/scsi_host/host5/link_power_management_policy  = max_performance


+++ PCIe Active State Power Management
/sys/module/pcie_aspm/parameters/policy = performance


+++ Intel Graphics
/sys/module/i915/parameters/powersave        =  1 (enabled)
/sys/module/i915/parameters/i915_enable_rc6  = -1 (use per-chip default)
/sys/module/i915/parameters/i915_enable_fbc  =  1 (enabled)
/sys/module/i915/parameters/lvds_downclock   =  1 (enabled)
/sys/module/i915/parameters/semaphores       =  1 (enabled)


+++ Wireless
bluetooth = off (software)
wifi      = on
wwan      = none (no device)


wlan0(iwlwifi): power management = off


+++ Audio
/sys/module/snd_hda_intel/parameters/power_save            = 1
/sys/module/snd_hda_intel/parameters/power_save_controller = Y


+++ ThinkPad Extended Battery Functions
tp-smapi   = inactive (kernel module 'tp_smapi' load error)
tpacpi-bat = inactive (disabled by user configuration)


+++ Battery Status
/sys/class/power_supply/BAT0/manufacturer                   = SANYO
/sys/class/power_supply/BAT0/model_name                     = 45N1007
/sys/class/power_supply/BAT0/cycle_count                    = (not supported)
/sys/class/power_supply/BAT0/energy_full_design             =  86580 [mWh]
/sys/class/power_supply/BAT0/energy_full                    =  80720 [mWh]
/sys/class/power_supply/BAT0/energy_now                     =  36920 [mWh]
/sys/class/power_supply/BAT0/power_now                      =  40225 [mW]
/sys/class/power_supply/BAT0/status                         = Charging


+++ Runtime Power Management
/sys/bus/pci/devices/0000:00:00.0/power/control = on   (0x060000 Host bridge)
/sys/bus/pci/devices/0000:00:01.0/power/control = on   (0x060400 PCI bridge)
/sys/bus/pci/devices/0000:00:02.0/power/control = on   (0x030000 VGA compatible controller)
/sys/bus/pci/devices/0000:00:14.0/power/control = on   (0x0c0330 USB controller)
/sys/bus/pci/devices/0000:00:16.0/power/control = on   (0x078000 Communication controller)
/sys/bus/pci/devices/0000:00:16.3/power/control = on   (0x070002 Serial controller)
/sys/bus/pci/devices/0000:00:19.0/power/control = on   (0x020000 Ethernet controller)
/sys/bus/pci/devices/0000:00:1a.0/power/control = on   (0x0c0320 USB controller)
/sys/bus/pci/devices/0000:00:1b.0/power/control = on   (0x040300 Audio device)
/sys/bus/pci/devices/0000:00:1c.0/power/control = on   (0x060400 PCI bridge)
/sys/bus/pci/devices/0000:00:1c.1/power/control = on   (0x060400 PCI bridge)
/sys/bus/pci/devices/0000:00:1c.2/power/control = on   (0x060400 PCI bridge)
/sys/bus/pci/devices/0000:00:1d.0/power/control = on   (0x0c0320 USB controller)
/sys/bus/pci/devices/0000:00:1f.0/power/control = on   (0x060100 ISA bridge)
/sys/bus/pci/devices/0000:00:1f.2/power/control = on   (0x010601 SATA controller)
/sys/bus/pci/devices/0000:00:1f.3/power/control = on   (0x0c0500 SMBus)
/sys/bus/pci/devices/0000:01:00.0/power/control = on   (0x030000 VGA compatible controller)
/sys/bus/pci/devices/0000:02:00.0/power/control = on   (0x088001 System peripheral)
/sys/bus/pci/devices/0000:02:00.3/power/control = on   (0x0c0010 FireWire (IEEE 1394))
/sys/bus/pci/devices/0000:03:00.0/power/control = on   (0x028000 Network controller)


+++ USB
tlp usb autosuspend = enabled
tlp usb blacklist   = (not configured)


Bus 001 Device 002 ID 8087:0024 control = auto, autosuspend_delay_ms =  2000 -- Intel Corp. Integrated Rate Matching Hub (hub)
Bus 002 Device 002 ID 8087:0024 control = auto, autosuspend_delay_ms =  2000 -- Intel Corp. Integrated Rate Matching Hub (hub)
Bus 001 Device 001 ID 1d6b:0002 control = auto, autosuspend_delay_ms =  2000 -- Linux Foundation 2.0 root hub (hub)
Bus 002 Device 001 ID 1d6b:0002 control = auto, autosuspend_delay_ms =  2000 -- Linux Foundation 2.0 root hub (hub)
Bus 003 Device 001 ID 1d6b:0002 control = auto, autosuspend_delay_ms =  2000 -- Linux Foundation 2.0 root hub (hub)
Bus 004 Device 001 ID 1d6b:0003 control = auto, autosuspend_delay_ms =  2000 -- Linux Foundation 3.0 root hub (hub)
Bus 001 Device 003 ID 147e:2020 control = auto, autosuspend_delay_ms =  2000 -- Upek  (no driver)
Bus 001 Device 004 ID 04f2:b2ea control = auto, autosuspend_delay_ms =  2000 -- Chicony Electronics Co., Ltd  (uvcvideo)



```

---

### Post by linrunner on 2013-06-04
Your model 2392-4BU has in fact Optimus graphics. Which of the above mentioned BIOS settings &#8211; Integrated / Discrete / Optimus &#8211; do you use?

---

### Post by amdemas on 2013-06-04
I use Optimus. I installed bumblebee so its off.

---

### Post by linrunner on 2013-06-04
> **amdemas said:**
> I use Optimus. I installed bumblebee so its off.
Fine, i see no further power optimizations.

Some final remarks concerning your TLP settings:


```
DEVICES_TO_ENABLE_ON_STARTUP="wifi wwan"
DEVICES_TO_ENABLE_ON_RADIOSW="wifi wwan"
```
=> not needed, comment them out again.

> tpacpi-bat = inactive (disabled by user configuration)
```
DISABLE_TPACPIBAT=1
```
=> is counterproductive on your hardware generation. tpacpi-bat is needed for TLP's battery functions. Change to
```
DISABLE_TPACPIBAT=0
```

---

### Post by novalu2 on 2013-11-08
> **linrunner said:**
> 
3) No workaround available atm (tp-smapi doesn't work at all on the *30)

Is there any news about HDAPS support without tp-smapi on T530? I found that successor for tp-smapi is [thinkpad-acpi]("http://www.thinkwiki.org/wiki/Thinkpad-acpi"), but it has not support for hdaps :/

Thanks in advance.

---

### Post by amdemas on 2013-11-09
Nothing yet for hdaps. I will note that since upgrading to 13.10 I have noticed better performance and battery life. I get a solid 6-7 hours with no tweaking whatsoever.

---

