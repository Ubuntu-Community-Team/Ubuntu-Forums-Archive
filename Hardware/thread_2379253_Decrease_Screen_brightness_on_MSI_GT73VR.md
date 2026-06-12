---
title: "Decrease Screen brightness on MSI GT73VR"
date: 2017-12-03
forum: Hardware
---

### Post by Paloseco on 2017-12-03
I have a MSI GT73VR, and whenever I boot Ubuntu 17.10, the screen brightness is at its maximum. Would like to decrease it because kills my eyes. The notebook has the following hardware:
[LIST]
[*]Intel CPU 6700HQ
[*]Nvidia GTX 1080 + integrated graphics from the CPU
[*]120Hz refresh rate display
[*]SSD + Spinning hard drive
[*]BIOS with LEGACY or UEFI modes
[/LIST]

These are several commands and its output:
```
sudo lspci -vnn | grep VGA -A 12
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP104M [GeForce GTX 1080 Mobile] [10de:1be0] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Micro-Star International Co., Ltd. [MSI] GP104M [GeForce GTX 1080 Mobile] [1462:11bb]
	Flags: bus master, fast devsel, latency 0, IRQ 125
	Memory at db000000 (32-bit, non-prefetchable) [size=16M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Memory at c0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at e000 [size=128]
	Expansion ROM at 000c0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [250] Latency Tolerance Reporting
```

```
sudo lshw -numeric -C display
  *-display                 
       description: VGA compatible controller
       product: GP104M [GeForce GTX 1080 Mobile] [10DE:1BE0]
       vendor: NVIDIA Corporation [10DE]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:125 memory:db000000-dbffffff memory:b0000000-bfffffff memory:c0000000-c1ffffff ioport:e000(size=128) memory:c0000-dffff
```

```
sudo lshw -c video | grep configuration
       configuration: driver=nouveau latency=0
```

