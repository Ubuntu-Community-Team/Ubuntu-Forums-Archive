---
title: "Radeon gpu lockup in syslog"
date: 2016-12-17
forum: Hardware
---

### Post by GreatDanton on 2016-12-17
I've been using my computer for a few years without any issues, until recently when I started to get random black screens (but a few seconds later I was able to use computer normally again). I thought they were from the latest update and I didn't pay much attention to them. Few days later my computer did not want to boot, and I heard 1 long beep  and 3 shorter right afterwards. I checked the beep error codes, and  according to the docs that supposed to be hardware fault. I opened up my case, removed the dust that gathered over the years, removed the graphic card, and put it back in. It booted on the first try so I thought the problem was solved.


 Later on, black screens happened more often, so I checked my syslog and found something like this in it (this is just a part of it):

```
ec 17 15:57:02 Desktop systemd[1]: Started Cleanup of Temporary Directories.
Dec 17 16:05:01 Desktop CRON[3995]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 17 16:15:01 Desktop CRON[4727]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 17 16:17:01 Desktop CRON[4868]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 17 16:25:01 Desktop CRON[5424]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 17 16:26:09 Desktop ntpd[1435]: 84.255.242.202 local addr 192.168.1.12 -> <null>
Dec 17 16:35:01 Desktop CRON[6156]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 17 16:41:06 Desktop org.a11y.Bus[1698]: Activating service name='org.a11y.atspi.Registry'
Dec 17 16:41:06 Desktop org.a11y.Bus[1698]: Successfully activated service 'org.a11y.atspi.Registry'
Dec 17 16:41:06 Desktop org.a11y.atspi.Registry[6603]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Dec 17 16:45:01 Desktop CRON[6921]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 17 16:55:01 Desktop CRON[7651]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 17 16:59:05 Desktop kernel: [ 4646.348020] radeon 0000:01:00.0: ring 0 stalled for more than 10180msec
Dec 17 16:59:05 Desktop kernel: [ 4646.348025] radeon 0000:01:00.0: GPU lockup (current fence id 0x000000000005c299 last fence id 0x000000000005c40a on ring 0)
Dec 17 16:59:05 Desktop kernel: [ 4646.348044] radeon 0000:01:00.0: failed to get a new IB (-35)
Dec 17 16:59:05 Desktop kernel: [ 4646.348089] [drm:radeon_cs_ioctl [radeon]] *ERROR* Failed to get ib !
Dec 17 16:59:05 Desktop kernel: [ 4646.370010] radeon 0000:01:00.0: Saved 11801 dwords of commands on ring 0.
Dec 17 16:59:05 Desktop kernel: [ 4646.370019] radeon 0000:01:00.0: GPU softreset: 0x00000019
Dec 17 16:59:05 Desktop kernel: [ 4646.370023] radeon 0000:01:00.0:   R_008010_GRBM_STATUS      = 0xE57044A4
Dec 17 16:59:05 Desktop kernel: [ 4646.370026] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2     = 0x3FFFFF02
Dec 17 16:59:05 Desktop kernel: [ 4646.370028] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS      = 0x200000C0
Dec 17 16:59:05 Desktop kernel: [ 4646.370031] radeon 0000:01:00.0:   R_008674_CP_STALLED_STAT1 = 0x04000000
Dec 17 16:59:05 Desktop kernel: [ 4646.370034] radeon 0000:01:00.0:   R_008678_CP_STALLED_STAT2 = 0x00010002
Dec 17 16:59:05 Desktop kernel: [ 4646.370037] radeon 0000:01:00.0:   R_00867C_CP_BUSY_STAT     = 0x00008482
Dec 17 16:59:05 Desktop kernel: [ 4646.370040] radeon 0000:01:00.0:   R_008680_CP_STAT          = 0x80818647
Dec 17 16:59:05 Desktop kernel: [ 4646.370042] radeon 0000:01:00.0:   R_00D034_DMA_STATUS_REG   = 0x44C83D57
Dec 17 16:59:05 Desktop kernel: [ 4646.422935] radeon 0000:01:00.0: R_008020_GRBM_SOFT_RESET=0x00007F6B
Dec 17 16:59:05 Desktop kernel: [ 4646.422989] radeon 0000:01:00.0: SRBM_SOFT_RESET=0x00000100
Dec 17 16:59:05 Desktop kernel: [ 4646.425078] radeon 0000:01:00.0:   R_008010_GRBM_STATUS      = 0x00003028
Dec 17 16:59:05 Desktop kernel: [ 4646.425081] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2     = 0x00000002
Dec 17 16:59:05 Desktop kernel: [ 4646.425083] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS      = 0x200000C0
Dec 17 16:59:05 Desktop kernel: [ 4646.425086] radeon 0000:01:00.0:   R_008674_CP_STALLED_STAT1 = 0x00000000
Dec 17 16:59:05 Desktop kernel: [ 4646.425089] radeon 0000:01:00.0:   R_008678_CP_STALLED_STAT2 = 0x00000000
Dec 17 16:59:05 Desktop kernel: [ 4646.425092] radeon 0000:01:00.0:   R_00867C_CP_BUSY_STAT     = 0x00000000
Dec 17 16:59:05 Desktop kernel: [ 4646.425094] radeon 0000:01:00.0:   R_008680_CP_STAT          = 0x00000000
Dec 17 16:59:05 Desktop kernel: [ 4646.425097] radeon 0000:01:00.0:   R_00D034_DMA_STATUS_REG   = 0x44C83D57
Dec 17 16:59:05 Desktop kernel: [ 4646.425104] radeon 0000:01:00.0: GPU reset succeeded, trying to resume
Dec 17 16:59:05 Desktop kernel: [ 4646.493307] [drm] PCIE GART of 1024M enabled (table at 0x0000000000258000).
Dec 17 16:59:05 Desktop kernel: [ 4646.493325] radeon 0000:01:00.0: WB enabled
Dec 17 16:59:05 Desktop kernel: [ 4646.493329] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff880034f5cc00
Dec 17 16:59:05 Desktop kernel: [ 4646.493331] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff880034f5cc0c
Dec 17 16:59:05 Desktop kernel: [ 4646.494306] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000056230 and cpu addr 0xffffc90001016230
Dec 17 16:59:05 Desktop kernel: [ 4646.540238] [drm] ring test on 0 succeeded in 1 usecs
Dec 17 16:59:05 Desktop kernel: [ 4646.540245] [drm] ring test on 3 succeeded in 2 usecs
Dec 17 16:59:05 Desktop kernel: [ 4646.714873] [drm] ring test on 5 succeeded in 1 usecs
Dec 17 16:59:05 Desktop kernel: [ 4646.714879] [drm] UVD initialized successfully.
Dec 17 16:59:06 Desktop kernel: [ 4646.736081] [drm] ib test on ring 0 succeeded in 0 usecs
Dec 17 16:59:06 Desktop kernel: [ 4646.736098] [drm] ib test on ring 3 succeeded in 0 usecs
Dec 17 16:59:16 Desktop kernel: [ 4656.884019] radeon 0000:01:00.0: ring 5 stalled for more than 10000msec
Dec 17 16:59:16 Desktop kernel: [ 4656.884024] radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000000002 last fence id 0x0000000000000004 on ring 5)
Dec 17 16:59:16 Desktop kernel: [ 4656.884083] [drm:uvd_v1_0_ib_test [radeon]] *ERROR* radeon: fence wait failed (-35).
Dec 17 16:59:16 Desktop kernel: [ 4656.884114] [drm:radeon_ib_ring_tests [radeon]] *ERROR* radeon: failed testing IB on ring 5 (-35).
Dec 17 16:59:58 Desktop kernel: [ 4699.716019] radeon 0000:01:00.0: ring 0 stalled for more than 10260msec
Dec 17 16:59:58 Desktop kernel: [ 4699.716025] radeon 0000:01:00.0: GPU lockup (current fence id 0x000000000005dcd1 last fence id 0x000000000005ddd9 on ring 0)
Dec 17 16:59:58 Desktop kernel: [ 4699.716044] radeon 0000:01:00.0: failed to get a new IB (-35)
Dec 17 16:59:58 Desktop kernel: [ 4699.716089] [drm:radeon_cs_ioctl [radeon]] *ERROR* Failed to get ib !
Dec 17 16:59:59 Desktop kernel: [ 4699.738001] radeon 0000:01:00.0: Saved 8441 dwords of commands on ring 0.
Dec 17 16:59:59 Desktop kernel: [ 4699.738011] radeon 0000:01:00.0: GPU softreset: 0x00000019
Dec 17 16:59:59 Desktop kernel: [ 4699.738014] radeon 0000:01:00.0:   R_008010_GRBM_STATUS      = 0xE57054A4
Dec 17 16:59:59 Desktop kernel: [ 4699.738017] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2     = 0x3FFFF102
Dec 17 16:59:59 Desktop kernel: [ 4699.738020] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS      = 0x200000C0
Dec 17 16:59:59 Desktop kernel: [ 4699.738023] radeon 0000:01:00.0:   R_008674_CP_STALLED_STAT1 = 0x04000000
Dec 17 16:59:59 Desktop kernel: [ 4699.738026] radeon 0000:01:00.0:   R_008678_CP_STALLED_STAT2 = 0x00010002
Dec 17 16:59:59 Desktop kernel: [ 4699.738029] radeon 0000:01:00.0:   R_00867C_CP_BUSY_STAT     = 0x00008482
Dec 17 16:59:59 Desktop kernel: [ 4699.738031] radeon 0000:01:00.0:   R_008680_CP_STAT          = 0x80818647
Dec 17 16:59:59 Desktop kernel: [ 4699.738034] radeon 0000:01:00.0:   R_00D034_DMA_STATUS_REG   = 0x44C83D57
Dec 17 16:59:59 Desktop kernel: [ 4699.801532] radeon 0000:01:00.0: R_008020_GRBM_SOFT_RESET=0x00007F6B
Dec 17 16:59:59 Desktop kernel: [ 4699.801586] radeon 0000:01:00.0: SRBM_SOFT_RESET=0x00000100
Dec 17 16:59:59 Desktop kernel: [ 4699.803674] radeon 0000:01:00.0:   R_008010_GRBM_STATUS      = 0x00003028
Dec 17 16:59:59 Desktop kernel: [ 4699.803677] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2     = 0x00000002
Dec 17 16:59:59 Desktop kernel: [ 4699.803680] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS      = 0x200000C0
Dec 17 16:59:59 Desktop kernel: [ 4699.803682] radeon 0000:01:00.0:   R_008674_CP_STALLED_STAT1 = 0x00000000
Dec 17 16:59:59 Desktop kernel: [ 4699.803685] radeon 0000:01:00.0:   R_008678_CP_STALLED_STAT2 = 0x00000000
Dec 17 16:59:59 Desktop kernel: [ 4699.803688] radeon 0000:01:00.0:   R_00867C_CP_BUSY_STAT     = 0x00000000
Dec 17 16:59:59 Desktop kernel: [ 4699.803691] radeon 0000:01:00.0:   R_008680_CP_STAT          = 0x00000000
Dec 17 16:59:59 Desktop kernel: [ 4699.803693] radeon 0000:01:00.0:   R_00D034_DMA_STATUS_REG   = 0x44C83D57
Dec 17 16:59:59 Desktop kernel: [ 4699.803701] radeon 0000:01:00.0: GPU reset succeeded, trying to resume
Dec 17 16:59:59 Desktop kernel: [ 4699.871829] [drm] PCIE GART of 1024M enabled (table at 0x0000000000258000).
Dec 17 16:59:59 Desktop kernel: [ 4699.871847] radeon 0000:01:00.0: WB enabled
Dec 17 16:59:59 Desktop kernel: [ 4699.871850] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff880034f5cc00
Dec 17 16:59:59 Desktop kernel: [ 4699.871852] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff880034f5cc0c
Dec 17 16:59:59 Desktop kernel: [ 4699.872888] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000056230 and cpu addr 0xffffc90001016230
Dec 17 16:59:59 Desktop kernel: [ 4699.918828] [drm] ring test on 0 succeeded in 1 usecs
Dec 17 16:59:59 Desktop kernel: [ 4699.918835] [drm] ring test on 3 succeeded in 2 usecs
Dec 17 16:59:59 Desktop kernel: [ 4700.093464] [drm] ring test on 5 succeeded in 1 usecs
Dec 17 16:59:59 Desktop kernel: [ 4700.093705] [drm] UVD initialized successfully.
Dec 17 16:59:59 Desktop kernel: [ 4700.132119] [drm] ib test on ring 0 succeeded in 0 usecs
Dec 17 16:59:59 Desktop kernel: [ 4700.132136] [drm] ib test on ring 3 succeeded in 0 usecs
Dec 17 17:00:09 Desktop kernel: [ 4710.284035] radeon 0000:01:00.0: ring 5 stalled for more than 10004msec
Dec 17 17:00:09 Desktop kernel: [ 4710.284041] radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000000004 last fence id 0x0000000000000006 on ring 5)
Dec 17 17:00:09 Desktop kernel: [ 4710.284100] [drm:uvd_v1_0_ib_test [radeon]] *ERROR* radeon: fence wait failed (-35).
Dec 17 17:00:09 Desktop kernel: [ 4710.284131] [drm:radeon_ib_ring_tests [radeon]] *ERROR* radeon: failed testing IB on ring 5 (-35).


```


I goggled what that supposed to mean and found this post: [URL="https://bbs.archlinux.org/viewtopic.php?id=186388"]https://bbs.archlinux.org/viewtopic.php?id=186388
[/URL]
I am not quite sure if that's related to my problem, since the post is from 2014. Or is my graphic card slowly dying? I am kinda clueless, so any ideas are welcome (:


lspci:
```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV770 [Radeon HD 4870]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV770 HDMI Audio [Radeon HD 4850/4870]
02:00.0 Ethernet controller: Qualcomm Atheros Attansic L1 Gigabit Ethernet (rev b0)
03:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
03:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
05:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)

```

---

