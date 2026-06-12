---
title: "can't use Radeon 7870 XT (Tahiti LE)"
date: 2020-06-24
forum: Hardware
---

### Post by exe-cute on 2020-06-24
I've got a "new" computer recently for graphical work - here's the parts:
[LIST]
[*]Intel® Core™ i3-4150 CPU @ 3.50GHz × 4 
[*]2x4 GB DDR3 memory @ 1600MHz 
[*]Gigabyte H81M-D2W (not D2V - it's an OEM motherboard) 
[*]VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti LE [Radeon HD 7870 XT] (not the GHz edition that has XT in its codename) 
[*]Generic SSD and peripherals 
[/LIST]
Now I've been trying to get it working for the past few weeks, including trying different Ubuntu versions, down to 14.04, but no avail. I've tried looking things up, but couldn't find any helpful information. Please help me avoid switching to Windows.

Here are the important bits of logs with my different approaches:

**iGPU and "launch with dedicaded GPU from GNOME:**
gnome crashes + restarts
```
radeon_dp_aux_transfer_native: 74 callbacks suppressed
``` a bunch of times

**starting with radoen (the default) and display connected directly:**
```
[drm] radeon kernel modesetting enabled.
radeon 0000:01:00.0: remove_conflicting_pci_framebuffers: bar 0: 0xe0000000 -> 0xefffffff
radeon 0000:01:00.0: remove_conflicting_pci_framebuffers: bar 2: 0xf7e00000 -> 0xf7e3ffff
fb0: switching to radeondrmfb from VESA VGA
radeon 0000:01:00.0: vgaarb: deactivate vga console
radeon 0000:01:00.0: No more image in the PCI ROM
radeon 0000:01:00.0: VRAM: 2048M 0x0000000000000000 - 0x000000007FFFFFFF (2048M used)
radeon 0000:01:00.0: GTT: 2048M 0x0000000080000000 - 0x00000000FFFFFFFF
radeon 0000:01:00.0: failed VCE resume (-22).
radeon 0000:01:00.0: ring 0 stalled for more than XXXXXmsec
radeon 0000:01:00.0: ring 4 stalled for more than XXXXXmsec
[drm:r600_ib_test [radeon]] *ERROR* radeon: fence wait timed out.
[drm:radeon_ib_ring_tests [radeon]] *ERROR* radeon: failed testing IB on GFX ring (-110).
radeon 0000:01:00.0: Syncing to a disabled ring!
radeon 0000:01:00.0: failed to sync rings (-22)
[drm:radeon_gem_va_ioctl [radeon]] *ERROR* Couldn't update BO_VA (-22)
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    va        : 0x000000010192e000
radeon: The kernel rejected CS, see dmesg for more information (-16).
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 4
radeon:    va        : 0x0000000100000000
radeonsi: Failed to create a context.
```

**radeon with nomodeset in parameters (changes to llvmpipe and is very unresponsive):**
```
[drm:radeon_init [radeon]] *ERROR* No UMS support in radeon module!
[drm:amdgpu_init [amdgpu]] *ERROR* VGACON disables amdgpu kernel modesetting.
Failed to start GNOME Shell on Wayland.
Failed to start Tracker file system data miner.
gkr-pam: unable to locate daemon control file
GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
(II) UnloadModule: "radeon"
```

**amdgpu (black screen):**
```
Kernel command line: BOOT_IMAGE=/vmlinuz-5.4.0-37-generic root=UUID=69aa8e32-2d30-4ed2-8962-bea344e5f14d ro quiet radeon.si_support=0 amdgpu.si_support=1 vt.handoff=7
[drm] amdgpu kernel modesetting enabled.
amdgpu 0000:01:00.0: remove_conflicting_pci_framebuffers: bar 0: 0xe0000000 -> 0xefffffff
amdgpu 0000:01:00.0: remove_conflicting_pci_framebuffers: bar 2: 0xf7e00000 -> 0xf7e3ffff
fb0: switching to amdgpudrmfb from VESA VGA
amdgpu 0000:01:00.0: vgaarb: deactivate vga console
amdgpu 0000:01:00.0: kfd not supported on this ASIC
amdgpu 0000:01:00.0: No more image in the PCI ROM
amdgpu 0000:01:00.0: VRAM: 2048M 0x000000F400000000 - 0x000000F47FFFFFFF (2048M used)
amdgpu 0000:01:00.0: GART: 1024M 0x000000FF00000000 - 0x000000FF3FFFFFFF
[drm] amdgpu: 2048M of VRAM memory ready
[drm] amdgpu: 3072M of GTT memory ready.
amdgpu 0000:01:00.0: PCIE GART of 1024M enabled (table at 0x000000F4007E9000).
[drm] amdgpu: dpm initialized
[drm] AMDGPU Display Connectors
fbcon: amdgpudrmfb (fb0) is primary device
amdgpu 0000:01:00.0: fb0: amdgpudrmfb frame buffer device
[drm] Initialized amdgpu 3.35.0 20150101 for 0000:01:00.0 on minor 0
[drm:amdgpu_job_timedout [amdgpu]] *ERROR* ring gfx timeout, signaled seq=2, emitted seq=3
[drm:amdgpu_job_timedout [amdgpu]] *ERROR* Process information: process gnome-shell pid 916 thread gnome-shel:cs0 pid 991
```

**amdgpu + nomodeset (llvmpipe almost tearfree):**
```
Kernel command line: BOOT_IMAGE=/vmlinuz-5.4.0-37-generic root=UUID=69aa8e32-2d30-4ed2-8962-bea344e5f14d ro radeon.si_support=0 amdgpu.si_support=1 nomodeset#
[drm:radeon_init [radeon]] *ERROR* No UMS support in radeon module!
[drm:amdgpu_init [amdgpu]] *ERROR* VGACON disables amdgpu kernel modesetting.
Failed to start GNOME Shell on Wayland.
Failed to start Tracker file system data miner.
gkr-pam: unable to locate daemon control file
```

---

