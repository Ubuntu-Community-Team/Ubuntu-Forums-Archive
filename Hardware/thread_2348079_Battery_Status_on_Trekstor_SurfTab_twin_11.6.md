---
title: "Battery Status on Trekstor SurfTab twin 11.6"
date: 2016-12-31
forum: Hardware
---

### Post by hanspeteriv on 2016-12-31
Hi, I have Ubuntu 16.10 and Windows 10 dual boot on my Trekstor SurfTab twin 11.6.


Battery status (and WiFi and sound, but that is not important) doesn't work with Ubuntu yet. Mains power status is correctly detected as /sys/class/power_supply/ADP1. I would expect the battery to be in /sys/class/battery but that directory does not exist.


According to Windows Device Manager there is a "Intel Battery Management Device". Hardware ID is "ACPI\VEN_INT&DEV_33FE".


Any ideas would be much appreciated. I can live without WiFi and sound but I have already bricked another Trekstor SurfTab by running out of power. :o

EDIT: WiFi works with the custom 17.04 iso from [https://linuxiumcomau.blogspot.com/](https://linuxiumcomau.blogspot.com/) 

EDIT 2: I found something interesting in dmesg, but don't know what to do with it.

```

[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x000000007B163000 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 0x000000007B1630A8 0000D4 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x000000007B180178 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x000000007B163210 01CF63 (v02 ALASKA A M I    01072009 INTL 20120913)
[    0.000000] ACPI: APIC 0x000000007B180288 000084 (v03 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x000000007B180310 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FIDT 0x000000007B180358 00009C (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: MSDM 0x000000007B1803F8 000055 (v03 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 0x000000007B180450 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
[    0.000000] ACPI: SSDT 0x000000007B180490 004021 (v01 DptfTb DptfTab  00001000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x000000007B1844B8 000645 (v01 CpuDpf CpuDptf  00001000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x000000007B184B00 000058 (v01 LowPM  LowPwrM  00001000 INTL 20120913)
[    0.000000] ACPI: UEFI 0x000000007B184B58 000042 (v01 ALASKA A M I    00000000      00000000)
[    0.000000] ACPI: HPET 0x000000007B184BA0 000038 (v01 ALASKA A M I    01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 0x000000007B184BD8 000763 (v01 PmRef  CpuPm    00003000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x000000007B185340 000290 (v01 PmRef  Cpu0Tst  00003000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x000000007B1855D0 00017A (v01 PmRef  ApTst    00003000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x000000007B185750 00043A (v01 Intel_ Tpm2Tabl 00001000 INTL 20120913)
[    0.000000] ACPI: TPM2 0x000000007B185B90 000034 (v03                 00000000      00000000)
[    0.000000] ACPI: LPIT 0x000000007B185BC8 000104 (v01 ALASKA A M I    00000005 MSFT 0100000D)
**[    0.000000] ACPI: BCFG 0x000000007B185CD0 000139 (v01 INTEL  BATTCONF 00000001 INTL 00000000)**
[    0.000000] ACPI: PRAM 0x000000007B185E10 000030 (v01                 00000001      00000000)
[    0.000000] ACPI: BGRT 0x000000007B185E40 000038 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: CSRT 0x000000007B185E78 00014C (v00 INTEL  LANFORDC 00000005 MSFT 0100000D)
[    0.000000] ACPI: WDAT 0x000000007B185FC8 000104 (v01                 00000000      00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000

...

[    0.216894] ------------[ cut here ]------------
[    0.216907] WARNING: CPU: 1 PID: 1 at /usr/src/development/linuxium/ubuntu/ubuntu-zesty/Ubuntu-4.9.0-11.12/fs/sysfs/dir.c:31 sysfs_warn_dup+0x64/0x80
**[    0.216909] sysfs: cannot create duplicate filename '/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/808622C1:00/OVTI2680:00/power_resources_D0/LNXPOWER:0b'**
[    0.216910] Modules linked in:
[    0.216917] CPU: 1 PID: 1 Comm: swapper/0 Not tainted 4.9.0-11-linuxium #12+IntelAtom
[    0.216919] Hardware name: TrekStor SurfTab twin 11.6/CherryTrail CR, BIOS TP15-VT5.3.1.3 10/28/2016
[    0.216923]  ffffbe96c0343a00 ffffffffa6418203 ffffbe96c0343a50 0000000000000000
[    0.216930]  ffffbe96c0343a40 ffffffffa6080b31 0000001fc0343a68 ffff9a62f578d000
[    0.216936]  ffff9a62fa107860 ffff9a62fa12eca8 0000000000000001 ffffffffffffffef
[    0.216941] Call Trace:
[    0.216951]  [<ffffffffa6418203>] dump_stack+0x63/0x90
[    0.216957]  [<ffffffffa6080b31>] __warn+0xd1/0xf0
[    0.216962]  [<ffffffffa6080b9f>] warn_slowpath_fmt+0x4f/0x60
[    0.216967]  [<ffffffffa62ad80f>] ? kernfs_path_from_node+0x4f/0x60
[    0.216970]  [<ffffffffa62b0f44>] sysfs_warn_dup+0x64/0x80
[    0.216974]  [<ffffffffa62b12ce>] sysfs_do_create_link_sd.isra.2+0x9e/0xb0
[    0.216978]  [<ffffffffa62b1337>] sysfs_create_link_sd+0x17/0x20
[    0.216981]  [<ffffffffa62b1675>] sysfs_add_link_to_group+0x35/0x60
[    0.216987]  [<ffffffffa64bd4d2>] acpi_power_expose_list+0x6f/0x93
[    0.216991]  [<ffffffffa64bd879>] acpi_power_add_remove_device+0x72/0x91
[    0.216998]  [<ffffffffa64b582c>] acpi_add_single_object+0x52e/0x576
[    0.217002]  [<ffffffffa64b59a5>] acpi_bus_check_add+0x131/0x1e0
[    0.217009]  [<ffffffffa60cd6d2>] ? up+0x32/0x50
[    0.217015]  [<ffffffffa64dced9>] ? acpi_ut_acquire_mutex+0x52/0x97
[    0.217019]  [<ffffffffa64d3e32>] acpi_ns_walk_namespace+0xdf/0x18f
[    0.217023]  [<ffffffffa64b5874>] ? acpi_add_single_object+0x576/0x576
[    0.217027]  [<ffffffffa64b5874>] ? acpi_add_single_object+0x576/0x576
[    0.217030]  [<ffffffffa64d4320>] acpi_walk_namespace+0x9b/0xcf
[    0.217037]  [<ffffffffa7019c75>] ? acpi_sleep_proc_init+0x28/0x28
[    0.217041]  [<ffffffffa64b5cb0>] acpi_bus_scan+0x48/0x67
[    0.217044]  [<ffffffffa701a1e9>] acpi_scan_init+0xd0/0x212
[    0.217048]  [<ffffffffa7019f29>] acpi_init+0x2b4/0x303
[    0.217054]  [<ffffffffa6002190>] do_one_initcall+0x50/0x1a0
[    0.217063]  [<ffffffffa6fce14b>] kernel_init_freeable+0x18b/0x218
[    0.217069]  [<ffffffffa6867380>] ? rest_init+0x80/0x80
[    0.217072]  [<ffffffffa686738e>] kernel_init+0xe/0x110
[    0.217077]  [<ffffffffa6874735>] ret_from_fork+0x25/0x30
[    0.217086] ---[ end trace 07b6f39a70166d7d ]---
```

Edit 3:Battery status works with the latest "17.04 pseudo beta 1" image from [https://sites.google.com/site/wwwlinuxiumcomau/how-tos/runningubuntuontheintelcomputestick](https://sites.google.com/site/wwwlinuxiumcomau/how-tos/runningubuntuontheintelcomputestick)

---

