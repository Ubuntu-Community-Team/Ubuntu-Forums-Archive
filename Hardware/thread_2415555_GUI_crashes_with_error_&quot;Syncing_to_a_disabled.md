---
title: "GUI crashes with error &quot;Syncing to a disabled ring!&quot;"
date: 2019-03-27
forum: Hardware
---

### Post by Only1KW on 2019-03-27
Recently I received a new PC and installed Xubuntu 18.04 LTS on it from scratch.  I was using this computer up to a few hours ago with no issues with it, but when I walked away and returned to it an hour ago, I found myself at a blank xfce desktop. I also noticed my screens were no longer rotated to match my monitors and couldn't be rotated again using arandr.  Digging around, I see the following issue in /var/log/syslog:

```
Mar 27 13:02:00 lucca kernel: [182192.987983] radeon 0000:41:00.0: Syncing to a disabled ring!
Mar 27 13:02:00 lucca kernel: [182192.987989] radeon 0000:41:00.0: failed to sync rings (-22)
Mar 27 13:02:00 lucca kernel: [182192.988015] [drm:radeon_gem_va_ioctl [radeon]] *ERROR* Couldn't update BO_VA (-22)
Mar 27 13:02:10 lucca xfce4-notifyd[10047]: xfce4-notifyd: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
Mar 27 13:02:10 lucca at-spi-bus-launcher[8803]: XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
Mar 27 13:02:10 lucca at-spi-bus-launcher[8803]:       after 61061 requests (61061 known processed) with 0 events remaining.
Mar 27 13:02:10 lucca systemd[1061]: xfce4-notifyd.service: Main process exited, code=exited, status=1/FAILURE
Mar 27 13:02:10 lucca systemd[1061]: xfce4-notifyd.service: Failed with result 'exit-code'.
```

After walking away from it again and coming back, the GUI had disappeared again, and in its place was just the text 

```
Mar 27 14:31:56 lucca kernel: [187588.774987] [drm:si_dpm_set_power_state [radeon]] *ERROR* si_enable_smc_cac failed
```

I had to reboot to recover.  Upon reboot, I still saw the line above (with a different timestamp) displayed in my terminal, but I was able to start xfce again, rotated screens and all.

Any idea how I can prevent this from happening in the future short of replacing my graphics adapter?  I assume this is some sort of hardware driver bug in the kernel, but I really don't want to start trying random other kernels just to cross my fingers hoping the problem goes away.

```

 ~/ $ sudo lshw -c video
  *-display                 
       description: VGA compatible controller
       product: Cape Verde GL [FirePro W4100]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:41:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:142 memory:80000000-8fffffff memory:9f600000-9f63ffff ioport:3000(size=256) memory:c0000-dffff
```

```

 ~/ $ lspci -nn | grep VGA
41:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde GL [FirePro W4100] [1002:682c]
```

[ATTACH]282865[/ATTACH]
[ATTACH]282866[/ATTACH]
[ATTACH]282867[/ATTACH]
[ATTACH]282868[/ATTACH]

---

### Post by Only1KW on 2019-04-01
Bump.

---

### Post by Only1KW on 2019-04-08
FYI for anyone else that stumbles across this while searching for the same error, this issue did continue to reproduce.  I've upgraded my graphics drivers to amdgpu, and so far (in the last week and a half), I haven't hit this again.  If you hit a similar issue, I recommend upgrading to that.  Be sure to update GRUB_CMDLINE_LINUX in your grub config to include "radeon.si_support=0 radeon.cik_support=0, amdgpu.si_support=1 amdgpu.cik_support=1" and stub out the radeon driver.

---

