---
title: "AMD GPU driver issue"
date: 2020-01-30
forum: Hardware
---

### Post by mptr8 on 2020-01-30
> **batmalin said:**
> Actually, this is not true. Despite the fact that obsolete bench tools are showing lower performance on RX560X the current one are showing something different. I am attaching 2 Win and 2 Linux benchmarks for the Vega and the RX560X. Well, Win performs a little bit better, but that might be fixed with the next update of the amdgpu open source driver. My system is Acer Nitro 5 AN515-43 (Ryzen 5 3550H, 16GB DDR4 2666Mhz, 512GB Intel 660p NVMe, 1TB HDD 5400rpm, Vega 8, RX560X, BIOS 1.06).

Your systems are the same as me (Acer Nitro 5 AN515-43), however, how do you manage to install the drivers? do there any step? I'm using 19.10 now. Since the RX 560X  Doesn't had any official drivers how do you manage to install the drivers? Do you use RX 560 Driver?

Im using 19.10 now with kernel 5.5

```

&#10140; sudo lspci -nn | grep -E 'VGA|Display'
01:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Baffin [Radeon RX 460/560D / Pro 450/455/460/555/555X/560/560X] [1002:67ef] (rev c0)
05:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Picasso [1002:15d8] (rev c2)

```


other info.

```

&#10140; dmesg | grep amdgpu
[    2.870501] [drm] amdgpu kernel modesetting enabled.
[    2.893914] amdgpu 0000:01:00.0: remove_conflicting_pci_framebuffers: bar 0: 0xb0000000 -> 0xbfffffff
[    2.893916] amdgpu 0000:01:00.0: remove_conflicting_pci_framebuffers: bar 2: 0xc0000000 -> 0xc01fffff
[    2.893918] amdgpu 0000:01:00.0: remove_conflicting_pci_framebuffers: bar 5: 0xc0b00000 -> 0xc0b3ffff
[    2.894027] amdgpu 0000:01:00.0: enabling device (0002 -> 0003)
[    3.414873] amdgpu 0000:01:00.0: VRAM: 4096M 0x000000F400000000 - 0x000000F4FFFFFFFF (4096M used)
[    3.414877] amdgpu 0000:01:00.0: GART: 256M 0x000000FF00000000 - 0x000000FF0FFFFFFF
[    3.415070] [drm] amdgpu: 4096M of VRAM memory ready
[    3.415074] [drm] amdgpu: 4096M of GTT memory ready.
[    3.428997] amdgpu: [powerplay] hwmgr_sw_init smu backed is polaris10_smu
[    3.926772] [drm] Initialized amdgpu 3.33.0 20150101 for 0000:01:00.0 on minor 0
[    3.926847] amdgpu 0000:05:00.0: remove_conflicting_pci_framebuffers: bar 0: 0x90000000 -> 0x9fffffff
[    3.926848] amdgpu 0000:05:00.0: remove_conflicting_pci_framebuffers: bar 2: 0xa0000000 -> 0xa01fffff
[    3.926850] amdgpu 0000:05:00.0: remove_conflicting_pci_framebuffers: bar 5: 0xc0800000 -> 0xc087ffff
[    3.926853] fb0: switching to amdgpudrmfb from EFI VGA
[    3.927050] amdgpu 0000:05:00.0: vgaarb: deactivate vga console
[    3.928494] amdgpu 0000:05:00.0: VRAM: 2048M 0x000000F400000000 - 0x000000F47FFFFFFF (2048M used)
[    3.928496] amdgpu 0000:05:00.0: GART: 1024M 0x0000000000000000 - 0x000000003FFFFFFF
[    3.928497] amdgpu 0000:05:00.0: AGP: 267419648M 0x000000F800000000 - 0x0000FFFFFFFFFFFF
[    3.928602] [drm] amdgpu: 2048M of VRAM memory ready
[    3.928606] [drm] amdgpu: 3072M of GTT memory ready.
[    3.935927] amdgpu: [powerplay] hwmgr_sw_init smu backed is smu10_smu
[    4.223479] fbcon: amdgpudrmfb (fb0) is primary device
[    4.223651] amdgpu 0000:05:00.0: fb0: amdgpudrmfb frame buffer device
[    4.246633] amdgpu 0000:05:00.0: ring gfx uses VM inv eng 0 on hub 0
[    4.246639] amdgpu 0000:05:00.0: ring comp_1.0.0 uses VM inv eng 1 on hub 0
[    4.246642] amdgpu 0000:05:00.0: ring comp_1.1.0 uses VM inv eng 4 on hub 0
[    4.246646] amdgpu 0000:05:00.0: ring comp_1.2.0 uses VM inv eng 5 on hub 0
[    4.246648] amdgpu 0000:05:00.0: ring comp_1.3.0 uses VM inv eng 6 on hub 0
[    4.246651] amdgpu 0000:05:00.0: ring comp_1.0.1 uses VM inv eng 7 on hub 0
[    4.246653] amdgpu 0000:05:00.0: ring comp_1.1.1 uses VM inv eng 8 on hub 0
[    4.246655] amdgpu 0000:05:00.0: ring comp_1.2.1 uses VM inv eng 9 on hub 0
[    4.246658] amdgpu 0000:05:00.0: ring comp_1.3.1 uses VM inv eng 10 on hub 0
[    4.246660] amdgpu 0000:05:00.0: ring kiq_2.1.0 uses VM inv eng 11 on hub 0
[    4.246663] amdgpu 0000:05:00.0: ring sdma0 uses VM inv eng 0 on hub 1
[    4.246666] amdgpu 0000:05:00.0: ring vcn_dec uses VM inv eng 1 on hub 1
[    4.246669] amdgpu 0000:05:00.0: ring vcn_enc0 uses VM inv eng 4 on hub 1
[    4.246671] amdgpu 0000:05:00.0: ring vcn_enc1 uses VM inv eng 5 on hub 1
[    4.246674] amdgpu 0000:05:00.0: ring vcn_jpeg uses VM inv eng 6 on hub 1
[    4.258055] [drm] Initialized amdgpu 3.33.0 20150101 for 0000:05:00.0 on minor 1
[   18.488441] amdgpu 0000:01:00.0: GPU pci config reset
[  408.038077] amdgpu 0000:01:00.0: GPU pci config reset
[  843.993945] amdgpu 0000:01:00.0: GPU pci config reset

```

