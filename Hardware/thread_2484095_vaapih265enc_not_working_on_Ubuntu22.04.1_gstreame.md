---
title: "vaapih265enc not working on Ubuntu22.04.1 gstreamer-1.0"
date: 2023-02-17
forum: Hardware
---

### Post by dxyzhou-tiger on 2023-02-17
Hi,


I  have Ubuntu 22.04.1 LTS, Kernel Version: 5.15.0-43-generic, and  gstreamer-1.0 installed on Intel 11th Gen Intel(R) Core(TM) i7-1185GRE @ 2.80GHz.

 using examples:


```
gst-launch-1.0 -ev videotestsrc num-buffers=60 ! timeoverlay ! vaapih265enc ! matroskamux ! filesink location=test.mkv
gst-launch-1.0 -ev videotestsrc num-buffers=60 ! timeoverlay ! vaapih265enc ! h265parse ! matroskamux ! filesink location=test.mkv
```
Got the following error:
```
Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...
Got  context from element 'vaapiencodeh265-0': gst.vaapi.Display=context,  gst.vaapi.Display=(GstVaapiDisplay)"\(GstVaapiDisplayWayland\)\  vaapidisplaywayland0",  gst.vaapi.Display.GObject=(GstObject)"\(GstVaapiDisplayWayland\)\  vaapidisplaywayland0";
/GstPipeline:pipeline0/GstVideoTestSrc:videotestsrc0.GstPad:src:  caps = video/x-raw, format=(string)Y410, width=(int)320,  height=(int)240, framerate=(fraction)30/1, multiview-mode=(string)mono,  pixel-aspect-ratio=(fraction)1/1, interlace-mode=(string)progressive
/GstPipeline:pipeline0/GstTimeOverlay:timeoverlay0.GstPad:src:  caps = video/x-raw, format=(string)Y410, width=(int)320,  height=(int)240, framerate=(fraction)30/1, multiview-mode=(string)mono,  pixel-aspect-ratio=(fraction)1/1, interlace-mode=(string)progressive
/GstPipeline:pipeline0/GstVaapiEncodeH265:vaapiencodeh265-0.GstPad:sink:  caps = video/x-raw, format=(string)Y410, width=(int)320,  height=(int)240, framerate=(fraction)30/1, multiview-mode=(string)mono,  pixel-aspect-ratio=(fraction)1/1, interlace-mode=(string)progressive
/GstPipeline:pipeline0/GstTimeOverlay:timeoverlay0.GstPad:video_sink:  caps = video/x-raw, format=(string)Y410, width=(int)320,  height=(int)240, framerate=(fraction)30/1, multiview-mode=(string)mono,  pixel-aspect-ratio=(fraction)1/1, interlace-mode=(string)progressive
ERROR: from element /GstPipeline:pipeline0/GstVideoTestSrc:videotestsrc0: Internal data stream error.
Additional debug info:
../libs/gst/base/gstbasesrc.c(3127): gst_base_src_loop (): /GstPipeline:pipeline0/GstVideoTestSrc:videotestsrc0:
streaming stopped, reason error (-5)
ERROR: pipeline doesn't want to preroll.
Setting pipeline to NULL ...
Freeing pipeline ...

 From the following i915 driver info:
 i915.guc_firmware_path=(null)
i915.huc_firmware_path=(null)
i915.dmc_firmware_path=(null)

```
 Not sure, the vaapih265 encoder error is related to the GUC and HUC firmware.```

  
 ==============================
 i915 gpu driver info:
Kernel: 5.15.0-43-generic x86_64
Driver: 20201103
Time: 1676494673 s 616282 us
Boottime: 5338 s 908448 us
Uptime: 5335 s 45996 us
Capture: 4296227012 jiffies; 0 ms ago
Reset count: 0
Suspend count: 0
Platform: TIGERLAKE
Subplatform: 0x1
PCI ID: 0x9a49
PCI Revision: 0x01
PCI Subsystem: 8086:9a49
IOMMU enabled?: 1
DMC loaded: yes
DMC fw version: 2.12
RPM wakelock: yes
PM suspended: no
GT awake: no
EIR: 0x00000000
IER: 0x00080000
GTIER[0]: 0x09090909
GTIER[1]: 0x09090909
GTIER[2]: 0x00000000
GTIER[3]: 0x00000000
GTIER[4]: 0x00000000
GTIER[5]: 0x00000000
PGTBL_ER: 0x00000000
FORCEWAKE: 0xffff0001
DERRMR: 0xffffffff
fence[0] = 00000000
fence[1] = 00000000
fence[2] = 00000000
fence[3] = 00000000
fence[4] = 00000000
fence[5] = 00000000
fence[6] = 00000000
fence[7] = 00000000
fence[8] = 13c603b00bc0001
fence[9] = 00000000
fence[10] = 1c0603b01400001
fence[11] = 244603b01c40001
fence[12] = 00000000
fence[13] = 00000000
fence[14] = 00000000
fence[15] = 00000000
fence[16] = 00000000
fence[17] = 00000000
fence[18] = 00000000
fence[19] = 00000000
fence[20] = 00000000
fence[21] = 00000000
fence[22] = 00000000
fence[23] = 00000000
fence[24] = 00000000
fence[25] = 00000000
fence[26] = 00000000
fence[27] = 00000000
fence[28] = 00000000
fence[29] = 00000000
fence[30] = 00000000
fence[31] = 00000000
FAULT_TLB_DATA: 0x00000000 0x0004e750
AUX_ERR_DBG: 0x00000000
SFC_DONE[0]: 0x000000ff
SFC_DONE[1]: 0x00000000
GAM_DONE: 0xffbfffff
GuC firmware: 
status: DISABLED
version: wanted 62.0, found 0.0
uCode: 0 bytes
RSA: 0 bytes
HuC firmware: 
status: DISABLED
version: wanted 7.9, found 0.0
uCode: 0 bytes
RSA: 0 bytes
available engines: 417
slice total: 1, mask=0001
subslice total: 6
slice0: 6 subslices, mask=0000003f
EU total: 96
EU per subslice: 16
has slice power gating: yes
has subslice power gating: no
has EU power gating: no
slice0: 6 subslice(s) (0x0000003f):
subslice0: 16 EUs (0xffff)
subslice1: 16 EUs (0xffff)
subslice2: 16 EUs (0xffff)
subslice3: 16 EUs (0xffff)
subslice4: 16 EUs (0xffff)
subslice5: 16 EUs (0xffff)
graphics version: 12
media version: 12
display version: 12
gt: 0
iommu: enabled
memory-regions: 5
page-sizes: 211000
platform: TIGERLAKE
ppgtt-size: 48
ppgtt-type: 2
dma_mask_size: 39
is_mobile: no
is_lp: no
require_force_probe: no
is_dgfx: no
has_64bit_reloc: yes
gpu_reset_clobbers_display: no
has_reset_engine: yes
has_global_mocs: yes
has_gt_uc: yes
has_l3_dpf: no
has_llc: yes
has_logical_ring_contexts: yes
has_logical_ring_elsq: yes
has_mslices: no
has_pooled_eu: no
has_rc6: yes
has_rc6p: no
has_rps: yes
has_runtime_pm: yes
has_snoop: no
has_coherent_ggtt: no
unfenced_needs_alignment: no
hws_needs_physical: no
cursor_needs_physical: no
has_cdclk_crawl: no
has_dmc: yes
has_ddi: yes
has_dp_mst: yes
has_dsb: no
has_dsc: yes
has_fbc: yes
has_fpga_dbg: yes
has_gmch: no
has_hdcp: yes
has_hotplug: yes
has_hti: no
has_ipc: yes
has_modular_fia: yes
has_overlay: no
has_psr: yes
has_psr_hw_tracking: yes
overlay_needs_physical: no
supports_tv: no
rawclk rate: 19200 kHz
Has logical contexts? yes
scheduler: 1f
i915.vbt_firmware=(null)
i915.modeset=-1
i915.lvds_channel_mode=0
i915.panel_use_ssc=-1
i915.vbt_sdvo_panel_type=-1
i915.enable_dc=-1
i915.enable_fbc=1
i915.enable_psr=-1
i915.psr_safest_params=no
i915.enable_psr2_sel_fetch=no
i915.disable_power_well=1
i915.enable_ips=1
i915.invert_brightness=0
i915.enable_guc=0
i915.guc_log_level=-1
i915.guc_firmware_path=(null)
i915.huc_firmware_path=(null)
i915.dmc_firmware_path=(null)
i915.mmio_debug=0
i915.edp_vswing=0
i915.reset=3
i915.inject_probe_failure=0
i915.fastboot=-1
i915.enable_dpcd_backlight=-1
i915.force_probe=
i915.fake_lmem_start=0
i915.request_timeout_ms=20000
i915.enable_hangcheck=yes
i915.load_detect_test=no
i915.force_reset_modeset_test=no
i915.error_capture=yes
i915.disable_display=no
i915.verbose_state_checks=yes
i915.nuclear_pageflip=no
i915.enable_dp_mst=yes
i915.enable_gvt=no
```

  
 Thank you,
Tiger

---

