---
title: "Ubuntu boots only with nomodeset option, not booting otherwise at all."
date: 2021-02-06
forum: Hardware
---

### Post by szewczyk-kamil on 2021-02-06
Yesterday I started having issues with my ubuntu installed on PC. I think this might've been caused by package upgrades, as I was able to correctly boot in the morning, and then after upgrade were installed I was not.
During the day I have noticed that some of the applications were not starting properly, like Zoom, Microsoft Teams of sftp client - all just showing artifacts instead of application window.
Other applications like file explorer, phpstorm or chrome were working without issue.

At some point after another failed attempts to start one of the other application I decided to restart my computer, and unfortunately it didn't boot up at all. All it shows was a white screen with hundreds of colored pixels. Clearly a GPU issue.
After some googling, I found out, to booting with nomodeset option set in grub might help, and yes - I was able to get to Ubuntu, however I have a dual monitor set up, and it was only in mirrored screen mode. Going into displays tab was not showing any monitor to configure. Again, clearly a GPU issue...

Thanks to being able to at least turn on the PC, I can see logs, and provide any required information to get this resolved. Unfortunately I cannot attach the whole dmesg log, as it exceeds the max file size, but I'll put below as much as possible
 ```
[    4.012616] kernel: [drm] PCIE GART of 2048M enabled (table at 0x00000000001D6000).[    4.012747] kernel: radeon 0000:09:00.0: WB enabled
[    4.012751] kernel: radeon 0000:09:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0x0000000003e4bba6
[    4.012752] kernel: radeon 0000:09:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0x00000000415143fc
[    4.012753] kernel: radeon 0000:09:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0x0000000054898365
[    4.012754] kernel: radeon 0000:09:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0x000000004e0b33a6
[    4.012755] kernel: radeon 0000:09:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0x0000000003005df2
[    4.013069] kernel: radeon 0000:09:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0x0000000060b61091
[    4.015752] kernel: input: HD-Audio Generic Front Mic as /devices/pci0000:00/0000:00:08.1/0000:0b:00.3/sound/card2/input33
[    4.015795] kernel: input: HD-Audio Generic Rear Mic as /devices/pci0000:00/0000:00:08.1/0000:0b:00.3/sound/card2/input34
[    4.015822] kernel: input: HD-Audio Generic Line as /devices/pci0000:00/0000:00:08.1/0000:0b:00.3/sound/card2/input35
[    4.015852] kernel: input: HD-Audio Generic Line Out as /devices/pci0000:00/0000:00:08.1/0000:0b:00.3/sound/card2/input36
[    4.015883] kernel: input: HD-Audio Generic Front Headphone as /devices/pci0000:00/0000:00:08.1/0000:0b:00.3/sound/card2/input37
[    4.033075] kernel: radeon 0000:09:00.0: fence driver on ring 6 use gpu addr 0x0000000080000c18 and cpu addr 0x00000000b1a637a0
[    4.033076] kernel: radeon 0000:09:00.0: fence driver on ring 7 use gpu addr 0x0000000080000c1c and cpu addr 0x00000000f52d5851
[    4.033084] kernel: [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    4.033085] kernel: radeon 0000:09:00.0: radeon: MSI limited to 32-bit
[    4.033112] kernel: radeon 0000:09:00.0: radeon: using MSI.
[    4.033135] kernel: [drm] radeon: irq initialized.
[    4.195801] kernel: usbcore: registered new interface driver snd-usb-audio
[    4.256841] kernel: [drm] ring test on 0 succeeded in 2 usecs
[    4.256846] kernel: [drm] ring test on 1 succeeded in 1 usecs
[    4.256851] kernel: [drm] ring test on 2 succeeded in 1 usecs
[    4.256861] kernel: [drm] ring test on 3 succeeded in 4 usecs
[    4.256869] kernel: [drm] ring test on 4 succeeded in 4 usecs
[    4.432693] kernel: [drm] ring test on 5 succeeded in 2 usecs
[    4.432700] kernel: [drm] UVD initialized successfully.
[    4.542014] kernel: [drm] ring test on 6 succeeded in 20 usecs
[    4.542028] kernel: [drm] ring test on 7 succeeded in 3 usecs
[    4.542029] kernel: [drm] VCE initialized successfully.
[    4.542296] kernel: [drm] ib test on ring 0 succeeded in 0 usecs
[    4.542340] kernel: [drm] ib test on ring 1 succeeded in 0 usecs
[    4.542382] kernel: [drm] ib test on ring 2 succeeded in 0 usecs
[    4.542423] kernel: [drm] ib test on ring 3 succeeded in 0 usecs
[    4.542464] kernel: [drm] ib test on ring 4 succeeded in 0 usecs
[    4.549191] kernel: EDAC amd64: F17h detected (node 0).
[    4.549249] kernel: EDAC amd64: Node 0: DRAM ECC disabled.
[    4.552558] kernel: cfg80211: Loading compiled-in X.509 certificates for regulatory database
[    4.552837] kernel: cfg80211: Loaded X.509 cert 'sforshee: 00b28ddf47aef9cea7'
[    4.554587] kernel: lib80211: common routines for IEEE802.11 drivers
[    4.554588] kernel: lib80211_crypt: registered algorithm 'NULL'
[    4.559765] kernel: r8188eu: module is from the staging directory, the quality is unknown, you have been warned.
[    4.561168] kernel: Chip Version Info: CHIP_8188E_Normal_Chip_TSMC_D_CUT_1T1R_RomVer(0)
[    4.621939] kernel: usbcore: registered new interface driver r8188eu
[    4.772628] kernel: EDAC amd64: F17h detected (node 0).
[    4.772670] kernel: EDAC amd64: Node 0: DRAM ECC disabled.
[    4.824851] kernel: r8188eu 3-4:1.0 wlxd037450d4c9b: renamed from wlan0
[    4.852726] kernel: EDAC amd64: F17h detected (node 0).
[    4.852775] kernel: EDAC amd64: Node 0: DRAM ECC disabled.
[    4.936803] kernel: EDAC amd64: F17h detected (node 0).
[    4.936849] kernel: EDAC amd64: Node 0: DRAM ECC disabled.
[    4.986428] kernel: audit: type=1400 audit(1612599093.906:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-senddoc" pid=681 comm="apparmor_parser"
[    4.986853] kernel: audit: type=1400 audit(1612599093.906:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="ippusbxd" pid=676 comm="apparmor_parser"
[    4.986904] kernel: audit: type=1400 audit(1612599093.906:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="lsb_release" pid=671 comm="apparmor_parser"
[    4.986984] kernel: audit: type=1400 audit(1612599093.906:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-xpdfimport" pid=678 comm="apparmor_parser"
[    4.988176] kernel: audit: type=1400 audit(1612599093.910:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe" pid=672 comm="apparmor_parser"
[    4.988180] kernel: audit: type=1400 audit(1612599093.910:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe//kmod" pid=672 comm="apparmor_parser"
[    4.988343] kernel: audit: type=1400 audit(1612599093.910:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-oopslash" pid=683 comm="apparmor_parser"
[    4.988745] kernel: audit: type=1400 audit(1612599093.910:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/man" pid=679 comm="apparmor_parser"
[    4.988749] kernel: audit: type=1400 audit(1612599093.910:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_filter" pid=679 comm="apparmor_parser"
[    5.076721] kernel: EDAC amd64: F17h detected (node 0).
[    5.076774] kernel: EDAC amd64: Node 0: DRAM ECC disabled.
[    5.180661] kernel: EDAC amd64: F17h detected (node 0).
[    5.180708] kernel: EDAC amd64: Node 0: DRAM ECC disabled.
[    5.220021] kernel: [drm] ib test on ring 5 succeeded
[    5.276775] kernel: EDAC amd64: F17h detected (node 0).
[    5.276867] kernel: EDAC amd64: Node 0: DRAM ECC disabled.
[    5.396683] kernel: EDAC amd64: F17h detected (node 0).
[    5.396736] kernel: EDAC amd64: Node 0: DRAM ECC disabled.
[    5.444015] kernel: Generic FE-GE Realtek PHY r8169-500:00: attached PHY driver [Generic FE-GE Realtek PHY] (mii_bus:phy_addr=r8169-500:00, irq=IGNORE)
[    5.484633] kernel: EDAC amd64: F17h detected (node 0).
[    5.484680] kernel: EDAC amd64: Node 0: DRAM ECC disabled.
[    5.484895] kernel: kauditd_printk_skb: 34 callbacks suppressed
[    5.484897] kernel: audit: type=1400 audit(1612599094.406:45): apparmor="DENIED" operation="capable" profile="/usr/sbin/cups-browsed" pid=817 comm="cups-browsed" capability=23  capname="sys_nice"
[    5.486095] kernel: aufs 5.x-rcN-20200622
[    5.588697] kernel: EDAC amd64: F17h detected (node 0).
[    5.588746] kernel: EDAC amd64: Node 0: DRAM ECC disabled.
[    5.636074] kernel: r8169 0000:05:00.0 enp5s0: Link is Down
[    5.672657] kernel: EDAC amd64: F17h detected (node 0).
[    5.672706] kernel: EDAC amd64: Node 0: DRAM ECC disabled.
[    5.732041] kernel: [drm] ib test on ring 6 succeeded
[    5.752764] kernel: EDAC amd64: F17h detected (node 0).
[    5.752811] kernel: EDAC amd64: Node 0: DRAM ECC disabled.
[    5.828828] kernel: EDAC amd64: F17h detected (node 0).
[    5.828880] kernel: EDAC amd64: Node 0: DRAM ECC disabled.
[    5.896801] kernel: EDAC amd64: F17h detected (node 0).
[    5.896850] kernel: EDAC amd64: Node 0: DRAM ECC disabled.
[    5.964642] kernel: EDAC amd64: F17h detected (node 0).
[    5.964686] kernel: EDAC amd64: Node 0: DRAM ECC disabled.
[    6.244073] kernel: [drm] ib test on ring 7 succeeded
[    6.245046] kernel: [drm] Radeon Display Connectors
[    6.245047] kernel: [drm] Connector 0:
[    6.245048] kernel: [drm]   DP-1
[    6.245048] kernel: [drm]   HPD4
[    6.245050] kernel: [drm]   DDC: 0x6530 0x6530 0x6534 0x6534 0x6538 0x6538 0x653c 0x653c
[    6.245050] kernel: [drm]   Encoders:
[    6.245050] kernel: [drm]     DFP1: INTERNAL_UNIPHY2
[    6.245051] kernel: [drm] Connector 1:
[    6.245051] kernel: [drm]   HDMI-A-1
[    6.245052] kernel: [drm]   HPD5
[    6.245053] kernel: [drm]   DDC: 0x6540 0x6540 0x6544 0x6544 0x6548 0x6548 0x654c 0x654c
[    6.245053] kernel: [drm]   Encoders:
[    6.245054] kernel: [drm]     DFP2: INTERNAL_UNIPHY2
[    6.245054] kernel: [drm] Connector 2:
[    6.245054] kernel: [drm]   DVI-I-1
[    6.245055] kernel: [drm]   HPD6
[    6.245056] kernel: [drm]   DDC: 0x6580 0x6580 0x6584 0x6584 0x6588 0x6588 0x658c 0x658c
[    6.245056] kernel: [drm]   Encoders:
[    6.245056] kernel: [drm]     DFP3: INTERNAL_UNIPHY
[    6.245057] kernel: [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    6.245057] kernel: [drm] Connector 3:
[    6.245058] kernel: [drm]   DVI-D-1
[    6.245058] kernel: [drm]   HPD1
[    6.245059] kernel: [drm]   DDC: 0x6570 0x6570 0x6574 0x6574 0x6578 0x6578 0x657c 0x657c
[    6.245059] kernel: [drm]   Encoders:
[    6.245060] kernel: [drm]     DFP4: INTERNAL_UNIPHY1
[    6.337904] kernel: snd_hda_codec_hdmi hdaudioC0D0: HDMI ATI/AMD: no speaker allocation for ELD
[    6.337960] kernel: snd_hda_codec_hdmi hdaudioC0D0: HDMI ATI/AMD: no speaker allocation for ELD
[    6.400743] kernel: snd_hda_codec_hdmi hdaudioC0D0: HDMI ATI/AMD: no speaker allocation for ELD
[    6.402905] kernel: [drm] fb mappable at 0xE05E1000
[    6.402905] kernel: [drm] vram apper at 0xE0000000
[    6.402906] kernel: [drm] size 8294400
[    6.402906] kernel: [drm] fb depth is 24
[    6.402906] kernel: [drm]    pitch is 7680
[    6.402972] kernel: fbcon: radeondrmfb (fb0) is primary device
[    6.403037] kernel: Console: switching to colour frame buffer device 240x67
[    6.403059] kernel: radeon 0000:09:00.0: fb0: radeondrmfb frame buffer device
[    6.424032] kernel: [drm] Initialized radeon 2.50.0 20080528 for 0000:09:00.0 on minor 0
[    6.426824] kernel: AMD-Vi: AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>
[    6.426825] kernel: AMD-Vi: AMD IOMMUv2 functionality not available on this system
[    6.466768] kernel: [drm] amdgpu kernel modesetting enabled.
[    6.466858] kernel: amdgpu: Ignoring ACPI CRAT on non-APU system
[    6.466861] kernel: Virtual CRAT table created for CPU
[    6.466870] kernel: amdgpu: Topology: Add CPU node
[    7.585404] kernel: MAC Address = d0:37:45:0d:4c:9b
[    7.807225] kernel: usb 3-2: reset high-speed USB device number 2 using xhci_hcd
[    8.827042] kernel: rfkill: input handler disabled
[    9.812368] kernel: [drm:si_ib_parse [radeon]] *ERROR* Invalid GFX packet3: 0x50
[    9.812371] kernel:         0xc0012800
[    9.812372] kernel:         0x80000000
[    9.812372] kernel:         0x80000000
[    9.812373] kernel:         0xc0026900
[    9.812373] kernel:         0x00000090
[    9.812373] kernel:         0x80000000
[    9.812373] kernel:         0x40004000
[    9.812374] kernel:         0xc0026900
[    9.812374] kernel:         0x00000286
[    9.812374] kernel:         0x42800000
[    9.812375] kernel:         0x00000000
[    9.812375] kernel:         0xc0016900
[    9.812375] kernel:         0x0000008c
[    9.812376] kernel:         0xaa99aaaa
[    9.812376] kernel:         0xc0016900
[    9.812376] kernel:         0x00000208
[    9.812376] kernel:         0x00000000
[    9.812377] kernel:         0xc0036900
[    9.812377] kernel:         0x000002b0
[    9.812377] kernel:         0x00000000
[    9.812377] kernel:         0x00000000
[    9.812378] kernel:         0x00000000
[    9.812378] kernel:         0xc0016900
[    9.812378] kernel:         0x00000003
[    9.812379] kernel:         0x00000000
[    9.812379] kernel:         0xc0016900
[    9.812379] kernel:         0x00000297
[    9.812379] kernel:         0x00000002
[    9.812380] kernel:         0xc0016900
[    9.812380] kernel:         0x000002a3
[    9.812380] kernel:         0x00000000
[    9.812381] kernel:         0xc0016900
[    9.812381] kernel:         0x000002e6
[    9.812381] kernel:         0x00000000
[    9.812381] kernel:         0xc0016900
[    9.812382] kernel:         0x000002ae
[    9.812382] kernel:         0x00000000
[    9.812383] kernel:         0xc0016900
[    9.812383] kernel:         0x00000020
[    9.812383] kernel:         0x01004300
[    9.812384] kernel:         0xc0016800
[    9.812384] kernel:         0x00000285
[    9.812384] kernel:         0x00000007
[    9.812384] kernel:         0xc0026900
[    9.812385] kernel:         0x00000316
[    9.812385] kernel:         0x0000000e
[    9.812385] kernel:         0x00000010
[    9.812385] kernel:         0xc0016900
[    9.812386] kernel:         0x000002ca
[    9.812386] kernel:         0x00000000
[    9.812386] kernel:         0xc0016900
[    9.812387] kernel:         0x00000081
[    9.812387] kernel:         0x80000000
[    9.812387] kernel:         0xc0026900
[    9.812387] kernel:         0x0000000c
[    9.812388] kernel:         0x00000000
[    9.812388] kernel:         0x40004000
[    9.812388] kernel:         0xc0016900
[    9.812388] kernel:         0x000000d4
[    9.812389] kernel:         0x2a00126a
[    9.812389] kernel:         0xc0026900
[    9.812389] kernel:         0x00000295
[    9.812389] kernel:         0x00000080
[    9.812390] kernel:         0x00000040
[    9.812390] kernel:         0xc0036900
[    9.812390] kernel:         0x00000100
[    9.812391] kernel:         0xffffffff
[    9.812391] kernel:         0x00000000
[    9.812391] kernel:         0x00000000
[    9.812391] kernel:         0xc0016900
[    9.812392] kernel:         0x000002a8
[    9.812392] kernel:         0x00000001
[    9.812392] kernel:         0xc0004200
[    9.812393] kernel:         0x00000000
[    9.812393] kernel:         0xc0034300
[    9.812393] kernel:         0x28c00000
[    9.812393] kernel:         0xffffffff
[    9.812394] kernel:         0x00000000
[    9.812394] kernel:         0x0000000a
[    9.812394] kernel:         0xc0004600
[    9.812394] kernel:         0x00000019
[    9.812395] kernel:         0xc0055000
[    9.812395] kernel:         0x60300000
[    9.812395] kernel:         0x00808ac0
[    9.812396] kernel:         0x00000000
[    9.812396] kernel:         0x00808ac0
[    9.812396] kernel:         0x00000000
[    9.812396] kernel:         0x00200020
[    9.812397] kernel:         0xc0017600 <---
``` 
which is then followed by what I guess is internal kernel information dump.

