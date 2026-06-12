---
title: "Via Epia M10000 - openchrome issues with dri"
date: 2010-09-12
forum: Hardware
---

### Post by ancarpan on 2010-09-12
Hi, 

my problem is that I have a mythbuntu 10.04 running on a Via Epia M10000, but direct rendering is not working.

- drm module is loaded at kernel startup. Here's what I get at boot:

```

$ dmesg |grep -e drm -e agp
[    0.000000] Linux version 2.6.32-24-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 (Ubuntu 2.6.32-24.42-generic 2.6.32.15+drm33.5)
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=a2ee4f9b-1db7-414c-9678-920310fd56c2 ro crashkernel=384M-2G:64M,2G-:128M quiet splash drm.debug=1 log_buf_len=16M
[   12.326378] Linux agpgart interface v0.103
[   13.969611] [drm] Initialized drm 1.1.0 20060810
[   14.003008] agpgart: Detected VIA CLE266 chipset
[   14.020903] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xd0000000
[   15.172767] [drm:drm_init], 
[   15.172806] [drm:drm_get_dev], 
[   15.172965] [drm:drm_get_minor], 
[   15.178244] [drm:drm_get_minor], new minor assigned 0
[   15.178508] [drm] Initialized via 2.11.1 20070202 for 0000:01:00.0 on minor 0
[   15.758948] [drm:drm_stub_open], 
[   15.758967] [drm:drm_open_helper], pid = 235, minor = 0
[   15.758989] [drm:drm_setup], 
[   15.759017] [drm:drm_ioctl], pid=235, cmd=0xc0246400, nr=0x00, dev 0xe200, auth=1
[   15.759040] [drm:drm_ioctl], pid=235, cmd=0xc0246400, nr=0x00, dev 0xe200, auth=1
[   15.759067] [drm:drm_release], open_count = 1
[   15.759077] [drm:drm_release], pid = 235, device = 0xe200, open_count = 1
[   15.759095] [drm:drm_lastclose], 
[   15.759105] [drm:drm_lastclose], driver lastclose completed
[   15.759118] [drm:drm_lastclose], lastclose completed

```

- I've added the following lines to xorg.conf:

```

Section "DRI"
    Mode       0666
EndSection

```

- I'm using openchrome xorg driver which should support the CLE266 chipset, but in /var/log/Xorg.0.log there's no [dri] line

- no useful warning/error in Xorg.0.log:

```

$ grep -e WW -e EE  /var/log/Xorg.0.log
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(II) Loading extension MIT-SCREEN-SAVER
(WW) CHROME(0): Manufacturer plainly copied main PCI IDs to subsystem/card IDs.
(WW) CHROME(0): [XvMC] Cannot use XvMC without DRI!
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(II) XKB: reuse xkmfile /var/lib/xkb/server-3781FECB9CB8D26EE03343DB2C93394EA704B98F.xkm

```

It really looks like the openchrome driver doesn't even try to enable dri. Anyone has an idea about this? Any suggestion?

Thanks.

---

### Post by shrecks_ on 2011-05-04
The reason openchrome doesnt enable DRI is because there have been instances in the past where people have experienced sudden freezing/stalling of their systems when direct 3D rendering was enabled.And i guess openchrome decided to keep it disabled by default.I am trying to figure out how this can be enabled.

---

