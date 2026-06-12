---
title: "Ubuntu 16.04.2 i386 (32bit) and RX480 - amdgpu unloading"
date: 2017-08-02
forum: Hardware
---

### Post by zpepa on 2017-08-02
I've upgraded my old system and amdgpu is not loading and when forced, then it's uloading:

```
[    51.082] (II) LoadModule: "amdgpu"
[    51.082] (II) Loading /usr/lib/xorg/modules/drivers/amdgpu_drv.so
[    54.834] (II) Module amdgpu: vendor="X.Org Foundation"
[    54.834]     compiled for 1.18.4, module version = 1.1.2
[    54.834]     Module class: X.Org Video Driver
[    54.834]     ABI class: X.Org Video Driver, version 20.0
[    54.834] (II) AMDGPU: Driver for AMD Radeon chipsets: OLAND, OLAND, OLAND, OLAND,
    OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
    OLAND, OLAND, OLAND, HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, HAINAN,
    TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, PITCAIRN, BONAIRE,
    BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
    BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
    MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
    MULLINS, MULLINS, MULLINS, MULLINS, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
    HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, TOPAZ, TOPAZ, TOPAZ,
    TOPAZ, TOPAZ, TONGA, TONGA, TONGA, TONGA, TONGA, TONGA, TONGA, TONGA,
    TONGA, CARRIZO, CARRIZO, CARRIZO, CARRIZO, CARRIZO, FIJI, STONEY,
    POLARIS11, POLARIS11, POLARIS11, POLARIS11, POLARIS11, POLARIS11,
    POLARIS11, POLARIS11, POLARIS11, POLARIS10, POLARIS10, POLARIS10,
    POLARIS10, POLARIS10, POLARIS10, POLARIS10, POLARIS10, POLARIS10,
    POLARIS10, POLARIS10
[    54.840] (II) [KMS] drm report modesetting isn't supported.
[    54.840] (EE) Screen 0 deleted because of no matching config section.
[    54.840] (II) UnloadModule: "amdgpu"
```

gpu-manager-log:
```
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /run/u-d-c-fglrx-was-loaded file
Looking for fglrx modules in /lib/modules/4.4.0-87-generic/updates/dkms
Looking for nvidia modules in /lib/modules/4.4.0-87-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is fglrx blacklisted? no
Is intel loaded? no
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is nouveau loaded? no
Is nouveau blacklisted? no
Is fglrx kernel module available? no
Is nvidia kernel module available? no
Vendor/Device Id: 1002:67df
BusID "PCI:1@0:0:0"
Is boot vga? yes
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver. Skipping...
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Does it require offloading? no
last cards number = 0
Has amd? no
Has intel? no
Has nvidia? no
How many cards? 0
Has the system changed? No
main_arch_path i386-linux-gnu, other_arch_path x86_64-linux-gnu
Current alternative: /usr/lib/i386-linux-gnu/mesa/ld.so.conf
Current core alternative: (null)
Current egl alternative: /usr/lib/i386-linux-gnu/mesa-egl/ld.so.conf
Is nvidia enabled? no
Is nvidia egl enabled? no
Is fglrx enabled? no
Is mesa enabled? yes
Is mesa egl enabled? yes
Is pxpress enabled? no
Is prime enabled? no
Is prime egl enabled? no
Is nvidia available? no
Is nvidia egl available? no
Is fglrx available? no
Is fglrx-core available? no
Is mesa available? yes
Is mesa egl available? yes
Is pxpress available? no
Is prime available? no
Is prime egl available? no
```

When I do "lsmod", there is a ati_agp module loaded.
The main problem is I have a 4k monitor but the maximum resolution is only 1920x1080.

Here is some background: the PC was originally running Ubuntu 12.04 and a Radeon HD6950 (fglrx) connected to a Full HD monitor.
I have upgraded the graphics to a RX480 and a 4k monitor.
I uninstalled and purged the fglrx drivers, then I upgraded Ubuntu to 14.04 and then to 16.04.

Amdgpu-pro is not an option because it is for 64 bit systems only.

What I have tried so far:
1) Install amdgpu-pro, failed because amdgpu-pro-lib32_17.10-450821_i386 is missing. I kind of expected it but it was worth a shot.
2) Forced to load the amdgpu adding it to /etc/initramfs-tools/modules and using update-initramfs -u
3) Blacklisted ati, ati_agp, ati-agp, radeon in /etc/modprobe.d/blacklist.conf
4) added 20-amdgpu.conf in /usr/share/X11/xorg.conf.d/
```
Section "Device"
    Identifier "AMD"
    Driver "amdgpu"
EndSection
```
5) tried to add nomodeset in grub
6) tried to boot the ubuntu-mate-16.04.2-desktop-i386.iso DVD - I've got "out of range" on the monitor

Did I miss something or is it a bug?

Any ideas what to try or how to solve this problem?

If there is any additional information needed, please let me know.


EDIT: I got two new ideas:
1) Would HWE Stack [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) help?

2) Alternative drivers [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers) ?


