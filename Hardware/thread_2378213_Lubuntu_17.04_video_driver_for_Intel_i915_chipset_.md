---
title: "Lubuntu 17.04 video driver for Intel i915 chipset on Dell Latitude e6410"
date: 2017-11-21
forum: Hardware
---

### Post by robert_frittmann2 on 2017-11-21
Trying to get better screen resolutions for this machine. Currently I can only get 1280x800 on the internal eDP1 display, and 1024x768 on the external VGA display. Here are some outputs of some common tests which might help in diagnosing the problem...

uname -a
```
Linux latitude 4.10.0-40-generic #44-Ubuntu SMP Thu Nov 9 14:49:09 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

lspci | grep VGA
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
```

lspci -nnk | grep VGA -A1
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
    Subsystem: Dell Latitude E6410 [1028:040a]
```

lshw -c video
```
  *-display                 
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:26 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:70b0(size=8) memory:c0000-dffff
```

glxinfo | grep "version"
```
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
    Max core profile version: 0.0
    Max compat profile version: 2.1
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 2.0
OpenGL version string: 2.1 Mesa 17.3.0-rc4
OpenGL shading language version string: 1.20
OpenGL ES profile version string: OpenGL ES 2.0 Mesa 17.3.0-rc4
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 1.0.16
```

inxi -Fxz
```
System:    Host: latitude Kernel: 4.10.0-40-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 17.04
Machine:   Device: laptop System: Dell product: Latitude E6410 v: 0001
           Mobo: Dell model: N/A BIOS: Dell v: A06 date: 11/20/2010
Battery    BAT0: charge: 56.0 Wh 256.2% condition: 21.9/56.0 Wh (39%)
           model: SMP DELL TX28306 status: Full
