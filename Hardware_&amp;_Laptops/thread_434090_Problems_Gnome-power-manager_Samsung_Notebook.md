---
title: "Problems Gnome-power-manager Samsung Notebook"
date: 2007-05-05
forum: Hardware &amp; Laptops
---

### Post by kanibasami on 2007-05-05
I 'm having problems with the Gnome-power-manager and my brightness control on a Samsung X11 notebook. I'm running Ubuntu Feisty and the brightness setting via "Fn" keys as well as gnome-power-manager does not work. Gnome-power-manager doesn't even show a slider to adjust the brightness. Furthermore the LCD does not dim or brighten up when AC is dis/connected. Only a reboot changes.  Here some data:

```

:~$ acpi -V
     Battery 1: charging, 87%, 00:24:59 until charged
     Thermal 1: active[0], 50.0 degrees C
     Thermal 2: ok, 50.0 degrees C
  AC Adapter 1: on-line
lennart@laptux:~$ 
```

```
~$ gnome-power-manager --verbose --no-daemon
[gpm_debug_init] gpm-debug.c:217 (22:28:38):     Verbose debugging enabled
[main] gpm-main.c:205 (22:28:38):        GNOME Energieverwaltung 2.18.2
[gpm_proxy_connect] gpm-proxy.c:101 (22:28:38):  emitting proxy-status TRUE: org.freedesktop.Hal
[gpm_proxy_connect] gpm-proxy.c:101 (22:28:38):  emitting proxy-status TRUE: org.freedesktop.Hal
[gpm_control_init] gpm-control.c:863 (22:28:38):         Using a supressed policy timeout of 5 seconds
[gpm_refcount_add] gpm-refcount.c:101 (22:28:38):        refcount now: 1
[gpm_refcount_add] gpm-refcount.c:102 (22:28:38):        non zero, so sending REFCOUNT_ADDED
[gpm_power_refcount_added] gpm-power.c:138 (22:28:38):   Data is now not trusted
[gpm_hash_new_kind_cache] gpm-power.c:1727 (22:28:38):   creating cache
[gpm_hash_new_device_cache] gpm-power.c:1761 (22:28:38):         creating cache
[gpm_warning_init] gpm-warning.c:260 (22:28:38):         Using per-time notification policy
[gpm_proxy_connect] gpm-proxy.c:101 (22:28:38):  emitting proxy-status TRUE: org.freedesktop.Hal
[gpm_cpufreq_set_governor] gpm-cpufreq.c:191 (22:28:38):         Doing SetCPUFreqGovernor (ondemand)
[gpm_cpufreq_set_consider_nice] gpm-cpufreq.c:506 (22:28:38):    Doing SetCPUFreqConsiderNice (0)
[gpm_cpufreq_set_performance] gpm-cpufreq.c:126 (22:28:38):      Doing SetCPUFreqPerformance (85)
[gpm_proxy_connect] gpm-proxy.c:101 (22:28:38):  emitting proxy-status TRUE: org.gnome.ScreenSaver
[gpm_srv_backlight_sync_policy] gpm-srv-backlight.c:151 (22:28:38):      choosing sensible default
[gpm_srv_backlight_sync_policy] gpm-srv-backlight.c:153 (22:28:38):      laptop, so use GPM_DPMS_METHOD_OFF
[gpm_srv_backlight_sync_policy] gpm-srv-backlight.c:185 (22:28:38):      SRV_BACKLIGHT parameters 0 0 1800, method '4'
[gpm_dpms_set_enabled] gpm-dpms.c:435 (22:28:38):        setting DPMS enabled: 1
[x11_sync_server_dpms_settings] gpm-dpms.c:130 (22:28:38):       Syncing DPMS settings enabled=1 timeouts=0 0 0
[x11_sync_server_dpms_settings] gpm-dpms.c:130 (22:28:38):       Syncing DPMS settings enabled=1 timeouts=0 0 0
[gpm_idle_set_check_cpu] gpm-idle.c:306 (22:28:38):      Setting the CPU load check to 0
[gpm_manager_init] gpm-manager.c:1564 (22:28:38):        creating new inhibit instance
[gpm_manager_init] gpm-manager.c:1575 (22:28:38):        creating new control instance
[gpm_manager_init] gpm-manager.c:1585 (22:28:38):        creating new tray icon
[gpm_manager_init] gpm-manager.c:1594 (22:28:38):        initialising info infrastructure
[gpm_hal_enable_power_save] gpm-hal.c:1414 (22:28:38):   Doing SetPowerSave (0)
[gpm_hal_enable_power_save] gpm-hal.c:1421 (22:28:38):   ERROR: No powersave method found
*** WARNING ***
[gpm_hal_enable_power_save] gpm-hal.c:1426 (22:28:38):   SetPowerSave failed!
[gpm_idle_set_system_timeout] gpm-idle.c:357 (22:28:38):         Setting system idle timeout: 0
[get_stock_id] gpm-tray-icon.c:680 (22:28:38):   Trying CRITICAL icon: primary, ups, mouse, keyboard
[get_stock_id] gpm-tray-icon.c:704 (22:28:38):   Trying CHARGING icon: primary, ups
[get_stock_id] gpm-tray-icon.c:716 (22:28:38):   no devices (dis)charging, so no icon will be displayed.
[gpm_tray_icon_sync] gpm-tray-icon.c:763 (22:28:38):     Going to use stock id: (null)
[gpm_tray_icon_sync] gpm-tray-icon.c:783 (22:28:38):     no icon will be displayed
*** WARNING ***
[main] gpm-main.c:239 (22:28:38):        Energieverwaltung is already running in this session.
```

```
 dmesg | grep acpi
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[   25.376000] ibm_acpi: ec object not found
[   25.628000] ACPI Exception (acpi_video-1564): UNKNOWN_STATUS_CODE, Cant attach device [20060707]
[   25.672000] pcc_acpi: loading...

```

I hope it's enough information to solve the problem, but I am more a noob than a pro in Linux. Hope you can give me an explanation step by step.

Thanks a lot

Kanibasami

---