```
sudo modinfo nouveau
filename:       /lib/modules/4.13.0-17-generic/kernel/drivers/gpu/drm/nouveau/nouveau.ko
firmware:       nvidia/gp100/gr/sw_method_init.bin
firmware:       nvidia/gp100/gr/sw_bundle_init.bin
firmware:       nvidia/gp100/gr/sw_nonctx.bin
firmware:       nvidia/gp100/gr/sw_ctx.bin
firmware:       nvidia/gp100/gr/gpccs_sig.bin
firmware:       nvidia/gp100/gr/gpccs_data.bin
firmware:       nvidia/gp100/gr/gpccs_inst.bin
firmware:       nvidia/gp100/gr/gpccs_bl.bin
firmware:       nvidia/gp100/gr/fecs_sig.bin
firmware:       nvidia/gp100/gr/fecs_data.bin
firmware:       nvidia/gp100/gr/fecs_inst.bin
firmware:       nvidia/gp100/gr/fecs_bl.bin
firmware:       nvidia/gp100/acr/ucode_unload.bin
firmware:       nvidia/gp100/acr/ucode_load.bin
firmware:       nvidia/gp100/acr/bl.bin
firmware:       nvidia/gm206/gr/sw_method_init.bin
firmware:       nvidia/gm206/gr/sw_bundle_init.bin
firmware:       nvidia/gm206/gr/sw_nonctx.bin
firmware:       nvidia/gm206/gr/sw_ctx.bin
firmware:       nvidia/gm206/gr/gpccs_sig.bin
firmware:       nvidia/gm206/gr/gpccs_data.bin
firmware:       nvidia/gm206/gr/gpccs_inst.bin
firmware:       nvidia/gm206/gr/gpccs_bl.bin
firmware:       nvidia/gm206/gr/fecs_sig.bin
firmware:       nvidia/gm206/gr/fecs_data.bin
firmware:       nvidia/gm206/gr/fecs_inst.bin
firmware:       nvidia/gm206/gr/fecs_bl.bin
firmware:       nvidia/gm206/acr/ucode_unload.bin
firmware:       nvidia/gm206/acr/ucode_load.bin
firmware:       nvidia/gm206/acr/bl.bin
firmware:       nvidia/gm204/gr/sw_method_init.bin
firmware:       nvidia/gm204/gr/sw_bundle_init.bin
firmware:       nvidia/gm204/gr/sw_nonctx.bin
firmware:       nvidia/gm204/gr/sw_ctx.bin
firmware:       nvidia/gm204/gr/gpccs_sig.bin
firmware:       nvidia/gm204/gr/gpccs_data.bin
firmware:       nvidia/gm204/gr/gpccs_inst.bin
firmware:       nvidia/gm204/gr/gpccs_bl.bin
firmware:       nvidia/gm204/gr/fecs_sig.bin
firmware:       nvidia/gm204/gr/fecs_data.bin
firmware:       nvidia/gm204/gr/fecs_inst.bin
firmware:       nvidia/gm204/gr/fecs_bl.bin
firmware:       nvidia/gm204/acr/ucode_unload.bin
firmware:       nvidia/gm204/acr/ucode_load.bin
firmware:       nvidia/gm204/acr/bl.bin
firmware:       nvidia/gm200/gr/sw_method_init.bin
firmware:       nvidia/gm200/gr/sw_bundle_init.bin
firmware:       nvidia/gm200/gr/sw_nonctx.bin
firmware:       nvidia/gm200/gr/sw_ctx.bin
firmware:       nvidia/gm200/gr/gpccs_sig.bin
firmware:       nvidia/gm200/gr/gpccs_data.bin
firmware:       nvidia/gm200/gr/gpccs_inst.bin
firmware:       nvidia/gm200/gr/gpccs_bl.bin
firmware:       nvidia/gm200/gr/fecs_sig.bin
firmware:       nvidia/gm200/gr/fecs_data.bin
firmware:       nvidia/gm200/gr/fecs_inst.bin
firmware:       nvidia/gm200/gr/fecs_bl.bin
firmware:       nvidia/gm200/acr/ucode_unload.bin
firmware:       nvidia/gm200/acr/ucode_load.bin
firmware:       nvidia/gm200/acr/bl.bin
firmware:       nvidia/gm20b/pmu/sig.bin
firmware:       nvidia/gm20b/pmu/image.bin
firmware:       nvidia/gm20b/pmu/desc.bin
firmware:       nvidia/gm20b/gr/sw_method_init.bin
firmware:       nvidia/gm20b/gr/sw_bundle_init.bin
firmware:       nvidia/gm20b/gr/sw_nonctx.bin
firmware:       nvidia/gm20b/gr/sw_ctx.bin
firmware:       nvidia/gm20b/gr/gpccs_data.bin
firmware:       nvidia/gm20b/gr/gpccs_inst.bin
firmware:       nvidia/gm20b/gr/fecs_sig.bin
firmware:       nvidia/gm20b/gr/fecs_data.bin
firmware:       nvidia/gm20b/gr/fecs_inst.bin
firmware:       nvidia/gm20b/gr/fecs_bl.bin
firmware:       nvidia/gm20b/acr/ucode_load.bin
firmware:       nvidia/gm20b/acr/bl.bin
firmware:       nvidia/gp107/sec2/sig.bin
firmware:       nvidia/gp107/sec2/image.bin
firmware:       nvidia/gp107/sec2/desc.bin
firmware:       nvidia/gp107/nvdec/scrubber.bin
firmware:       nvidia/gp107/gr/sw_method_init.bin
firmware:       nvidia/gp107/gr/sw_bundle_init.bin
firmware:       nvidia/gp107/gr/sw_nonctx.bin
firmware:       nvidia/gp107/gr/sw_ctx.bin
firmware:       nvidia/gp107/gr/gpccs_sig.bin
firmware:       nvidia/gp107/gr/gpccs_data.bin
firmware:       nvidia/gp107/gr/gpccs_inst.bin
firmware:       nvidia/gp107/gr/gpccs_bl.bin
firmware:       nvidia/gp107/gr/fecs_sig.bin
firmware:       nvidia/gp107/gr/fecs_data.bin
firmware:       nvidia/gp107/gr/fecs_inst.bin
firmware:       nvidia/gp107/gr/fecs_bl.bin
firmware:       nvidia/gp107/acr/ucode_unload.bin
firmware:       nvidia/gp107/acr/ucode_load.bin
firmware:       nvidia/gp107/acr/unload_bl.bin
firmware:       nvidia/gp107/acr/bl.bin
firmware:       nvidia/gp106/sec2/sig.bin
firmware:       nvidia/gp106/sec2/image.bin
firmware:       nvidia/gp106/sec2/desc.bin
firmware:       nvidia/gp106/nvdec/scrubber.bin
firmware:       nvidia/gp106/gr/sw_method_init.bin
firmware:       nvidia/gp106/gr/sw_bundle_init.bin
firmware:       nvidia/gp106/gr/sw_nonctx.bin
firmware:       nvidia/gp106/gr/sw_ctx.bin
firmware:       nvidia/gp106/gr/gpccs_sig.bin
firmware:       nvidia/gp106/gr/gpccs_data.bin
firmware:       nvidia/gp106/gr/gpccs_inst.bin
firmware:       nvidia/gp106/gr/gpccs_bl.bin
firmware:       nvidia/gp106/gr/fecs_sig.bin
firmware:       nvidia/gp106/gr/fecs_data.bin
firmware:       nvidia/gp106/gr/fecs_inst.bin
firmware:       nvidia/gp106/gr/fecs_bl.bin
firmware:       nvidia/gp106/acr/ucode_unload.bin
firmware:       nvidia/gp106/acr/ucode_load.bin
firmware:       nvidia/gp106/acr/unload_bl.bin
firmware:       nvidia/gp106/acr/bl.bin
firmware:       nvidia/gp104/sec2/sig.bin
firmware:       nvidia/gp104/sec2/image.bin
firmware:       nvidia/gp104/sec2/desc.bin
firmware:       nvidia/gp104/nvdec/scrubber.bin
firmware:       nvidia/gp104/gr/sw_method_init.bin
firmware:       nvidia/gp104/gr/sw_bundle_init.bin
firmware:       nvidia/gp104/gr/sw_nonctx.bin
firmware:       nvidia/gp104/gr/sw_ctx.bin
firmware:       nvidia/gp104/gr/gpccs_sig.bin
firmware:       nvidia/gp104/gr/gpccs_data.bin
firmware:       nvidia/gp104/gr/gpccs_inst.bin
firmware:       nvidia/gp104/gr/gpccs_bl.bin
firmware:       nvidia/gp104/gr/fecs_sig.bin
firmware:       nvidia/gp104/gr/fecs_data.bin
firmware:       nvidia/gp104/gr/fecs_inst.bin
firmware:       nvidia/gp104/gr/fecs_bl.bin
firmware:       nvidia/gp104/acr/ucode_unload.bin
firmware:       nvidia/gp104/acr/ucode_load.bin
firmware:       nvidia/gp104/acr/unload_bl.bin
firmware:       nvidia/gp104/acr/bl.bin
firmware:       nvidia/gp102/sec2/sig.bin
firmware:       nvidia/gp102/sec2/image.bin
firmware:       nvidia/gp102/sec2/desc.bin
firmware:       nvidia/gp102/nvdec/scrubber.bin
firmware:       nvidia/gp102/gr/sw_method_init.bin
firmware:       nvidia/gp102/gr/sw_bundle_init.bin
firmware:       nvidia/gp102/gr/sw_nonctx.bin
firmware:       nvidia/gp102/gr/sw_ctx.bin
firmware:       nvidia/gp102/gr/gpccs_sig.bin
firmware:       nvidia/gp102/gr/gpccs_data.bin
firmware:       nvidia/gp102/gr/gpccs_inst.bin
firmware:       nvidia/gp102/gr/gpccs_bl.bin
firmware:       nvidia/gp102/gr/fecs_sig.bin
firmware:       nvidia/gp102/gr/fecs_data.bin
firmware:       nvidia/gp102/gr/fecs_inst.bin
firmware:       nvidia/gp102/gr/fecs_bl.bin
firmware:       nvidia/gp102/acr/ucode_unload.bin
firmware:       nvidia/gp102/acr/ucode_load.bin
firmware:       nvidia/gp102/acr/unload_bl.bin
firmware:       nvidia/gp102/acr/bl.bin
firmware:       nvidia/gp10b/pmu/sig.bin
firmware:       nvidia/gp10b/pmu/image.bin
firmware:       nvidia/gp10b/pmu/desc.bin
firmware:       nvidia/gp10b/gr/sw_method_init.bin
firmware:       nvidia/gp10b/gr/sw_bundle_init.bin
firmware:       nvidia/gp10b/gr/sw_nonctx.bin
firmware:       nvidia/gp10b/gr/sw_ctx.bin
firmware:       nvidia/gp10b/gr/gpccs_sig.bin
firmware:       nvidia/gp10b/gr/gpccs_data.bin
firmware:       nvidia/gp10b/gr/gpccs_inst.bin
firmware:       nvidia/gp10b/gr/gpccs_bl.bin
firmware:       nvidia/gp10b/gr/fecs_sig.bin
firmware:       nvidia/gp10b/gr/fecs_data.bin
firmware:       nvidia/gp10b/gr/fecs_inst.bin
firmware:       nvidia/gp10b/gr/fecs_bl.bin
firmware:       nvidia/gp10b/acr/ucode_load.bin
firmware:       nvidia/gp10b/acr/bl.bin
license:        GPL and additional rights
description:    nVidia Riva/TNT/GeForce/Quadro/Tesla
author:         Nouveau Project
srcversion:     69FF59065FAB5594E391F02
alias:          pci:v000012D2d*sv*sd*bc03sc*i*
alias:          pci:v000010DEd*sv*sd*bc03sc*i*
depends:        drm,drm_kms_helper,ttm,mxm-wmi,wmi,video,i2c-algo-bit
intree:         Y
name:           nouveau
vermagic:       4.13.0-17-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           tv_norm:Default TV norm.
		Supported: PAL, PAL-M, PAL-N, PAL-Nc, NTSC-M, NTSC-J,
			hd480i, hd480p, hd576i, hd576p, hd720p, hd1080i.
		Default: PAL
		*NOTE* Ignored for cards with external TV encoders. (charp)
parm:           vram_pushbuf:Create DMA push buffers in VRAM (int)
parm:           nofbaccel:Disable fbcon acceleration (int)
parm:           mst:Enable DisplayPort multi-stream (default: enabled) (int)
parm:           atomic:Expose atomic ioctl (default: disabled) (int)
parm:           tv_disable:Disable TV-out detection (int)
parm:           ignorelid:Ignore ACPI lid status (int)
parm:           duallink:Allow dual-link TMDS (default: enabled) (int)
parm:           hdmimhz:Force a maximum HDMI pixel clock (in MHz) (int)
parm:           config:option string to pass to driver core (charp)
parm:           debug:debug string to pass to driver core (charp)
parm:           noaccel:disable kernel/abi16 acceleration (int)
parm:           modeset:enable driver (default: auto, 0 = disabled, 1 = enabled, 2 = headless) (int)
parm:           runpm:disable (0), force enable (1), optimus only default (-1) (int)
```