EDIT 2:
I've tried the HWE, the result is the amdgpu is not unloading but the display is random pixels, there seem to be some bug(s) in the amdgpu:
```
dmesg |grep amdgpu
[    3.510531] [drm] amdgpu kernel modesetting enabled.
[    3.510561] fb: switching to amdgpudrmfb from VESA VGA
[    3.510871] amdgpu 0000:01:00.0: Invalid PCI ROM header signature: expecting 0xaa55, got 0xffff
[    3.511886] amdgpu 0000:01:00.0: VRAM: 8192M 0x0000000000000000 - 0x00000001FFFFFFFF (8192M used)
[    3.511887] amdgpu 0000:01:00.0: GTT: 8192M 0x0000000200000000 - 0x00000003FFFFFFFF
[    3.511971] [drm] amdgpu: 8192M of VRAM memory ready
[    3.511971] [drm] amdgpu: 8192M of GTT memory ready.
[    3.513195] amdgpu 0000:01:00.0: amdgpu: using MSI.
[    3.513209] [drm] amdgpu: irq initialized.
[    3.513368] amdgpu: powerplay initialized
[    3.513989] amdgpu 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000200000008, cpu addr 0xffc1c008
[    3.514018] amdgpu 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000200000018, cpu addr 0xffc1c018
[    3.514044] amdgpu 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000200000028, cpu addr 0xffc1c028
[    3.514070] amdgpu 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000200000038, cpu addr 0xffc1c038
[    3.514094] amdgpu 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000200000048, cpu addr 0xffc1c048
[    3.514118] amdgpu 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000200000058, cpu addr 0xffc1c058
[    3.514142] amdgpu 0000:01:00.0: fence driver on ring 6 use gpu addr 0x0000000200000068, cpu addr 0xffc1c068
[    3.514169] amdgpu 0000:01:00.0: fence driver on ring 7 use gpu addr 0x0000000200000078, cpu addr 0xffc1c078
[    3.514194] amdgpu 0000:01:00.0: fence driver on ring 8 use gpu addr 0x0000000200000088, cpu addr 0xffc1c088
[    3.514259] amdgpu 0000:01:00.0: fence driver on ring 9 use gpu addr 0x0000000200000098, cpu addr 0xffc1c098
[    3.514285] amdgpu 0000:01:00.0: fence driver on ring 10 use gpu addr 0x00000002000000a8, cpu addr 0xffc1c0a8
[    3.514658] amdgpu 0000:01:00.0: fence driver on ring 11 use gpu addr 0x000000000109c420, cpu addr 0xfa85a420
[    3.514780] amdgpu 0000:01:00.0: fence driver on ring 12 use gpu addr 0x00000002000000c8, cpu addr 0xffc1c0c8
[    3.514803] amdgpu 0000:01:00.0: fence driver on ring 13 use gpu addr 0x00000002000000d8, cpu addr 0xffc1c0d8
[    3.862202] fbcon: amdgpudrmfb (fb0) is primary device
[    3.862491] amdgpu 0000:01:00.0: fb0: amdgpudrmfb frame buffer device
[    4.078141] [drm] Initialized amdgpu 3.9.0 20150101 for 0000:01:00.0 on minor 0
[   69.590973] amdgpu 0000:01:00.0: GPU fault detected: 147 0x02484801
[   69.590980] amdgpu 0000:01:00.0:   VM_CONTEXT1_PROTECTION_FAULT_ADDR   0x08B4C249
[   69.590985] amdgpu 0000:01:00.0:   VM_CONTEXT1_PROTECTION_FAULT_STATUS 0x02048001
[   69.590991] amdgpu 0000:01:00.0: VM fault (0x01, vmid 1) at page 146063945, read from 'TC4' (0x54433400) (72)
[  244.199433]  ? amd_sched_entity_in+0x30/0xe0 [amdgpu]
[  244.199502]  amd_sched_entity_push_job+0xad/0xf0 [amdgpu]
[  244.199572]  amdgpu_job_submit+0x7e/0xc0 [amdgpu]
[  244.199622]  amdgpu_vm_bo_split_mapping+0x5de/0x750 [amdgpu]
[  244.199673]  ? amdgpu_gem_prime_export+0x40/0x40 [amdgpu]
[  244.199722]  amdgpu_vm_bo_update+0x11d/0x2e0 [amdgpu]
[  244.199769]  amdgpu_gem_va_update_vm+0x160/0x180 [amdgpu]
[  244.199814]  ? amdgpu_init_mem_type+0xa1/0x110 [amdgpu]
[  244.199871]  amdgpu_gem_va_ioctl+0x226/0x2c0 [amdgpu]
[  244.199919]  ? amdgpu_gem_metadata_ioctl+0x1f0/0x1f0 [amdgpu]
[  244.199989]  ? amdgpu_gem_metadata_ioctl+0x1f0/0x1f0 [amdgpu]
[  244.200036]  amdgpu_drm_ioctl+0x3e/0x70 [amdgpu]
```

---

