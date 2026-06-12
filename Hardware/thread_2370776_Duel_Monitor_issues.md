---
title: "Duel Monitor issues"
date: 2017-09-07
forum: Hardware
---

### Post by abasel on 2017-09-07
I was originally using a vanilla Debian install but have now change to Ubuntu

> No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial


While booting both screens display output. The moment the login screen appears my eternal Philips 273V goes blank with a "no cable connected" message. Sometimes it flashes back on and I can see the blue background of the gnome desktop for a split second. My laptop is a EliteBook 9470p.

Using the display settings I have tried all the resolution options for the external monitor and only 800x600 and lower showed anything on the external screen. 

$ sudo modinfo i915 returns
```
filename:       /lib/modules/4.10.0-33-generic/kernel/drivers/gpu/drm/i915/i915.ko
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
vermagic:       4.10.0-33-generic SMP mod_unload 
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
parm:           invert_brightness:Invert backlight brightness (-1 force normal, 0 machine defaults, 1 force inversion), please report PCI device ID, subsystem vendor and subsystem device ID to [email]dri-devel@lists.freedesktop.org[/email], if your machine needs it. It will then be included in an upcoming module version. (int)
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
abasel@lt-basel-a:~$ 

```

monitors.xml contains the following
```

<monitors version="1">
  <configuration>
    <clone>no</clone>
    <output name="HDMI-3">
      <vendor>PHL</vendor>
      <product>PHL 273V5</product>
      <serial>UK11634027907</serial>
      <width>1920</width>
      <height>1080</height>
      <rate>60</rate>
      <x>0</x>
      <y>0</y>
      <rotation>normal</rotation>
      <reflect_x>no</reflect_x>
      <reflect_y>no</reflect_y>
      <primary>no</primary>
      <presentation>no</presentation>
      <underscanning>no</underscanning>
    </output>
   <output name="LVDS-1">
      <vendor>LGD</vendor>
      <product>0x0335</product>
      <serial>0x00000000</serial>
      <width>1366</width>
      <height>768</height>
      <rate>59.973125457763672</rate>
      <x>1920</x>
      <y>312</y>
      <rotation>normal</rotation>
      <reflect_x>no</reflect_x>
      <reflect_y>no</reflect_y>
      <primary>yes</primary>
      <presentation>no</presentation>
      <underscanning>no</underscanning>
    </output>
  </configuration>
</monitors>

```

I have tried using [https://01.org/linuxgraphics/downloads/intel-graphics-update-tool-linux-os-v2.0.2]("https://01.org/linuxgraphics/downloads/intel-graphics-update-tool-linux-os-v2.0.2")[https://01.org/linuxgraphics/downloads/intel-graphics-update-tool-linux-os-v2.0.2]("https://01.org/linuxgraphics/downloads/intel-graphics-update-tool-linux-os-v2.0.2")

Lastly, even though the external monitor is black, the OS can still see it

$xrandr --listmonitors

$Monitors: 2
 0: +*LVDS-1 1366/310x768/174+1920+312  LVDS-1
 1: +HDMI-3 1920/598x1080/336+0+0  HDMI-3

---