```
glxinfo | grep OpenGL
OpenGL vendor string: nouveau
OpenGL renderer string: NV134
OpenGL core profile version string: 4.3 (Core Profile) Mesa 17.2.2
OpenGL core profile shading language version string: 4.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 17.2.2
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.1 Mesa 17.2.2
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10
OpenGL ES profile extensions:
```

```
inxi -G
Graphics:  Card: NVIDIA GP104M [GeForce GTX 1080 Mobile]
           Display Server: wayland (X.Org 1.19.5 ) drivers: (unloaded: fbdev,vesa) FAILED: modesetting
           Resolution: 1920x1080@119.93hz
           OpenGL: renderer: NV134 version: 4.3 Mesa 17.2.2
```

When I try to open steam shows this error:

```
steam
Running Steam on ubuntu 17.10 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0)
libGL error: unable to load driver: nouveau_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: nouveau
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast

```

This is a screenshot of the additional drivers from Software & Updates on Synaptic Package Manager:

[IMG]http://oi64.tinypic.com/25jd1lj.jpg[/IMG]

Trying to change the brightness manually just fails:
```
cat /sys/class/backlight/acpi_video0/max_brightness 
100
sudo echo 10 | sudo tee /sys/class/backlight/acpi_video0/actual_brightness 
tee: /sys/class/backlight/acpi_video0/actual_brightness: Permission denied
10
```