Result of ```
lshw -C display
```
```
*-display UNCLAIMED              description: VGA compatible controller
       product: Curacao PRO [Radeon R7 370 / R9 270/370 OEM]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:e0000000-efffffff memory:fce00000-fce3ffff ioport:e000(size=256) memory:c0000-dffff

```

```
lsb_release -aNo LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:    20.04
Codename:    focal

```

```
uname -aLinux kamil-desktop 5.8.0-41-generic #46~20.04.1-Ubuntu SMP Mon Jan 18 17:52:23 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

```

Is this a hardware issue and my GPU just decided to die, or can it be solved with software/config changes? 
It is clearly a GPU problem, but based on the fact that with nomodeset option it boots, and uses the card to actually use the display I'm hoping it's not dead...

---

### Post by guiverc on 2021-02-06
Also asked at [https://askubuntu.com/questions/1314078/ubuntu-boots-only-with-nomodeset-option-not-booting-otherwise-at-all-gpu-error](https://askubuntu.com/questions/1314078/ubuntu-boots-only-with-nomodeset-option-not-booting-otherwise-at-all-gpu-error)

---

### Post by szewczyk-kamil on 2021-02-06
That's correct, I was not sure whether those 2 forums are linked, so I posted in both

---

### Post by szewczyk-kamil on 2021-02-06
I'm now almost 100% sure that this is caused by the packages upgrade from Friday morning.
Here are the apt logs, as you can see lots og libgl and graphics related upgrades
```


Start-Date: 2021-02-05  09:14:18
Commandline: aptdaemon role='role-commit-packages' sender=':1.116'
Upgrade: language-pack-gnome-en:amd64 (1:20.04+20200709, 1:20.04+20210121), update-manager-core:amd64 (1:20.04.10.1, 1:20.04.10.5), libegl-mesa0:amd64 (21.1~git2101280600.0f1a8f~oibaf~f, 21.1~git2102050600.465465~oibaf~f), libfprint-2-2:amd64 (1:1.90.2+tod1-0ubuntu1~20.04.2, 1:1.90.2+tod1-0ubuntu1~20.04.4), libglapi-mesa:amd64 (21.1~git2101280600.0f1a8f~oibaf~f, 21.1~git2102050600.465465~oibaf~f), libglapi-mesa:i386 (21.1~git2101280600.0f1a8f~oibaf~f, 21.1~git2102050600.465465~oibaf~f), update-manager:amd64 (1:20.04.10.1, 1:20.04.10.5), google-chrome-stable:amd64 (88.0.4324.96-1, 88.0.4324.150-1), docker-ce-rootless-extras:amd64 (5:20.10.2~3-0~ubuntu-focal, 5:20.10.3~3-0~ubuntu-focal), python-apt-common:amd64 (2.0.0ubuntu0.20.04.3, 2.0.0ubuntu0.20.04.4), libxatracker2:amd64 (21.1~git2101280600.0f1a8f~oibaf~f, 21.1~git2102050600.465465~oibaf~f), libegl1-mesa:amd64 (21.1~git2101280600.0f1a8f~oibaf~f, 21.1~git2102050600.465465~oibaf~f), language-pack-en:amd64 (1:20.04+20200709, 1:20.04+20210121), libgbm1:amd64 (21.1~git2101280600.0f1a8f~oibaf~f, 21.1~git2102050600.465465~oibaf~f), ubuntu-drivers-common:amd64 (1:0.8.4~0.20.04.3, 1:0.8.6.5~0.20.04.1), python3-update-manager:amd64 (1:20.04.10.1, 1:20.04.10.5), language-pack-gnome-en-base:amd64 (1:20.04+20200709, 1:20.04+20210121), libglib2.0-bin:amd64 (2.64.3-1~ubuntu20.04.1, 2.64.6-1~ubuntu20.04.1), libgl1-mesa-dri:amd64 (21.1~git2101280600.0f1a8f~oibaf~f, 21.1~git2102050600.465465~oibaf~f), libgl1-mesa-dri:i386 (21.1~git2101280600.0f1a8f~oibaf~f, 21.1~git2102050600.465465~oibaf~f), libglib2.0-data:amd64 (2.64.3-1~ubuntu20.04.1, 2.64.6-1~ubuntu20.04.1), language-pack-en-base:amd64 (1:20.04+20200709, 1:20.04+20210121), libgl1-mesa-glx:amd64 (21.1~git2101280600.0f1a8f~oibaf~f, 21.1~git2102050600.465465~oibaf~f), libgl1-mesa-glx:i386 (21.1~git2101280600.0f1a8f~oibaf~f, 21.1~git2102050600.465465~oibaf~f), mesa-vdpau-drivers:amd64 (21.1~git2101280600.0f1a8f~oibaf~f, 21.1~git2102050600.465465~oibaf~f), linux-firmware:amd64 (1.187.8, 1.187.9), mesa-vulkan-drivers:amd64 (21.1~git2101280600.0f1a8f~oibaf~f, 21.1~git2102050600.465465~oibaf~f), mesa-vulkan-drivers:i386 (21.1~git2101280600.0f1a8f~oibaf~f, 21.1~git2102050600.465465~oibaf~f), libglib2.0-0:amd64 (2.64.3-1~ubuntu20.04.1, 2.64.6-1~ubuntu20.04.1), docker-ce:amd64 (5:20.10.2~3-0~ubuntu-focal, 5:20.10.3~3-0~ubuntu-focal), python3-apt:amd64 (2.0.0ubuntu0.20.04.3, 2.0.0ubuntu0.20.04.4), mesa-va-drivers:amd64 (21.1~git2101280600.0f1a8f~oibaf~f, 21.1~git2102050600.465465~oibaf~f), base-files:amd64 (11ubuntu5.2, 11ubuntu5.3), docker-ce-cli:amd64 (5:20.10.2~3-0~ubuntu-focal, 5:20.10.3~3-0~ubuntu-focal), libglx-mesa0:amd64 (21.1~git2101280600.0f1a8f~oibaf~f, 21.1~git2102050600.465465~oibaf~f), libglx-mesa0:i386 (21.1~git2101280600.0f1a8f~oibaf~f, 21.1~git2102050600.465465~oibaf~f)
End-Date: 2021-02-05  09:15:32
```

I have done today a full upgrade which was suggested somewhere on the internet, and I can see again a lot of libgl upgrades, but this didn't help... 
```


Start-Date: 2021-02-06  09:15:43
Commandline: apt full-upgrade
Requested-By: kamil (1000)
Upgrade: libegl-mesa0:amd64 (21.1~git2102050600.465465~oibaf~f, 21.1~git2102060600.75c7e4~oibaf~f), update-notifier-common:amd64 (3.192.30.3, 3.192.30.5), libglapi-mesa:amd64 (21.1~git2102050600.465465~oibaf~f, 21.1~git2102060600.75c7e4~oibaf~f), libglapi-mesa:i386 (21.1~git2102050600.465465~oibaf~f, 21.1~git2102060600.75c7e4~oibaf~f), libxatracker2:amd64 (21.1~git2102050600.465465~oibaf~f, 21.1~git2102060600.75c7e4~oibaf~f), libegl1-mesa:amd64 (21.1~git2102050600.465465~oibaf~f, 21.1~git2102060600.75c7e4~oibaf~f), libgbm1:amd64 (21.1~git2102050600.465465~oibaf~f, 21.1~git2102060600.75c7e4~oibaf~f), libgl1-mesa-dri:amd64 (21.1~git2102050600.465465~oibaf~f, 21.1~git2102060600.75c7e4~oibaf~f), libgl1-mesa-dri:i386 (21.1~git2102050600.465465~oibaf~f, 21.1~git2102060600.75c7e4~oibaf~f), libgl1-mesa-glx:amd64 (21.1~git2102050600.465465~oibaf~f, 21.1~git2102060600.75c7e4~oibaf~f), libgl1-mesa-glx:i386 (21.1~git2102050600.465465~oibaf~f, 21.1~git2102060600.75c7e4~oibaf~f), mesa-vdpau-drivers:amd64 (21.1~git2102050600.465465~oibaf~f, 21.1~git2102060600.75c7e4~oibaf~f), mesa-vulkan-drivers:amd64 (21.1~git2102050600.465465~oibaf~f, 21.1~git2102060600.75c7e4~oibaf~f), mesa-vulkan-drivers:i386 (21.1~git2102050600.465465~oibaf~f, 21.1~git2102060600.75c7e4~oibaf~f), update-notifier:amd64 (3.192.30.3, 3.192.30.5), mesa-va-drivers:amd64 (21.1~git2102050600.465465~oibaf~f, 21.1~git2102060600.75c7e4~oibaf~f), libglx-mesa0:amd64 (21.1~git2102050600.465465~oibaf~f, 21.1~git2102060600.75c7e4~oibaf~f), libglx-mesa0:i386 (21.1~git2102050600.465465~oibaf~f, 21.1~git2102060600.75c7e4~oibaf~f)
End-Date: 2021-02-06  09:15:47
```

---

### Post by szewczyk-kamil on 2021-02-06
If anyone is interested, it was the packages.
I was able to get ubuntu back to boot without nomodeset and correct dual monitor set up by downgrading the graphics packages that were upgraded on Friday morning.
Somewhat suprisingly it did removed my Steam for Linux installation - but not very worried about that.

Command that has fixed the issue in my case was:
```
sudo apt-get install libegl-mesa0:amd64=20.2.6-0ubuntu0.20.04.1 libglapi-mesa:amd64=20.2.6-0ubuntu0.20.04.1 libglapi-mesa:i386=20.2.6-0ubuntu0.20.04.1 libxatracker2:amd64=20.2.6-0ubuntu0.20.04.1 libegl1-mesa:amd64=20.2.6-0ubuntu0.20.04.1 ubuntu-drivers-common:amd64=1:0.8.1 libglib2.0-bin:amd64=2.64.6-1~ubuntu20.04.1 libgl1-mesa-glx:amd64=20.2.6-0ubuntu0.20.04.1 mesa-vdpau-drivers:amd64=20.2.6-0ubuntu0.20.04.1 mesa-vulkan-drivers:amd64=20.2.6-0ubuntu0.20.04.1 mesa-vulkan-drivers:i386=20.2.6-0ubuntu0.20.04.1 mesa-va-drivers:amd64=20.2.6-0ubuntu0.20.04.1 libglx-mesa0:amd64=20.2.6-0ubuntu0.20.04.1 libglx-mesa0:i386=20.2.6-0ubuntu0.20.04.1 libgbm1=20.2.6-0ubuntu0.20.04.1 libgl1-mesa-dri=20.2.6-0ubuntu0.20.04.1 libgl1-mesa-dri:i386=20.2.6-0ubuntu0.20.04.1
```

---

### Post by CelticWarrior on 2021-02-06
Have you added a PPA for graphics drivers at some point?

---

### Post by szewczyk-kamil on 2021-02-07
> **CelticWarrior said:**
> Have you added a PPA for graphics drivers at some point?

Not before the Friday update.
I was doing some actions after the graphics were broken, but from my point of view, it looks like the latest package upgrade for one of those packages broke something.

---

### Post by CelticWarrior on 2021-02-07
Yes, but I'm trying to determine where that or those packages came from.
It is a serious problem if they were from the Ubuntu repositories. Not so much if they were from third-party PPAs, breakage is expected due to its experimental nature.

---

### Post by szewczyk-kamil on 2021-02-07
Ah sure.
Well, for me it looks like Ubuntu repositories - however I'm not 100% sure how to confirm. If there's a way of getting package sources I can check that for you, since I know to which versions the packages has been updated on Friday.
My current list of 3rd party PPAs looks like this: [https://i.imgur.com/0ykVoox.png](https://i.imgur.com/0ykVoox.png) and the oibaf/graphics-drivers I installed on Saturday in my attempts to fix the issue. So doesn't look like any of other repositories would provide those packages.

---

### Post by thomasparis on 2021-02-11
Hi,
I think I was hit by the same bug. The timing and symptoms are at least similar. And for a few days, I was seeing updates to the radeon packages, so thought things would get fixed. But I'm not seeing any change any more and still have the problem. Have you guys heard anything? I'm not even sure which package is responsible for the problem, so don't know where to look for more info...

---

### Post by szewczyk-kamil on 2021-02-11
> **thomasparis said:**
> Hi,
I think I was hit by the same bug. The timing and symptoms are at least similar. And for a few days, I was seeing updates to the radeon packages, so thought things would get fixed. But I'm not seeing any change any more and still have the problem. Have you guys heard anything? I'm not even sure which package is responsible for the problem, so don't know where to look for more info...

In var/log/apt/history.log you can find history of all packages upgrades. If you know roughly the time and date of the upgrade that broke things you can find the packages responsible for breaking it. When I looked into my case I noticed that all the graphics packages has been upgraded in bulk - same origin version and same target updated version. I just went on and downgraded ALL of those to original version (omiting the packages not related to graphics)

---

### Post by thomasparis on 2021-02-11
I think it happened for me the same time it did for you.
But, there had to be a "but", right? ;), but I since tried and upgrade to 20.10. I expected it not to help but thought I might try anyway. And something tells me downgrading these specific packages might not be a good idea.
Oh well...
Thanks for the quick reply, btw!

---

### Post by deadflowr on 2021-02-11
ppa-purge the oibaf ppa .

---

### Post by thomasparis on 2021-02-11
Oh! I didn't remember playing with ppa but I do see a reference to that oibaf ppa you mention in my history.

ppa-purge fails, however :(
Warning: Could not find package list for PPA: oibaf graphics-drivers

But now I have a lead. Thanks for the tip!

---

### Post by thomasparis on 2021-02-11
OK, the problem was the relevant lines were commented in my sources.list.d, probably because of the upgrade to 20.10
I uncommented, ppa-purge worked and my system is now fixed.

Thanks!

---