CPU:       Dual core Intel Core i5 M 540 (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 10108
           clock speeds: max: 2534 MHz 1: 1333 MHz 2: 1199 MHz 3: 1199 MHz
           4: 1999 MHz
Graphics:  Card: Intel Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.19.3 driver: intel
           Resolution: 1280x800@60.14hz, 1024x768@60.00hz
           GLX Renderer: Mesa DRI Intel Ironlake Mobile
           GLX Version: 2.1 Mesa 17.3.0-rc4 Direct Rendering: Yes
Audio:     Card Intel 5 Series/3400 Series High Definition Audio
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.10.0-40-generic
Network:   Card-1: Intel 82577LM Gigabit Network Connection
           driver: e1000e v: 3.2.6-k port: 7040 bus-ID: 00:19.0
           IF: eno1 state: down mac: <filter>
           Card-2: Intel Centrino Ultimate-N 6300
           driver: iwlwifi bus-ID: 02:00.0
           IF: wlp2s0 state: up mac: <filter>
Drives:    HDD Total Size: 320.1GB (4.2% used)
           ID-1: /dev/mmcblk0 model: N/A size: 32.0GB
           ID-2: /dev/sda model: TOSHIBA_MQ01ACF0 size: 320.1GB temp: 37C
Partition: ID-1: / size: 197G used: 9.1G (5%) fs: ext4 dev: /dev/sda3
           ID-2: /boot size: 470M used: 125M (29%) fs: ext2 dev: /dev/sda1
           ID-3: swap-1 size: 3.70GB used: 0.00GB (0%) fs: swap dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 54.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 189 Uptime: 2:58 Memory: 1273.4/3807.5MB
           Init: systemd runlevel: 5 Gcc sys: 6.3.0
           Client: Shell (bash 4.4.71) inxi: 2.3.8
```

modinfo i915
```

filename:       /lib/modules/4.10.0-40-generic/kernel/drivers/gpu/drm/i915/i915.ko
license:        GPL and additional rights
description:    Intel Graphics
author:         Intel Corporation
author:         Tungsten Graphics, Inc.
firmware:       i915/bxt_dmc_ver1_07.bin
firmware:       i915/skl_dmc_ver1_26.bin
firmware:       i915/kbl_dmc_ver1_01.bin
firmware:       i915/skl_guc_ver6_1.bin
srcversion:     E344723FEE4FBA650921D4D
alias:          pci:v00008086d0000593Bsv*sd*bc03sc*i*
alias:          pci:v00008086d00005927sv*sd*bc03sc*i*
alias:          pci:v00008086d00005926sv*sd*bc03sc*i*
alias:          pci:v00008086d00005923sv*sd*bc03sc*i*
alias:          pci:v00008086d0000591Dsv*sd*bc03sc*i*
alias:          pci:v00008086d0000591Asv*sd*bc03sc*i*
alias:          pci:v00008086d0000591Bsv*sd*bc03sc*i*
alias:          pci:v00008086d00005912sv*sd*bc03sc*i*
alias:          pci:v00008086d0000591Esv*sd*bc03sc*i*
alias:          pci:v00008086d00005921sv*sd*bc03sc*i*
alias:          pci:v00008086d00005916sv*sd*bc03sc*i*
alias:          pci:v00008086d0000590Asv*sd*bc03sc*i*
alias:          pci:v00008086d0000590Bsv*sd*bc03sc*i*
alias:          pci:v00008086d00005908sv*sd*bc03sc*i*
alias:          pci:v00008086d00005902sv*sd*bc03sc*i*
alias:          pci:v00008086d0000590Esv*sd*bc03sc*i*
alias:          pci:v00008086d00005906sv*sd*bc03sc*i*
alias:          pci:v00008086d00005917sv*sd*bc03sc*i*
alias:          pci:v00008086d00005915sv*sd*bc03sc*i*
alias:          pci:v00008086d00005913sv*sd*bc03sc*i*
alias:          pci:v00008086d00005A85sv*sd*bc03sc*i*
alias:          pci:v00008086d00005A84sv*sd*bc03sc*i*
alias:          pci:v00008086d00001A85sv*sd*bc03sc*i*
alias:          pci:v00008086d00001A84sv*sd*bc03sc*i*
alias:          pci:v00008086d00000A84sv*sd*bc03sc*i*
alias:          pci:v00008086d0000193Asv*sd*bc03sc*i*
alias:          pci:v00008086d0000193Dsv*sd*bc03sc*i*
alias:          pci:v00008086d0000193Bsv*sd*bc03sc*i*
alias:          pci:v00008086d00001932sv*sd*bc03sc*i*
alias:          pci:v00008086d0000192Asv*sd*bc03sc*i*
alias:          pci:v00008086d0000192Bsv*sd*bc03sc*i*
alias:          pci:v00008086d00001927sv*sd*bc03sc*i*
alias:          pci:v00008086d00001926sv*sd*bc03sc*i*
alias:          pci:v00008086d00001923sv*sd*bc03sc*i*
alias:          pci:v00008086d0000191Dsv*sd*bc03sc*i*
alias:          pci:v00008086d0000191Asv*sd*bc03sc*i*
alias:          pci:v00008086d0000191Bsv*sd*bc03sc*i*
alias:          pci:v00008086d00001912sv*sd*bc03sc*i*
alias:          pci:v00008086d0000191Esv*sd*bc03sc*i*
alias:          pci:v00008086d00001921sv*sd*bc03sc*i*
alias:          pci:v00008086d00001916sv*sd*bc03sc*i*
alias:          pci:v00008086d0000190Asv*sd*bc03sc*i*
alias:          pci:v00008086d0000190Bsv*sd*bc03sc*i*
alias:          pci:v00008086d00001902sv*sd*bc03sc*i*
alias:          pci:v00008086d0000190Esv*sd*bc03sc*i*
alias:          pci:v00008086d00001906sv*sd*bc03sc*i*
alias:          pci:v00008086d000022B3sv*sd*bc03sc*i*
alias:          pci:v00008086d000022B2sv*sd*bc03sc*i*
alias:          pci:v00008086d000022B1sv*sd*bc03sc*i*
alias:          pci:v00008086d000022B0sv*sd*bc03sc*i*
alias:          pci:v00008086d0000163Dsv*sd*bc03sc*i*
alias:          pci:v00008086d0000163Asv*sd*bc03sc*i*
alias:          pci:v00008086d0000163Esv*sd*bc03sc*i*
alias:          pci:v00008086d0000163Bsv*sd*bc03sc*i*
alias:          pci:v00008086d00001636sv*sd*bc03sc*i*
alias:          pci:v00008086d00001632sv*sd*bc03sc*i*
alias:          pci:v00008086d0000162Dsv*sd*bc03sc*i*
alias:          pci:v00008086d0000162Asv*sd*bc03sc*i*
alias:          pci:v00008086d0000162Esv*sd*bc03sc*i*
alias:          pci:v00008086d0000162Bsv*sd*bc03sc*i*
alias:          pci:v00008086d00001626sv*sd*bc03sc*i*
alias:          pci:v00008086d00001622sv*sd*bc03sc*i*
alias:          pci:v00008086d0000161Dsv*sd*bc03sc*i*
alias:          pci:v00008086d0000161Asv*sd*bc03sc*i*
alias:          pci:v00008086d0000160Dsv*sd*bc03sc*i*
alias:          pci:v00008086d0000160Asv*sd*bc03sc*i*
alias:          pci:v00008086d0000161Esv*sd*bc03sc*i*
alias:          pci:v00008086d0000161Bsv*sd*bc03sc*i*
alias:          pci:v00008086d00001616sv*sd*bc03sc*i*
alias:          pci:v00008086d00001612sv*sd*bc03sc*i*
alias:          pci:v00008086d0000160Esv*sd*bc03sc*i*
alias:          pci:v00008086d0000160Bsv*sd*bc03sc*i*
alias:          pci:v00008086d00001606sv*sd*bc03sc*i*
alias:          pci:v00008086d00001602sv*sd*bc03sc*i*
alias:          pci:v00008086d00000155sv*sd*bc03sc*i*
alias:          pci:v00008086d00000157sv*sd*bc03sc*i*
alias:          pci:v00008086d00000F33sv*sd*bc03sc*i*
alias:          pci:v00008086d00000F32sv*sd*bc03sc*i*
alias:          pci:v00008086d00000F31sv*sd*bc03sc*i*
alias:          pci:v00008086d00000F30sv*sd*bc03sc*i*
alias:          pci:v00008086d00000D26sv*sd*bc03sc*i*
alias:          pci:v00008086d00000D16sv*sd*bc03sc*i*
alias:          pci:v00008086d00000D06sv*sd*bc03sc*i*
alias:          pci:v00008086d00000A2Esv*sd*bc03sc*i*
alias:          pci:v00008086d00000A1Esv*sd*bc03sc*i*
alias:          pci:v00008086d00000A0Esv*sd*bc03sc*i*
alias:          pci:v00008086d00000A26sv*sd*bc03sc*i*
alias:          pci:v00008086d00000A16sv*sd*bc03sc*i*
alias:          pci:v00008086d00000A06sv*sd*bc03sc*i*
alias:          pci:v00008086d00000C26sv*sd*bc03sc*i*
alias:          pci:v00008086d00000C16sv*sd*bc03sc*i*
alias:          pci:v00008086d00000C06sv*sd*bc03sc*i*
alias:          pci:v00008086d00000426sv*sd*bc03sc*i*
alias:          pci:v00008086d00000416sv*sd*bc03sc*i*
alias:          pci:v00008086d00000406sv*sd*bc03sc*i*
alias:          pci:v00008086d00000D2Esv*sd*bc03sc*i*
alias:          pci:v00008086d00000D1Esv*sd*bc03sc*i*
alias:          pci:v00008086d00000D0Esv*sd*bc03sc*i*
alias:          pci:v00008086d00000D2Bsv*sd*bc03sc*i*
alias:          pci:v00008086d00000D1Bsv*sd*bc03sc*i*
alias:          pci:v00008086d00000D0Bsv*sd*bc03sc*i*
alias:          pci:v00008086d00000D2Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000D1Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000D0Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000D22sv*sd*bc03sc*i*
alias:          pci:v00008086d00000D12sv*sd*bc03sc*i*
alias:          pci:v00008086d00000D02sv*sd*bc03sc*i*
alias:          pci:v00008086d00000A2Bsv*sd*bc03sc*i*
alias:          pci:v00008086d00000A1Bsv*sd*bc03sc*i*
alias:          pci:v00008086d00000A0Bsv*sd*bc03sc*i*
alias:          pci:v00008086d00000A2Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000A1Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000A0Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000A22sv*sd*bc03sc*i*
alias:          pci:v00008086d00000A12sv*sd*bc03sc*i*
alias:          pci:v00008086d00000A02sv*sd*bc03sc*i*
alias:          pci:v00008086d00000C2Esv*sd*bc03sc*i*
alias:          pci:v00008086d00000C1Esv*sd*bc03sc*i*
alias:          pci:v00008086d00000C0Esv*sd*bc03sc*i*
alias:          pci:v00008086d00000C2Bsv*sd*bc03sc*i*
alias:          pci:v00008086d00000C1Bsv*sd*bc03sc*i*
alias:          pci:v00008086d00000C0Bsv*sd*bc03sc*i*
alias:          pci:v00008086d00000C2Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000C1Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000C0Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000C22sv*sd*bc03sc*i*
alias:          pci:v00008086d00000C12sv*sd*bc03sc*i*
alias:          pci:v00008086d00000C02sv*sd*bc03sc*i*
alias:          pci:v00008086d0000042Esv*sd*bc03sc*i*
alias:          pci:v00008086d0000041Esv*sd*bc03sc*i*
alias:          pci:v00008086d0000040Esv*sd*bc03sc*i*
alias:          pci:v00008086d0000042Bsv*sd*bc03sc*i*
alias:          pci:v00008086d0000041Bsv*sd*bc03sc*i*
alias:          pci:v00008086d0000040Bsv*sd*bc03sc*i*
alias:          pci:v00008086d0000042Asv*sd*bc03sc*i*
alias:          pci:v00008086d0000041Asv*sd*bc03sc*i*
alias:          pci:v00008086d0000040Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000422sv*sd*bc03sc*i*
alias:          pci:v00008086d00000412sv*sd*bc03sc*i*
alias:          pci:v00008086d00000402sv*sd*bc03sc*i*
alias:          pci:v00008086d0000016Asv*sd*bc03sc*i*
alias:          pci:v00008086d0000015Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000162sv*sd*bc03sc*i*
alias:          pci:v00008086d00000152sv*sd*bc03sc*i*
alias:          pci:v00008086d00000166sv*sd*bc03sc*i*
alias:          pci:v00008086d00000156sv*sd*bc03sc*i*
alias:          pci:v00008086d0000016Asv0000152Dsd00008990bc03sc*i*
alias:          pci:v00008086d00000126sv*sd*bc03sc*i*
alias:          pci:v00008086d00000116sv*sd*bc03sc*i*
alias:          pci:v00008086d00000106sv*sd*bc03sc*i*
alias:          pci:v00008086d0000010Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000122sv*sd*bc03sc*i*
alias:          pci:v00008086d00000112sv*sd*bc03sc*i*
alias:          pci:v00008086d00000102sv*sd*bc03sc*i*
alias:          pci:v00008086d00000046sv*sd*bc03sc*i*
alias:          pci:v00008086d00000042sv*sd*bc03sc*i*
alias:          pci:v00008086d0000A011sv*sd*bc03sc*i*
alias:          pci:v00008086d0000A001sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E92sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E42sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E32sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E22sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E12sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E02sv*sd*bc03sc*i*
alias:          pci:v00008086d00002A42sv*sd*bc03sc*i*
alias:          pci:v00008086d00002A12sv*sd*bc03sc*i*
alias:          pci:v00008086d00002A02sv*sd*bc03sc*i*
alias:          pci:v00008086d000029D2sv*sd*bc03sc*i*
alias:          pci:v00008086d000029C2sv*sd*bc03sc*i*
alias:          pci:v00008086d000029B2sv*sd*bc03sc*i*
alias:          pci:v00008086d000029A2sv*sd*bc03sc*i*
alias:          pci:v00008086d00002992sv*sd*bc03sc*i*
alias:          pci:v00008086d00002982sv*sd*bc03sc*i*
alias:          pci:v00008086d00002972sv*sd*bc03sc*i*
alias:          pci:v00008086d000027AEsv*sd*bc03sc*i*
alias:          pci:v00008086d000027A2sv*sd*bc03sc*i*
alias:          pci:v00008086d00002772sv*sd*bc03sc*i*
alias:          pci:v00008086d00002592sv*sd*bc03sc*i*
alias:          pci:v00008086d0000258Asv*sd*bc03sc*i*
alias:          pci:v00008086d00002582sv*sd*bc03sc*i*
alias:          pci:v00008086d00002572sv*sd*bc03sc*i*
alias:          pci:v00008086d0000358Esv*sd*bc03sc*i*
alias:          pci:v00008086d00003582sv*sd*bc03sc*i*
alias:          pci:v00008086d00002562sv*sd*bc03sc*i*
alias:          pci:v00008086d00003577sv*sd*bc03sc*i*
depends:        drm_kms_helper,drm,video,i2c-algo-bit
intree:         Y
vermagic:       4.10.0-40-generic SMP mod_unload 
parm:           modeset:Use kernel modesetting [KMS] (0=disable, 1=on, -1=force vga console preference [default]) (int)
parm:           panel_ignore_lid:Override lid status (0=autodetect, 1=autodetect disabled [default], -1=force lid closed, -2=force lid open) (int)
parm:           semaphores:Use semaphores for inter-ring sync (default: -1 (use per-chip defaults)) (int)
parm:           enable_rc6:Enable power-saving render C-state 6. Different stages can be selected via bitmask values (0 = disable; 1 = enable rc6; 2 = enable deep rc6; 4 = enable deepest rc6). For example, 3 would enable rc6 and deep rc6, and 7 would enable everything. default: -1 (use per-chip default) (int)
parm:           enable_dc:Enable power-saving display C-states. (-1=auto [default]; 0=disable; 1=up to DC5; 2=up to DC6) (int)
parm:           enable_fbc:Enable frame buffer compression for power savings (default: -1 (use per-chip default)) (int)
parm:           lvds_channel_mode:Specify LVDS channel mode (0=probe BIOS [default], 1=single-channel, 2=dual-channel) (int)
parm:           lvds_use_ssc:Use Spread Spectrum Clock with panels [LVDS/eDP] (default: auto from VBT) (int)
parm:           vbt_sdvo_panel_type:Override/Ignore selection of SDVO panel mode in the VBT (-2=ignore, -1=auto [default], index in VBT BIOS table) (int)
parm:           reset:Attempt GPU resets (default: true) (bool)
parm:           error_capture:Record the GPU state following a hang. This information in /sys/class/drm/card<N>/error is vital for triaging and debugging hangs. (bool)
parm:           enable_hangcheck:Periodically check GPU activity for detecting hangs. WARNING: Disabling this can cause system wide hangs. (default: true) (bool)
parm:           enable_ppgtt:Override PPGTT usage. (-1=auto [default], 0=disabled, 1=aliasing, 2=full, 3=full with extended address space) (int)
parm:           enable_execlists:Override execlists usage. (-1=auto [default], 0=disabled, 1=enabled) (int)
parm:           enable_psr:Enable PSR (0=disabled, 1=enabled - link mode chosen per-platform, 2=force link-standby mode, 3=force link-off mode) Default: -1 (use per-chip default) (int)
parm:           alpha_support:Enable alpha quality driver support for latest hardware. See also CONFIG_DRM_I915_ALPHA_SUPPORT. (int)
parm:           disable_power_well:Disable display power wells when possible (-1=auto [default], 0=power wells always on, 1=power wells disabled when possible) (int)
parm:           enable_ips:Enable IPS (default: true) (int)
parm:           fastboot:Try to skip unnecessary mode sets at boot time (default: false) (bool)
parm:           prefault_disable:Disable page prefaulting for pread/pwrite/reloc (default:false). For developers only. (bool)
parm:           load_detect_test:Force-enable the VGA load detect code for testing (default:false). For developers only. (bool)
parm:           force_reset_modeset_test:Force a modeset during gpu reset for testing (default:false). For developers only. (bool)
parm:           invert_brightness:Invert backlight brightness (-1 force normal, 0 machine defaults, 1 force inversion), please report PCI device ID, subsystem vendor and subsystem device ID to dri-devel@lists.freedesktop.org, if your machine needs it. It will then be included in an upcoming module version. (int)
parm:           disable_display:Disable display (default: false) (bool)
parm:           enable_cmd_parser:Enable command parsing (1=enabled [default], 0=disabled) (int)
parm:           use_mmio_flip:use MMIO flips (-1=never, 0=driver discretion [default], 1=always) (int)
parm:           mmio_debug:Enable the MMIO debug code for the first N failures (default: off). This may negatively affect performance. (int)
parm:           verbose_state_checks:Enable verbose logs (ie. WARN_ON()) in case of unexpected hw state conditions. (bool)
parm:           nuclear_pageflip:Force atomic modeset functionality; asynchronous mode is not yet supported. (default: false). (bool)
parm:           edp_vswing:Ignore/Override vswing pre-emph table selection from VBT (0=use value from vbt [default], 1=low power swing(200mV),2=default swing(400mV)) (int)
parm:           enable_guc_loading:Enable GuC firmware loading (-1=auto, 0=never [default], 1=if available, 2=required) (int)
parm:           enable_guc_submission:Enable GuC submission (-1=auto, 0=never [default], 1=if available, 2=required) (int)
parm:           guc_log_level:GuC firmware logging level (-1:disabled (default), 0-3:enabled) (int)
parm:           enable_dp_mst:Enable multi-stream transport (MST) for new DisplayPort sinks. (default: true) (bool)
parm:           inject_load_failure:Force an error after a number of failure check points (0:disabled (default), N:force failure at the Nth failure check point) (uint)
parm:           enable_dpcd_backlight:Enable support for DPCD backlight control (default:false) (bool)
parm:           enable_gvt:Enable support for Intel GVT-g graphics virtualization host support(default:false) (bool)
```

I've been reading up a lot, and tried various things. As far as I can remember, the only thing I have in place that isn't standard is a new file,/etc/X11/xorg.conf which contains the lines...```
Section "Device"
Identifier "Card0"
Driver "intel"
Option "AccelMethod" "sna"
EndSection
```Beyond that, nothing I've tried so far has had any effect, so I have undone any changes I made, reverting back to a fairly stock standard Lubuntu installation. Any suggestions on how to get this video card working properly, so that it supports higher resolutions?

---

### Post by ajgreeny on 2017-11-21
Where did that **/etc/X11/xorg.conf** file come from? The Ubuntu family has not used such a file as default for a long time now so I presume you may have created it manually after reading something about this and following a guide.

Can you show the terminal output of ```
dpkg -s xserver-xorg-video-intel
```to check that the package is installed (it appears to be but let's check).

If all appears well with the installation of that, try editing the xorg.conf to ```
Option "AccelMethod" "UXA"
``` which can sometimes aid display problems in older hardware, even though I don't think that laptop is all that old.

---

### Post by robert_frittmann2 on 2017-11-21
Thanks for the reply, **ajgreeny**. The xorg.conf idea came from one of the many things I had tried from my own search prior to asking here for help. Heck, at first I wasn't even too sure which hardware was installed in this laptop, so I tried installing the Nvidia Radeon drivers, but that made no difference at all, haha.

The xorg.conf file did make some difference, but not really an improvement, as such. It reorganised the list of output devices in ARandR, moving the external VGA to the bottom of the list. I think it may have given me the 1280x800 option for the internal eDP1 display as well, because my desktops no longer lined up correctly, so I had to move the VGA display down slightly in ARandR, to match the new bottom of the eDP1 display. Beyond that, I don't really have anything better than the VESA resolutions.

dpkg -s xserver-xorg-video-intel
```
Package: xserver-xorg-video-intel
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 3211
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 2:2.99.917+git20170309-0ubuntu1
Provides: xorg-driver-video
Depends: libc6 (>= 2.17), libdrm-intel1 (>= 2.4.38), libdrm2 (>= 2.4.25), libpciaccess0 (>= 0.8.0+git20071002), libpixman-1-0 (>= 0.30.0), libudev1 (>= 183), libx11-6, libx11-xcb1, libxcb-dri2-0, libxcb-dri3-0, libxcb-sync1, libxcb-util1 (>= 0.4.0), libxcb1, libxcursor1 (>> 1.1.2), libxdamage1 (>= 1:1.1), libxext6, libxfixes3, libxinerama1, libxrandr2 (>= 2:1.2.99.3), libxrender1, libxshmfence1, libxss1, libxtst6, libxv1, libxvmc1, libxxf86vm1, xorg-video-abi-23, xserver-xorg-core (>= 2:1.18.99.901)
Description: X.Org X server -- Intel i8xx, i9xx display driver
 This package provides the driver for the Intel i8xx and i9xx family
 of chipsets, including i810, i815, i830, i845, i855, i865, i915, i945
 and i965 series chips.
 .
 This package also provides XvMC (XVideo Motion Compensation) drivers
 for i810/i815 and i9xx and newer chipsets.
 .
 This package is built from the X.org xf86-video-intel driver module.
 .
 The use of this driver is discouraged if your hw is new enough (ca.
 2007 and newer). You can try uninstalling this driver and let the
 server use it's builtin modesetting driver instead.
Homepage: https://www.x.org/
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
```

So, I did that, and it seemed to work fine. I then replace the "sna"with your suggested "UXA" in the xorg.conf file and rebooted. No immediate difference at first, but then it wanted to do some updates, including for libgles2-mesa, libdrm-nouveau2, libglapi-mesa, ibxatracker2, libegl1-mesa, libgbm1, samba-libs, libdrm-amdgpu1, libwayland-egl1-mesa, and lots of other mesa and radeon-related stuff. Just to be sure, I rebooted again after all the updates were installed.

The only noticeable difference this has made is that the internal eDP1 display has now also been moved to the bottom of the list in ARandR. I still don't have any additional resolutions to choose from.

---

### Post by QIII on 2017-11-21
Hello!

Please use the Forum default font, size and color unless it is clearly important to draw attention to a particular point in your posts.  Departure from the default can often be more of a distraction than a help.

Thanks!

---

### Post by robert_frittmann2 on 2017-11-21
@QIII, What is so wrong with displaying personal preference and style? It wasn't  distracting at all to me, and no-one else had complained. Is there a  particular rule against using different fonts and colours? If so, why  not disable those options in the interface, so that we can't  inadvertently break the rules? If I haven't broken any rules, then  please revert my posts to the way they were. Thanks.

---