Unigine Heaven Benchmark 4.0 scores with the nouveau drivers on Ubuntu, nVidia drivers on Windows, and with discrete graphics card both:
[LIST]
[*]Ubuntu with mentioned settings: 343
[*]Windows 10: 4275
[/LIST]

---

### Post by Paloseco on 2017-12-05
Ok, I've found a way to workaround it and get brightness control working.

First, you need to use the physical button to switch from discrete graphics card to the integrated one. Use the button called GPU Graphics Switch. You need to use Microsoft Windows 10 for this and have MSI SCM (MSI System Control Manager) software installed. After clicking the button, you will be prompted to restart. Just after powering off, the discrete graphics card will be disabled until you click the button again from Windows. Even if you enter the BIOS or boot another operating system, the state of the graphics configuration will be preserved, so great to run linux now.

[IMG]http://oi63.tinypic.com/s2qgp1.jpg[/IMG]

[IMG]http://oi64.tinypic.com/34ir5w5.jpg[/IMG]

When clicking the GPU switcher button from Linux, this is the dmesg output:
```
[dic 5 12:23] atkbd serio0: Unknown key pressed (translated set 2, code 0x95 on isa0060/serio0).
[  +0,000005] atkbd serio0: Use 'setkeycodes e015 <keycode>' to make it known.
[  +0,002456] atkbd serio0: Unknown key released (translated set 2, code 0x95 on isa0060/serio0).
[  +0,000005] atkbd serio0: Use 'setkeycodes e015 <keycode>' to make it known.
```