---

### Post by batmalin on 2020-04-22
Hi, I didn`t isntall anyting those are the embedded amdgpu drivers in the kernel.

---

### Post by QIII on 2020-04-22
Moved to its own thread from [here]("https://ubuntuforums.org/showthread.php?t=2413167").

Please do not hijack the threads of other users to ask your own support question.  Please start a new thread so that the OP and you both get one-on-one help.

---

### Post by hackingguy on 2020-04-24
> **batmalin said:**
> Hi, I didn`t isntall anyting those are the embedded amdgpu drivers in the kernel.

Hi, Can you help! I am getting approx. equal FPS By Both Vega 8 and Amd Radeon 560X.

I have attached screenshots of "DRI_PRIME=0 glxgears" and "DRI_PRIME=1 glxgears"

Both Integrated And Dedicated GPU are providing 60 FPS Approx!



[ATTACH=CONFIG]285593[/ATTACH]

[ATTACH=CONFIG]285592[/ATTACH]

---

### Post by batmalin on 2020-05-08
Already told you that this bench is not relevant. Install unigine heaven bench and post the results here

---

### Post by Yellow Pasque on 2020-05-09
"Running synchronized to the vertical refresh.  The framerate should be approximately the same as the monitor refresh rate."
So of course you're going to get ~60fps if your display is 60Hz.
Read the output more carefully next time.

> **batmalin said:**
> Already told you that this bench is not relevant.

glxgears is not even a bench(mark).

---

