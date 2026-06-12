---
title: "NVidia RTX 2060 not working, 2nd monitor not detected on Ubuntu Studio 22.04"
date: 2022-07-13
forum: Hardware
---

### Post by mountainman1312 on 2022-07-13
I have a relatively fresh install (few days old) of Ubuntu Studio 22.04 on a CyberPowerPC Tracer R17.
Hardware includes NVidia RTX 2060, AMD Ryzen 7 4800H, and 32GB of DDR4.

I was playing Planetside 2, and the game crashed and I couldn't interact with any windows. After rebooting, all of the window decorations were gone and I couldn't interact with them even more (couldn't close, move, or resize anything). For some reason, those are back now and it all seems fine. However, the 2nd monitor still won't work / won't be detected.

When I boot the machine, I get the following messages sometime during startup:
```

[    0.315063] ACPI BIOS Error (bug): Failure creating named object [\SMIB], AE_ALREADY_EXISTS (20210730/dsfield-637)
[    0.316712] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCIO.GPP4.WLAN], AE_NOT_FOUND (20210730/dswload2-162)
[    0.316717] ACPI Error: AE_NOT_FOUND, During name lookup/catalog (20210730/psobject-220)
[    4.899661] nvidia-gpu 0000:01:00.3: i2c timeout error e0000000
[    4.899696] ucsi_ccg 2-0008: i2c_transfer failed -110
[    4.899696] usci_ccg 2-0008: ucsi_ccg_init failed - -110

```

I can't remember where I found it, but the internet suggested running the following command, and I got the following output:
```

$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-5.15.0-41-lowlatency
W: Possible missing firmware /lib/firmware/amdgpu/yellow_carp_gpu_info.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vangogh_gpu_info.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/cyan_skillfish_rlc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/cyan_skillfish_mec2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/cyan_skillfish_mec.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/cyan_skillfish_me.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/cyan_skillfish_pfp.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/cyan_skillfish_ce.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/cyan_skillfish_sdma1.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/cyan_skillfish_sdma.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sienna_cichlid_mes.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi10_mes.bin for module amdgpu

```

The internet also suggested creating the following file with the following contents.
[FONT=monospace]/etc/modprobe.d/blacklist_i2c-nvidia-gpu.conf
[/FONT]```

[FONT=monospace]blacklist i2c_nvidia_gpu
[/FONT]
```[FONT=monospace]
This did not work. The error messages still show up on boot, and the monitor still doesn't work.
[/FONT]

---