Now, repeating the previous commands, this is the output:

```
sudo lspci -vnn | grep VGA -A 12
00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 530 [8086:191b] (rev 06) (prog-if 00 [VGA controller])
        Subsystem: Micro-Star International Co., Ltd. [MSI] HD Graphics 530 [1462:11b1]
        Flags: bus master, fast devsel, latency 0, IRQ 132
        Memory at db000000 (64-bit, non-prefetchable) [size=16M]
        Memory at 90000000 (64-bit, prefetchable) [size=256M]
        I/O ports at f000 [size=64]
        [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
        Capabilities: [40] Vendor Specific Information: Len=0c <?>
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [ac] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [d0] Power Management version 2
        Capabilities: [100] Process Address Space ID (PASID)
        Capabilities: [200] Address Translation Service (ATS)
```

```
sudo lshw -numeric -C display
  *-display                 
       description: VGA compatible controller
       product: HD Graphics 530 [8086:191B]
       vendor: Intel Corporation [8086]
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:132 memory:db000000-dbffffff memory:90000000-9fffffff ioport:f000(size=64) memory:c0000-dffff

```

```
sudo lshw -c video | grep configuration
       configuration: driver=i915 latency=0

```

```
sudo modinfo i915
filename:       /lib/modules/4.13.0-17-generic/kernel/drivers/gpu/drm/i915/i915.ko
license:        GPL and additional rights
description:    Intel Graphics
author:         Intel Corporation
author:         Tungsten Graphics, Inc.
firmware:       i915/bxt_dmc_ver1_07.bin
firmware:       i915/skl_dmc_ver1_26.bin
firmware:       i915/kbl_dmc_ver1_01.bin
firmware:       i915/skl_guc_ver6_1.bin
firmware:       i915/kbl_huc_ver02_00_1810.bin
firmware:       i915/bxt_huc_ver01_07_1398.bin
firmware:       i915/skl_huc_ver01_07_1398.bin
srcversion:     79894C129D5D79DF7A009CA
alias:          pci:v00008086d00005A79sv*sd*bc03sc*i*
alias:          pci:v00008086d00005A71sv*sd*bc03sc*i*
alias:          pci:v00008086d00005A49sv*sd*bc03sc*i*
alias:          pci:v00008086d00005A41sv*sd*bc03sc*i*
alias:          pci:v00008086d00005A59sv*sd*bc03sc*i*
alias:          pci:v00008086d00005A51sv*sd*bc03sc*i*
alias:          pci:v00008086d00005A4Asv*sd*bc03sc*i*
alias:          pci:v00008086d00005A42sv*sd*bc03sc*i*
alias:          pci:v00008086d00005A5Asv*sd*bc03sc*i*
alias:          pci:v00008086d00005A52sv*sd*bc03sc*i*
alias:          pci:v00008086d00003EA5sv*sd*bc03sc*i*
alias:          pci:v00008086d00003EA8sv*sd*bc03sc*i*
alias:          pci:v00008086d00003EA7sv*sd*bc03sc*i*
alias:          pci:v00008086d00003EA6sv*sd*bc03sc*i*
alias:          pci:v00008086d00003E94sv*sd*bc03sc*i*
alias:          pci:v00008086d00003E9Bsv*sd*bc03sc*i*
alias:          pci:v00008086d00003E96sv*sd*bc03sc*i*
alias:          pci:v00008086d00003E92sv*sd*bc03sc*i*
alias:          pci:v00008086d00003E91sv*sd*bc03sc*i*
alias:          pci:v00008086d00003E93sv*sd*bc03sc*i*
alias:          pci:v00008086d00003E90sv*sd*bc03sc*i*
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
alias:          pci:v00008086d00003185sv*sd*bc03sc*i*
alias:          pci:v00008086d00003184sv*sd*bc03sc*i*
alias:          pci:v00008086d00005A85sv*sd*bc03sc*i*
alias:          pci:v00008086d00005A84sv*sd*bc03sc*i*
alias:          pci:v00008086d00001A85sv*sd*bc03sc*i*
alias:          pci:v00008086d00001A84sv*sd*bc03sc*i*
alias:          pci:v00008086d00000A84sv*sd*bc03sc*i*
alias:          pci:v00008086d0000193Asv*sd*bc03sc*i*
alias:          pci:v00008086d0000192Asv*sd*bc03sc*i*
alias:          pci:v00008086d0000193Dsv*sd*bc03sc*i*
alias:          pci:v00008086d0000193Bsv*sd*bc03sc*i*
alias:          pci:v00008086d00001932sv*sd*bc03sc*i*
alias:          pci:v00008086d0000192Dsv*sd*bc03sc*i*
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
name:           i915
vermagic:       4.13.0-17-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
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
parm:           alpha_support:Enable alpha quality driver support for latest hardware. See also CONFIG_DRM_I915_ALPHA_SUPPORT. (bool)
parm:           disable_power_well:Disable display power wells when possible (-1=auto [default], 0=power wells always on, 1=power wells disabled when possible) (int)
parm:           enable_ips:Enable IPS (default: true) (int)
parm:           fastboot:Try to skip unnecessary mode sets at boot time (default: false) (bool)
parm:           prefault_disable:Disable page prefaulting for pread/pwrite/reloc (default:false). For developers only. (bool)
parm:           load_detect_test:Force-enable the VGA load detect code for testing (default:false). For developers only. (bool)
parm:           force_reset_modeset_test:Force a modeset during gpu reset for testing (default:false). For developers only. (bool)
parm:           invert_brightness:Invert backlight brightness (-1 force normal, 0 machine defaults, 1 force inversion), please report PCI device ID, subsystem vendor and subsystem device ID to dri-devel@lists.freedesktop.org, if your machine needs it. It will then be included in an upcoming module version. (int)
parm:           disable_display:Disable display (default: false) (bool)
parm:           enable_cmd_parser:Enable command parsing (true=enabled [default], false=disabled) (bool)
parm:           use_mmio_flip:use MMIO flips (-1=never, 0=driver discretion [default], 1=always) (int)
parm:           mmio_debug:Enable the MMIO debug code for the first N failures (default: off). This may negatively affect performance. (int)
parm:           verbose_state_checks:Enable verbose logs (ie. WARN_ON()) in case of unexpected hw state conditions. (bool)
parm:           nuclear_pageflip:Force enable atomic functionality on platforms that don't have full support yet. (bool)
parm:           edp_vswing:Ignore/Override vswing pre-emph table selection from VBT (0=use value from vbt [default], 1=low power swing(200mV),2=default swing(400mV)) (int)
parm:           enable_guc_loading:Enable GuC firmware loading (-1=auto, 0=never [default], 1=if available, 2=required) (int)
parm:           enable_guc_submission:Enable GuC submission (-1=auto, 0=never [default], 1=if available, 2=required) (int)
parm:           guc_log_level:GuC firmware logging level (-1:disabled (default), 0-3:enabled) (int)
parm:           guc_firmware_path:GuC firmware path to use instead of the default one (charp)
parm:           huc_firmware_path:HuC firmware path to use instead of the default one (charp)
parm:           enable_dp_mst:Enable multi-stream transport (MST) for new DisplayPort sinks. (default: true) (bool)
parm:           inject_load_failure:Force an error after a number of failure check points (0:disabled (default), N:force failure at the Nth failure check point) (uint)
parm:           enable_dpcd_backlight:Enable support for DPCD backlight control (default:false) (bool)
parm:           enable_gvt:Enable support for Intel GVT-g graphics virtualization host support(default:false) (bool)
```

```
glxinfo | grep OpenGL
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) HD Graphics 530 (Skylake GT2) 
OpenGL core profile version string: 4.5 (Core Profile) Mesa 17.2.2
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 17.2.2
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 Mesa 17.2.2
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:

```

```
inxi -G
Graphics:  Card: Intel HD Graphics 530
           Display Server: wayland (X.Org 1.19.5 ) drivers: (unloaded: fbdev,vesa) FAILED: modesetting
           Resolution: 1920x1080@119.93hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 530 (Skylake GT2) version: 4.5 Mesa 17.2.2
```

With integrated graphics, Unigine Heaven Benchmark 4.0 scores are:
- Ubuntu: 274
- Windows 10: 246

Related thread on Gentoo forums:
[Writing to SMBios]("https://forums.gentoo.org/viewtopic-p-7808870.html")

---

### Post by Paloseco on 2017-12-16
I've found that the problem is with Unity. If you use KDE Plasma, the Fn hardware keys to increase/decrease screen brightness work out of the box. With both nvidia proprietary and nouveau drivers.

---

