---
title: "Dell Inspiron 15 7548 screen flickering after resume"
date: 2016-01-06
forum: Hardware
---

### Post by fryda.tomas on 2016-01-06
Hi,

I've got following issue - after resume from suspend wifi is down and screen is randomly blinking. I've found out some correlation between blinking and thunderbird fetching data from gmail. And it does not blink while touching a touchpad but it does while moving a cursor using the touchpad.

I've been able to reproduce this behaviour by following steps:
1) boot into ubuntu and log in
2) start firefox and thunderbird
3) suspend
4) resume
5) enable wifi if it's down
6) minimize and maximize thunderbird
7) screen flickers/blinks 

I've got following setup:
kernel: 4.2.0-23-generic #28-Ubuntu SMP Sun Dec 27 17:47:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
using fglrx-updates (but tried opensource driver and fglrx, didn't help)
4K screen
Intel i7-5500U (broadwell)
AMD Radeon R7 M270
output of lshw and dmesg is below 

What I've tried:
* using different gpu driver and while using proprietary driver using both settings powersave (using intel gpu) and performance
* using uxa instead of sna as AccelMethod
* using each pm-suspend quirk  from following list and some combinations [--quirk-dpms-on, --quirk-dpms-suspend,  --quirk-radeon-off,  --quirk-reset-brightness,  --quirk-s3-bios,  --quirk-s3-mode, --quirk-vbe-post,  --quirk-vbemode-restore,  --quirk-vbestate-restore,  --quirk-vga-mode-3]


Do you have any idea what i could try?
dmesg:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.2.0-23-generic (buildd@lcy01-30) (gcc version 5.2.1 20151010 (Ubuntu 5.2.1-22ubuntu2) ) #28-Ubuntu SMP Sun Dec 27 17:47:31 UTC 2015 (Ubuntu 4.2.0-23.28-generic 4.2.6)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-23-generic.efi.signed root=UUID=cea9bfa6-81da-400b-a577-7b7c208bc428 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: xstate_offset[2]: 0240, xstate_sizes[2]: 0100
[    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x04: 'AVX registers'
[    0.000000] x86/fpu: Enabled xstate features 0x7, context size is 0x340 bytes, using 'standard' format.
[    0.000000] x86/fpu: Using 'eager' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000059000-0x000000000009dfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000c630dfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c630e000-0x00000000c667ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c6680000-0x00000000cbb83fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cbb84000-0x00000000cbbe2fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cbbe3000-0x00000000cbc0cfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cbc0d000-0x00000000ccd50fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000ccd51000-0x00000000ccffefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ccfff000-0x00000000ccffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cd800000-0x00000000cfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000042effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] e820: update [mem 0xc539c018-0xc53ac057] usable ==> usable
[    0.000000] e820: update [mem 0xc538d018-0xc539ba57] usable ==> usable
[    0.000000] extended physical RAM map:
[    0.000000] reserve setup_data: [mem 0x0000000000000000-0x0000000000057fff] usable
[    0.000000] reserve setup_data: [mem 0x0000000000058000-0x0000000000058fff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000000059000-0x000000000009dfff] usable
[    0.000000] reserve setup_data: [mem 0x000000000009e000-0x000000000009ffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000000100000-0x00000000c538d017] usable
[    0.000000] reserve setup_data: [mem 0x00000000c538d018-0x00000000c539ba57] usable
[    0.000000] reserve setup_data: [mem 0x00000000c539ba58-0x00000000c539c017] usable
[    0.000000] reserve setup_data: [mem 0x00000000c539c018-0x00000000c53ac057] usable
[    0.000000] reserve setup_data: [mem 0x00000000c53ac058-0x00000000c630dfff] usable
[    0.000000] reserve setup_data: [mem 0x00000000c630e000-0x00000000c667ffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000c6680000-0x00000000cbb83fff] usable
[    0.000000] reserve setup_data: [mem 0x00000000cbb84000-0x00000000cbbe2fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000cbbe3000-0x00000000cbc0cfff] ACPI data
[    0.000000] reserve setup_data: [mem 0x00000000cbc0d000-0x00000000ccd50fff] ACPI NVS
[    0.000000] reserve setup_data: [mem 0x00000000ccd51000-0x00000000ccffefff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000ccfff000-0x00000000ccffffff] usable
[    0.000000] reserve setup_data: [mem 0x00000000cd800000-0x00000000cfffffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000100000000-0x000000042effffff] usable
[    0.000000] efi: EFI v2.40 by American Megatrends
[    0.000000] efi:  ESRT=0xccfa8198  ACPI=0xcbbeb000  ACPI 2.0=0xcbbeb000  SMBIOS=0xccef4e18 
[    0.000000] esrt: Reserving ESRT space from 0x00000000ccfa8198 to 0x00000000ccfa81d0.
[    0.000000] SMBIOS 2.8 present.
[    0.000000] DMI: Dell Inc. Inspiron 7548/0AM6R0, BIOS A05 07/20/2015
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x42f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7F80000000 write-back
[    0.000000]   1 base 0080000000 mask 7FC0000000 write-back
[    0.000000]   2 base 00C0000000 mask 7FF8000000 write-back
[    0.000000]   3 base 00C8000000 mask 7FFC000000 write-back
[    0.000000]   4 base 00CC000000 mask 7FFF000000 write-back
[    0.000000]   5 base 0100000000 mask 7F00000000 write-back
[    0.000000]   6 base 0200000000 mask 7E00000000 write-back
[    0.000000]   7 base 0400000000 mask 7FC0000000 write-back
[    0.000000]   8 base 0430000000 mask 7FF0000000 uncachable
[    0.000000]   9 base 042F000000 mask 7FFF000000 uncachable
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 128MB, type WB
[    0.000000] reg 3, base: 3200MB, range: 64MB, type WB
[    0.000000] reg 4, base: 3264MB, range: 16MB, type WB
[    0.000000] reg 5, base: 4GB, range: 4GB, type WB
[    0.000000] reg 6, base: 8GB, range: 8GB, type WB
[    0.000000] reg 7, base: 16GB, range: 1GB, type WB
[    0.000000] reg 8, base: 17152MB, range: 256MB, type UC
[    0.000000] reg 9, base: 17136MB, range: 16MB, type UC
[    0.000000] total RAM covered: 16320M
[    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 64K     chunk_size: 128K     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 64K     chunk_size: 256K     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 64K     chunk_size: 512K     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 64K     chunk_size: 1M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 64K     chunk_size: 4M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 64K     chunk_size: 8M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 10      lose cover RAM: 48M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 32M     num_reg: 10      lose cover RAM: -16M
[    0.000000]  gran_size: 64K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 64K     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000]  gran_size: 64K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 64K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 128K     chunk_size: 128K     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 128K     chunk_size: 256K     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 128K     chunk_size: 512K     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 128K     chunk_size: 1M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 128K     chunk_size: 2M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 128K     chunk_size: 4M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 128K     chunk_size: 8M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 128K     chunk_size: 16M     num_reg: 10      lose cover RAM: 48M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 32M     num_reg: 10      lose cover RAM: -16M
[    0.000000]  gran_size: 128K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 128K     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000]  gran_size: 128K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 128K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 256K     chunk_size: 256K     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 256K     chunk_size: 512K     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 256K     chunk_size: 1M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 256K     chunk_size: 2M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 256K     chunk_size: 4M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 256K     chunk_size: 8M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 256K     chunk_size: 16M     num_reg: 10      lose cover RAM: 48M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 32M     num_reg: 10      lose cover RAM: -16M
[    0.000000]  gran_size: 256K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 256K     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000]  gran_size: 256K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 256K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 512K     chunk_size: 512K     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 512K     chunk_size: 1M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 512K     chunk_size: 2M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 512K     chunk_size: 4M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 512K     chunk_size: 8M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 512K     chunk_size: 16M     num_reg: 10      lose cover RAM: 48M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 32M     num_reg: 10      lose cover RAM: -16M
[    0.000000]  gran_size: 512K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 512K     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000]  gran_size: 512K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 512K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 1M     chunk_size: 1M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 1M     chunk_size: 2M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 1M     chunk_size: 4M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 1M     chunk_size: 8M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 1M     chunk_size: 16M     num_reg: 10      lose cover RAM: 48M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 32M     num_reg: 10      lose cover RAM: -16M
[    0.000000]  gran_size: 1M     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 1M     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000]  gran_size: 1M     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 1M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 2M     chunk_size: 2M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 2M     chunk_size: 4M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 2M     chunk_size: 8M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 2M     chunk_size: 16M     num_reg: 10      lose cover RAM: 48M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 32M     num_reg: 10      lose cover RAM: -16M
[    0.000000]  gran_size: 2M     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 2M     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000]  gran_size: 2M     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 2M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 4M     chunk_size: 4M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 4M     chunk_size: 8M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 4M     chunk_size: 16M     num_reg: 10      lose cover RAM: 48M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 32M     num_reg: 10      lose cover RAM: -16M
[    0.000000]  gran_size: 4M     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 4M     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 4M     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 4M     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000]  gran_size: 4M     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 4M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 8M     chunk_size: 8M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 8M     chunk_size: 16M     num_reg: 10      lose cover RAM: 48M
[    0.000000] *BAD*gran_size: 8M     chunk_size: 32M     num_reg: 10      lose cover RAM: -16M
[    0.000000]  gran_size: 8M     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 8M     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 8M     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 8M     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000]  gran_size: 8M     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 8M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 16M     chunk_size: 16M     num_reg: 10      lose cover RAM: 48M
[    0.000000] *BAD*gran_size: 16M     chunk_size: 32M     num_reg: 10      lose cover RAM: -16M
[    0.000000]  gran_size: 16M     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 16M     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 16M     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 16M     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000]  gran_size: 16M     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 16M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 32M     chunk_size: 32M     num_reg: 10      lose cover RAM: 32M
[    0.000000]  gran_size: 32M     chunk_size: 64M     num_reg: 9      lose cover RAM: 32M
[    0.000000]  gran_size: 32M     chunk_size: 128M     num_reg: 9      lose cover RAM: 32M
[    0.000000]  gran_size: 32M     chunk_size: 256M     num_reg: 9      lose cover RAM: 32M
[    0.000000]  gran_size: 32M     chunk_size: 512M     num_reg: 10      lose cover RAM: 32M
[    0.000000]  gran_size: 32M     chunk_size: 1G     num_reg: 9      lose cover RAM: 32M
[    0.000000]  gran_size: 32M     chunk_size: 2G     num_reg: 10      lose cover RAM: 32M
[    0.000000]  gran_size: 64M     chunk_size: 64M     num_reg: 9      lose cover RAM: 64M
[    0.000000]  gran_size: 64M     chunk_size: 128M     num_reg: 9      lose cover RAM: 64M
[    0.000000]  gran_size: 64M     chunk_size: 256M     num_reg: 9      lose cover RAM: 64M
[    0.000000]  gran_size: 64M     chunk_size: 512M     num_reg: 10      lose cover RAM: 64M
[    0.000000]  gran_size: 64M     chunk_size: 1G     num_reg: 9      lose cover RAM: 64M
[    0.000000]  gran_size: 64M     chunk_size: 2G     num_reg: 10      lose cover RAM: 64M
[    0.000000]  gran_size: 128M     chunk_size: 128M     num_reg: 7      lose cover RAM: 192M
[    0.000000]  gran_size: 128M     chunk_size: 256M     num_reg: 9      lose cover RAM: 192M
[    0.000000]  gran_size: 128M     chunk_size: 512M     num_reg: 10      lose cover RAM: 192M
[    0.000000]  gran_size: 128M     chunk_size: 1G     num_reg: 9      lose cover RAM: 192M
[    0.000000]  gran_size: 128M     chunk_size: 2G     num_reg: 10      lose cover RAM: 192M
[    0.000000]  gran_size: 256M     chunk_size: 256M     num_reg: 5      lose cover RAM: 448M
[    0.000000]  gran_size: 256M     chunk_size: 512M     num_reg: 5      lose cover RAM: 448M
[    0.000000]  gran_size: 256M     chunk_size: 1G     num_reg: 6      lose cover RAM: 448M
[    0.000000]  gran_size: 256M     chunk_size: 2G     num_reg: 7      lose cover RAM: 448M
[    0.000000]  gran_size: 512M     chunk_size: 512M     num_reg: 5      lose cover RAM: 448M
[    0.000000]  gran_size: 512M     chunk_size: 1G     num_reg: 6      lose cover RAM: 448M
[    0.000000]  gran_size: 512M     chunk_size: 2G     num_reg: 7      lose cover RAM: 448M
[    0.000000]  gran_size: 1G     chunk_size: 1G     num_reg: 4      lose cover RAM: 960M
[    0.000000]  gran_size: 1G     chunk_size: 2G     num_reg: 4      lose cover RAM: 960M
[    0.000000]  gran_size: 2G     chunk_size: 2G     num_reg: 3      lose cover RAM: 1984M
[    0.000000] mtrr_cleanup: can not find optimal value
[    0.000000] please specify mtrr_gran_size/mtrr_chunk_size
[    0.000000] e820: update [mem 0xcd000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcd000 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01ff0000, 0x01ff0fff] PGTABLE
[    0.000000] BRK [0x01ff1000, 0x01ff1fff] PGTABLE
[    0.000000] BRK [0x01ff2000, 0x01ff2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x42ee00000-0x42effffff]
[    0.000000]  [mem 0x42ee00000-0x42effffff] page 2M
[    0.000000] BRK [0x01ff3000, 0x01ff3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x420000000-0x42edfffff]
[    0.000000]  [mem 0x420000000-0x42edfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x400000000-0x41fffffff]
[    0.000000]  [mem 0x400000000-0x41fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xc630dfff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
[    0.000000]  [mem 0xc0000000-0xc61fffff] page 2M
[    0.000000]  [mem 0xc6200000-0xc630dfff] page 4k
[    0.000000] init_memory_mapping: [mem 0xc6680000-0xcbb83fff]
[    0.000000]  [mem 0xc6680000-0xc67fffff] page 4k
[    0.000000]  [mem 0xc6800000-0xcb9fffff] page 2M
[    0.000000]  [mem 0xcba00000-0xcbb83fff] page 4k
[    0.000000] BRK [0x01ff4000, 0x01ff4fff] PGTABLE
[    0.000000] BRK [0x01ff5000, 0x01ff5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xccfff000-0xccffffff]
[    0.000000]  [mem 0xccfff000-0xccffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x3ffffffff]
[    0.000000]  [mem 0x100000000-0x3ffffffff] page 1G
[    0.000000] RAMDISK: [mem 0x3e3d1000-0x3fffafff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000CBBEB000 000024 (v02 DELL  )
[    0.000000] ACPI: XSDT 0x00000000CBBEB0A8 0000CC (v01 DELL   QA09     01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x00000000CBBFD2D8 00010C (v05 DELL   QA09     01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x00000000CBBEB200 0120D7 (v02 DELL   QA09     01072009 INTL 20120913)
[    0.000000] ACPI: FACS 0x00000000CCD4CF80 000040
[    0.000000] ACPI: APIC 0x00000000CBBFD3E8 000084 (v03 DELL   QA09     01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x00000000CBBFD470 000044 (v01 DELL   QA09     01072009 AMI  00010013)
[    0.000000] ACPI: FIDT 0x00000000CBBFD4B8 00009C (v01 DELL   QA09     01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 0x00000000CBBFD558 00003C (v01 DELL   QA09     01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x00000000CBBFD598 000038 (v01 DELL   QA09     01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 0x00000000CBBFD5D0 0003B3 (v01 SataRe SataTabl 00001000 INTL 20120913)
[    0.000000] ACPI: UEFI 0x00000000CBBFD988 000042 (v01                 00000000      00000000)
[    0.000000] ACPI: MSDM 0x00000000CBBFD9D0 000055 (v03 DELL   QA09     01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 0x00000000CBBFDA28 0004E5 (v02 Ther_R Ther_Rvp 00001000 INTL 20120913)
[    0.000000] ACPI: ASF! 0x00000000CBBFDF10 0000A0 (v32 INTEL   HCG     00000001 TFSM 000F4240)
[    0.000000] ACPI: SSDT 0x00000000CBBFDFB0 000539 (v02 PmRef  Cpu0Ist  00003000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x00000000CBBFE4F0 000B74 (v02 CpuRef CpuSsdt  00003000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x00000000CBBFF068 006014 (v02 DptfTa DptfTabl 00001000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x00000000CBC05080 005545 (v02 SaSsdt SaSsdt   00003000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x00000000CBC0A5C8 000510 (v02 SgRef  SgPch    00001000 INTL 20120913)
[    0.000000] ACPI: DMAR 0x00000000CBC0AAD8 0000D4 (v01 INTEL  BDW      00000001 INTL 00000001)
[    0.000000] ACPI: CSRT 0x00000000CBC0ABB0 0000C4 (v01 INTL   BDW-ULT  00000001 INTL 20100528)
[    0.000000] ACPI: BGRT 0x00000000CBC0AC78 000038 (v01 DELL   QA09     01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 0x00000000CBC0ACB0 000D9E (v01 AmdRef AmdTabl  00001000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x00000000CBC0BA50 0005C3 (v02 Intel_ IsctTabl 00001000 INTL 20120913)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000042effffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x42eff8000-0x42effcfff]
[    0.000000]  [ffffea0000000000-ffffea0010bfffff] PMD -> [ffff88041e600000-ffff88042e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000042effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x0000000000057fff]
[    0.000000]   node   0: [mem 0x0000000000059000-0x000000000009dfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000c630dfff]
[    0.000000]   node   0: [mem 0x00000000c6680000-0x00000000cbb83fff]
[    0.000000]   node   0: [mem 0x00000000ccfff000-0x00000000ccffffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000042effffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000042effffff]
[    0.000000] On node 0 totalpages: 4171695
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12961 pages used for memmap
[    0.000000]   DMA32 zone: 829459 pages, LIFO batch:31
[    0.000000]   Normal zone: 52160 pages used for memmap
[    0.000000]   Normal zone: 3338240 pages, LIFO batch:31
[    0.000000] tboot: non-0 tboot_addr but it is not of type E820_RESERVED
[    0.000000] Reserving Intel graphics stolen memory at 0xce000000-0xcfffffff
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] low dfl lint[0x61])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x0])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl level lint[0x73])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] res dfl lint[0x0])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-39
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xc538d000-0xc538dfff]
[    0.000000] PM: Registered nosave memory: [mem 0xc539b000-0xc539bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xc539c000-0xc539cfff]
[    0.000000] PM: Registered nosave memory: [mem 0xc53ac000-0xc53acfff]
[    0.000000] PM: Registered nosave memory: [mem 0xc630e000-0xc667ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcbb84000-0xcbbe2fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcbbe3000-0xcbc0cfff]
[    0.000000] PM: Registered nosave memory: [mem 0xcbc0d000-0xccd50fff]
[    0.000000] PM: Registered nosave memory: [mem 0xccd51000-0xccffefff]
[    0.000000] PM: Registered nosave memory: [mem 0xcd000000-0xcd7fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcd800000-0xcfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xd0000000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xd0000000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88042ec00000 s96728 r8192 d30248 u524288
[    0.000000] pcpu-alloc: s96728 r8192 d30248 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 4106489
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-23-generic.efi.signed root=UUID=cea9bfa6-81da-400b-a577-7b7c208bc428 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16214900K/16686780K available (8148K kernel code, 1237K rwdata, 3800K rodata, 1460K init, 1292K bss, 471880K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 64.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=4
[    0.000000] NR_IRQS:16640 nr_irqs:728 16
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-3.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] tsc: Detected 2394.382 MHz processor
[    0.000023] Calibrating delay loop (skipped), value calculated using timer frequency.. 4788.76 BogoMIPS (lpj=9577528)
[    0.000025] pid_max: default: 32768 minimum: 301
[    0.000028] ACPI: Core revision 20150619
[    0.017973] ACPI: All ACPI Tables successfully acquired
[    0.018392] Security Framework initialized
[    0.018398] AppArmor: AppArmor initialized
[    0.018399] Yama: becoming mindful.
[    0.019182] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.021620] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.022662] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.022676] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.022857] Initializing cgroup subsys blkio
[    0.022859] Initializing cgroup subsys memory
[    0.022864] Initializing cgroup subsys devices
[    0.022866] Initializing cgroup subsys freezer
[    0.022867] Initializing cgroup subsys net_cls
[    0.022869] Initializing cgroup subsys perf_event
[    0.022870] Initializing cgroup subsys net_prio
[    0.022872] Initializing cgroup subsys hugetlb
[    0.022890] CPU: Physical Processor ID: 0
[    0.022891] CPU: Processor Core ID: 0
[    0.022894] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.022895] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.023814] mce: CPU supports 7 MCE banks
[    0.023823] CPU0: Thermal monitoring enabled (TM1)
[    0.023830] process: using mwait in idle threads
[    0.023832] Last level iTLB entries: 4KB 64, 2MB 8, 4MB 8
[    0.023833] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
[    0.024113] Freeing SMP alternatives memory: 28K (ffffffff81ea4000 - ffffffff81eab000)
[    0.044945] ftrace: allocating 30910 entries in 121 pages
[    0.055589] DMAR: Host address width 39
[    0.055591] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.055600] DMAR: dmar0: reg_base_addr fed90000 ver 1:0 cap 1c0000c40660462 ecap 7e1ff0505e
[    0.055601] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.055604] DMAR: dmar1: reg_base_addr fed91000 ver 1:0 cap d2008c20660462 ecap f010da
[    0.055605] DMAR: RMRR base: 0x000000ccf05000 end: 0x000000ccf13fff
[    0.055606] DMAR: RMRR base: 0x000000cd800000 end: 0x000000cfffffff
[    0.055607] DMAR: ANDD device: 1 name: \_SB.PCI0.SDMA
[    0.055609] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.055610] DMAR-IR: HPET id 0 under DRHD base 0xfed91000
[    0.055610] DMAR-IR: x2apic is disabled because BIOS sets x2apic opt out bit.
[    0.055611] DMAR-IR: Use 'intremap=no_x2apic_optout' to override the BIOS setting.
[    0.055980] DMAR-IR: Enabled IRQ remapping in xapic mode
[    0.055981] x2apic: IRQ remapping doesn't support X2APIC mode
[    0.056576] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.096295] TSC deadline timer enabled
[    0.096297] smpboot: CPU0: Intel(R) Core(TM) i7-5500U CPU @ 2.40GHz (fam: 06, model: 3d, stepping: 04)
[    0.096319] Performance Events: PEBS fmt2+, 16-deep LBR, Broadwell events, full-width counters, Intel PMU driver.
[    0.096334] ... version:                3
[    0.096335] ... bit width:              48
[    0.096336] ... generic registers:      4
[    0.096336] ... value mask:             0000ffffffffffff
[    0.096337] ... max period:             0000ffffffffffff
[    0.096338] ... fixed-purpose events:   3
[    0.096338] ... event mask:             000000070000000f
[    0.096963] x86: Booting SMP configuration:
[    0.096964] .... node  #0, CPUs:      #1
[    0.101137] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.101197]  #2 #3
[    0.109498] x86: Booted up 1 node, 4 CPUs
[    0.109500] smpboot: Total of 4 processors activated (19155.05 BogoMIPS)
[    0.113203] devtmpfs: initialized
[    0.115276] evm: security.selinux
[    0.115277] evm: security.SMACK64
[    0.115278] evm: security.SMACK64EXEC
[    0.115279] evm: security.SMACK64TRANSMUTE
[    0.115279] evm: security.SMACK64MMAP
[    0.115280] evm: security.ima
[    0.115281] evm: security.capability
[    0.115318] PM: Registering ACPI NVS region [mem 0xcbc0d000-0xccd50fff] (18104320 bytes)
[    0.115525] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.115583] pinctrl core: initialized pinctrl subsystem
[    0.115665] RTC time: 20:38:18, date: 01/06/16
[    0.115750] NET: Registered protocol family 16
[    0.125133] cpuidle: using governor ladder
[    0.129141] cpuidle: using governor menu
[    0.129216] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.129217] ACPI: bus type PCI registered
[    0.129219] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.129272] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.129274] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.129279] PCI: Using configuration type 1 for base access
[    0.133796] ACPI: Added _OSI(Module Device)
[    0.133798] ACPI: Added _OSI(Processor Device)
[    0.133799] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.133800] ACPI: Added _OSI(Processor Aggregator Device)
[    0.138074] ACPI: Executed 10 blocks of module-level executable AML code
[    0.142139] ACPI: Dynamic OEM Table Load:
[    0.142144] ACPI: SSDT 0xFFFF88041BE19C00 0003D3 (v02 PmRef  Cpu0Cst  00003001 INTL 20120913)
[    0.142799] ACPI: Dynamic OEM Table Load:
[    0.142803] ACPI: SSDT 0xFFFF88041BDE2800 0005AA (v02 PmRef  ApIst    00003000 INTL 20120913)
[    0.143491] ACPI: Dynamic OEM Table Load:
[    0.143494] ACPI: SSDT 0xFFFF88041BE16A00 000119 (v02 PmRef  ApCst    00003000 INTL 20120913)
[    0.144548] ACPI : EC: EC started
[    0.145335] ACPI: Interpreter enabled
[    0.145345] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150619/hwxface-580)
[    0.145352] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150619/hwxface-580)
[    0.145371] ACPI: (supports S0 S3 S4 S5)
[    0.145372] ACPI: Using IOAPIC for interrupt routing
[    0.145404] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.148076] ACPI: Power Resource [PC05] (on)
[    0.153304] ACPI: Power Resource [FN00] (off)
[    0.153803] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.153808] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.153890] \_SB_.PCI0:_OSC invalid UUID
[    0.153891] _OSC request data:1 1f 0 
[    0.153893] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.154124] PCI host bridge to bus 0000:00
[    0.154126] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.154128] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.154129] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.154130] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.154131] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff window]
[    0.154132] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff window]
[    0.154134] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff window]
[    0.154135] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff window]
[    0.154136] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff window]
[    0.154137] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff window]
[    0.154138] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff window]
[    0.154139] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff window]
[    0.154140] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff window]
[    0.154141] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff window]
[    0.154142] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff window]
[    0.154143] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff window]
[    0.154144] pci_bus 0000:00: root bus resource [mem 0xd0000000-0xfeafffff window]
[    0.154150] pci 0000:00:00.0: [8086:1604] type 00 class 0x060000
[    0.154219] pci 0000:00:02.0: [8086:1616] type 00 class 0x030000
[    0.154230] pci 0000:00:02.0: reg 0x10: [mem 0xf6000000-0xf6ffffff 64bit]
[    0.154235] pci 0000:00:02.0: reg 0x18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.154239] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.154299] pci 0000:00:03.0: [8086:160c] type 00 class 0x040300
[    0.154309] pci 0000:00:03.0: reg 0x10: [mem 0xf7214000-0xf7217fff 64bit]
[    0.154383] pci 0000:00:14.0: [8086:9cb1] type 00 class 0x0c0330
[    0.154403] pci 0000:00:14.0: reg 0x10: [mem 0xf7200000-0xf720ffff 64bit]
[    0.154442] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.154479] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.154507] pci 0000:00:16.0: [8086:9cba] type 00 class 0x078000
[    0.154531] pci 0000:00:16.0: reg 0x10: [mem 0xf721c000-0xf721c01f 64bit]
[    0.154578] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.154647] pci 0000:00:1b.0: [8086:9ca0] type 00 class 0x040300
[    0.154665] pci 0000:00:1b.0: reg 0x10: [mem 0xf7210000-0xf7213fff 64bit]
[    0.154697] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.154738] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.154764] pci 0000:00:1c.0: [8086:9c90] type 01 class 0x060400
[    0.154816] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.154872] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.154899] pci 0000:00:1c.3: [8086:9c96] type 01 class 0x060400
[    0.154954] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.155006] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.155031] pci 0000:00:1c.4: [8086:9c98] type 01 class 0x060400
[    0.155079] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.155129] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.155158] pci 0000:00:1d.0: [8086:9ca6] type 00 class 0x0c0320
[    0.155183] pci 0000:00:1d.0: reg 0x10: [mem 0xf721a000-0xf721a3ff]
[    0.155243] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.155281] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.155309] pci 0000:00:1f.0: [8086:9cc3] type 00 class 0x060100
[    0.155451] pci 0000:00:1f.2: [8086:9c83] type 00 class 0x010601
[    0.155467] pci 0000:00:1f.2: reg 0x10: [io  0xf0b0-0xf0b7]
[    0.155473] pci 0000:00:1f.2: reg 0x14: [io  0xf0a0-0xf0a3]
[    0.155478] pci 0000:00:1f.2: reg 0x18: [io  0xf090-0xf097]
[    0.155484] pci 0000:00:1f.2: reg 0x1c: [io  0xf080-0xf083]
[    0.155489] pci 0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f]
[    0.155495] pci 0000:00:1f.2: reg 0x24: [mem 0xf7219000-0xf72197ff]
[    0.155514] pci 0000:00:1f.2: PME# supported from D3hot
[    0.155564] pci 0000:00:1f.3: [8086:9ca2] type 00 class 0x0c0500
[    0.155576] pci 0000:00:1f.3: reg 0x10: [mem 0xf7218000-0xf72180ff 64bit]
[    0.155592] pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
[    0.155696] acpiphp: Slot [1] registered
[    0.155699] pci 0000:00:1c.0: PCI bridge to [bus 04]
[    0.155777] pci 0000:07:00.0: [8086:08b3] type 00 class 0x028000
[    0.155831] pci 0000:07:00.0: reg 0x10: [mem 0xf7100000-0xf7101fff 64bit]
[    0.155962] pci 0000:07:00.0: PME# supported from D0 D3hot D3cold
[    0.156006] pci 0000:07:00.0: System wakeup disabled by ACPI
[    0.165404] pci 0000:00:1c.3: PCI bridge to [bus 07]
[    0.165409] pci 0000:00:1c.3:   bridge window [mem 0xf7100000-0xf71fffff]
[    0.165465] pci 0000:08:00.0: [1002:6604] type 00 class 0x030000
[    0.165495] pci 0000:08:00.0: reg 0x10: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.165506] pci 0000:08:00.0: reg 0x18: [mem 0xf7000000-0xf703ffff 64bit]
[    0.165512] pci 0000:08:00.0: reg 0x20: [io  0xe000-0xe0ff]
[    0.165524] pci 0000:08:00.0: reg 0x30: [mem 0xf7040000-0xf705ffff pref]
[    0.165557] pci 0000:08:00.0: supports D1 D2
[    0.165558] pci 0000:08:00.0: PME# supported from D1 D2 D3hot
[    0.165584] pci 0000:08:00.0: System wakeup disabled by ACPI
[    0.177398] pci 0000:00:1c.4: PCI bridge to [bus 08]
[    0.177401] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
[    0.177404] pci 0000:00:1c.4:   bridge window [mem 0xf7000000-0xf70fffff]
[    0.177408] pci 0000:00:1c.4:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.178856] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.178891] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.178924] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.178956] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.178988] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.179020] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.179052] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.179085] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.179288] ACPI: Enabled 4 GPEs in block 00 to 7F
[    0.179324] ACPI : EC: GPE = 0xa, I/O: command/status = 0x66, data = 0x62
[    0.179395] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.179397] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.179401] vgaarb: device added: PCI:0000:08:00.0,decodes=io+mem,owns=none,locks=none
[    0.179401] vgaarb: loaded
[    0.179402] vgaarb: bridge control possible 0000:08:00.0
[    0.179403] vgaarb: no bridge control possible 0000:00:02.0
[    0.179588] SCSI subsystem initialized
[    0.179618] libata version 3.00 loaded.
[    0.179634] ACPI: bus type USB registered
[    0.179645] usbcore: registered new interface driver usbfs
[    0.179651] usbcore: registered new interface driver hub
[    0.179663] usbcore: registered new device driver usb
[    0.179794] PCI: Using ACPI for IRQ routing
[    0.180894] PCI: pci_cache_line_size set to 64 bytes
[    0.180949] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff]
[    0.180950] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
[    0.180950] e820: reserve RAM buffer [mem 0xc538d018-0xc7ffffff]
[    0.180952] e820: reserve RAM buffer [mem 0xc539c018-0xc7ffffff]
[    0.180953] e820: reserve RAM buffer [mem 0xc630e000-0xc7ffffff]
[    0.180953] e820: reserve RAM buffer [mem 0xcbb84000-0xcbffffff]
[    0.180954] e820: reserve RAM buffer [mem 0xcd000000-0xcfffffff]
[    0.180955] e820: reserve RAM buffer [mem 0x42f000000-0x42fffffff]
[    0.181030] NetLabel: Initializing
[    0.181031] NetLabel:  domain hash size = 128
[    0.181032] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.181039] NetLabel:  unlabeled traffic allowed by default
[    0.181089] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.181093] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.183116] clocksource: Switched to clocksource hpet
[    0.187638] AppArmor: AppArmor Filesystem Enabled
[    0.187688] pnp: PnP ACPI init
[    0.187849] pnp 00:00: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.187927] system 00:01: [io  0x0680-0x069f] has been reserved
[    0.187929] system 00:01: [io  0xffff] has been reserved
[    0.187931] system 00:01: [io  0xffff] has been reserved
[    0.187932] system 00:01: [io  0xffff] has been reserved
[    0.187934] system 00:01: [io  0x1800-0x18fe] could not be reserved
[    0.187935] system 00:01: [io  0x164e-0x164f] has been reserved
[    0.187938] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.187971] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.188001] system 00:03: [io  0x1854-0x1857] has been reserved
[    0.188003] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.188163] system 00:04: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.188165] system 00:04: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.188167] system 00:04: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.188168] system 00:04: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.188170] system 00:04: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.188171] system 00:04: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.188173] system 00:04: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.188174] system 00:04: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.188176] system 00:04: [mem 0xff000000-0xffffffff] has been reserved
[    0.188177] system 00:04: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.188179] system 00:04: [mem 0xf7fe0000-0xf7feffff] has been reserved
[    0.188180] system 00:04: [mem 0xf7ff0000-0xf7ffffff] has been reserved
[    0.188182] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.188354] system 00:05: [mem 0xfe102000-0xfe102fff] has been reserved
[    0.188356] system 00:05: [mem 0xfe106000-0xfe106fff] has been reserved
[    0.188358] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.188751] pnp: PnP ACPI: found 6 devices
[    0.194482] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.194495] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 04] add_size 1000
[    0.194497] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 04] add_size 200000 add_align 100000
[    0.194498] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 04] add_size 200000 add_align 100000
[    0.194512] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.194513] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.194514] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.194516] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.194517] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.194518] pci 0000:00:1c.0: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.194524] pci 0000:00:1c.0: BAR 14: assigned [mem 0xf0000000-0xf01fffff]
[    0.194530] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf0200000-0xf03fffff 64bit pref]
[    0.194532] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.194534] pci 0000:00:1c.0: PCI bridge to [bus 04]
[    0.194536] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.194540] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf01fffff]
[    0.194543] pci 0000:00:1c.0:   bridge window [mem 0xf0200000-0xf03fffff 64bit pref]
[    0.194547] pci 0000:00:1c.3: PCI bridge to [bus 07]
[    0.194550] pci 0000:00:1c.3:   bridge window [mem 0xf7100000-0xf71fffff]
[    0.194556] pci 0000:00:1c.4: PCI bridge to [bus 08]
[    0.194558] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
[    0.194561] pci 0000:00:1c.4:   bridge window [mem 0xf7000000-0xf70fffff]
[    0.194564] pci 0000:00:1c.4:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.194568] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.194569] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.194571] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.194572] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff window]
[    0.194573] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff window]
[    0.194574] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff window]
[    0.194575] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff window]
[    0.194576] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff window]
[    0.194577] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff window]
[    0.194578] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff window]
[    0.194579] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff window]
[    0.194580] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff window]
[    0.194581] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff window]
[    0.194582] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff window]
[    0.194584] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff window]
[    0.194585] pci_bus 0000:00: resource 19 [mem 0xd0000000-0xfeafffff window]
[    0.194586] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
[    0.194587] pci_bus 0000:04: resource 1 [mem 0xf0000000-0xf01fffff]
[    0.194588] pci_bus 0000:04: resource 2 [mem 0xf0200000-0xf03fffff 64bit pref]
[    0.194589] pci_bus 0000:07: resource 1 [mem 0xf7100000-0xf71fffff]
[    0.194590] pci_bus 0000:08: resource 0 [io  0xe000-0xefff]
[    0.194591] pci_bus 0000:08: resource 1 [mem 0xf7000000-0xf70fffff]
[    0.194592] pci_bus 0000:08: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.194615] NET: Registered protocol family 2
[    0.194764] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.194921] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.195017] TCP: Hash tables configured (established 131072 bind 65536)
[    0.195044] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.195082] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.195140] NET: Registered protocol family 1
[    0.195151] pci 0000:00:02.0: Video device with shadowed ROM
[    0.215244] PCI: CLS 64 bytes, default 64
[    0.215286] Trying to unpack rootfs image as initramfs...
[    0.562101] Freeing initrd memory: 28840K (ffff88003e3d1000 - ffff88003fffb000)
[    0.562135] DMAR: ACPI device "INTL9C60:00" under DMAR at fed91000 as 00:15.0
[    0.562143] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.562144] software IO TLB [mem 0xbe696000-0xc2696000] (64MB) mapped at [ffff8800be696000-ffff8800c2695fff]
[    0.562193] RAPL PMU detected, API unit is 2^-32 Joules, 4 fixed counters 655360 ms ovfl timer
[    0.562194] hw unit of domain pp0-core 2^-14 Joules
[    0.562195] hw unit of domain package 2^-14 Joules
[    0.562195] hw unit of domain dram 2^-14 Joules
[    0.562196] hw unit of domain pp1-gpu 2^-14 Joules
[    0.562282] microcode: CPU0 sig=0x306d4, pf=0x40, revision=0x19
[    0.562288] microcode: CPU1 sig=0x306d4, pf=0x40, revision=0x19
[    0.562291] microcode: CPU2 sig=0x306d4, pf=0x40, revision=0x19
[    0.562296] microcode: CPU3 sig=0x306d4, pf=0x40, revision=0x19
[    0.562330] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.562392] Scanning for low memory corruption every 60 seconds
[    0.562602] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.562613] Initialise system trusted keyring
[    0.562634] audit: initializing netlink subsys (disabled)
[    0.562646] audit: type=2000 audit(1452112698.544:1): initialized
[    0.562910] HugeTLB registered 1 GB page size, pre-allocated 0 pages
[    0.562911] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.564014] zpool: loaded
[    0.564017] zbud: loaded
[    0.564144] VFS: Disk quotas dquot_6.6.0
[    0.564167] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.564494] fuse init (API version 7.23)
[    0.564592] Key type big_key registered
[    0.564822] Key type asymmetric registered
[    0.564823] Asymmetric key parser 'x509' registered
[    0.564833] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.564859] io scheduler noop registered
[    0.564861] io scheduler deadline registered (default)
[    0.564883] io scheduler cfq registered
[    0.565193] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.565197] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.565227] efifb: probing for efifb
[    0.565237] efifb: framebuffer at 0xd0000000, mapped to 0xffffc90002000000, using 7500k, total 7500k
[    0.565238] efifb: mode is 1600x1200x32, linelength=6400, pages=1
[    0.565238] efifb: scrolling: redraw
[    0.565240] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.565309] Console: switching to colour frame buffer device 200x75
[    0.565326] fb0: EFI VGA frame buffer device
[    0.565332] intel_idle: MWAIT substates: 0x11142120
[    0.565333] intel_idle: v0.4 model 0x3D
[    0.565334] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.565534] ACPI: AC Adapter [ADP1] (on-line)
[    0.565592] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.565594] ACPI: Sleep Button [SLPB]
[    0.565619] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.565620] ACPI: Power Button [PWRB]
[    0.565646] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.565866] ACPI: Lid Switch [LID0]
[    0.565892] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.565894] ACPI: Power Button [PWRF]
[    0.566109] thermal LNXTHERM:00: registered as thermal_zone0
[    0.566111] ACPI: Thermal Zone [TZ00] (28 C)
[    0.566239] thermal LNXTHERM:01: registered as thermal_zone1
[    0.566240] ACPI: Thermal Zone [TZ01] (30 C)
[    0.566286] GHES: HEST is not enabled!
[    0.566349] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.570117] ACPI: Battery Slot [BAT0] (battery present)
[    0.570276] Linux agpgart interface v0.103
[    0.571831] brd: module loaded
[    0.572481] loop: module loaded
[    0.572651] libphy: Fixed MDIO Bus: probed
[    0.572653] tun: Universal TUN/TAP device driver, 1.6
[    0.572654] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.572685] PPP generic driver version 2.4.2
[    0.572817] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.572822] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.573878] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00009810
[    0.573882] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.573938] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.573939] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.573940] usb usb1: Product: xHCI Host Controller
[    0.573941] usb usb1: Manufacturer: Linux 4.2.0-23-generic xhci-hcd
[    0.573942] usb usb1: SerialNumber: 0000:00:14.0
[    0.574019] hub 1-0:1.0: USB hub found
[    0.574028] hub 1-0:1.0: 11 ports detected
[    0.576462] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.576465] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.576485] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.576487] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.576487] usb usb2: Product: xHCI Host Controller
[    0.576489] usb usb2: Manufacturer: Linux 4.2.0-23-generic xhci-hcd
[    0.576489] usb usb2: SerialNumber: 0000:00:14.0
[    0.576558] hub 2-0:1.0: USB hub found
[    0.576564] hub 2-0:1.0: 4 ports detected
[    0.577492] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.577499] ehci-pci: EHCI PCI platform driver
[    0.577566] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.577569] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    0.577578] ehci-pci 0000:00:1d.0: debug port 2
[    0.581468] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.581478] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf721a000
[    0.591456] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.591482] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.591484] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.591485] usb usb3: Product: EHCI Host Controller
[    0.591486] usb usb3: Manufacturer: Linux 4.2.0-23-generic ehci_hcd
[    0.591487] usb usb3: SerialNumber: 0000:00:1d.0
[    0.591575] hub 3-0:1.0: USB hub found
[    0.591578] hub 3-0:1.0: 2 ports detected
[    0.591669] ehci-platform: EHCI generic platform driver
[    0.591678] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.591682] ohci-pci: OHCI PCI platform driver
[    0.591690] ohci-platform: OHCI generic platform driver
[    0.591697] uhci_hcd: USB Universal Host Controller Interface driver
[    0.591734] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.591735] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.592650] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.592737] mousedev: PS/2 mouse device common for all mice
[    0.592873] rtc_cmos 00:02: RTC can wake from S4
[    0.592984] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.593009] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.593015] i2c /dev entries driver
[    0.593066] device-mapper: uevent: version 1.0.3
[    0.593132] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
[    0.593143] Intel P-state driver initializing.
[    0.593290] ledtrig-cpu: registered to indicate activity on CPUs
[    0.593299] EFI Variables Facility v0.08 2004-May-17
[    0.597483] PCCT header not found.
[    0.598060] NET: Registered protocol family 10
[    0.598472] NET: Registered protocol family 17
[    0.598527] Key type dns_resolver registered
[    0.598753] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.599423] Loading compiled-in X.509 certificates
[    0.600185] Loaded X.509 cert 'Build time autogenerated kernel key: 5b77c7b2b6447c14c514ab2aee8004bfbd7c3913'
[    0.600199] registered taskstats version 1
[    0.600215] zswap: loading zswap
[    0.600216] zswap: using zbud pool
[    0.600220] zswap: using lzo compressor
[    0.601789] Key type trusted registered
[    0.604327] Key type encrypted registered
[    0.604334] AppArmor: AppArmor sha1 policy hashing enabled
[    0.604337] ima: No TPM chip found, activating TPM-bypass!
[    0.604353] evm: HMAC attrs: 0x1
[    0.604645]   Magic number: 0:123:649
[    0.604689] acpi LNXCPU:02: hash matches
[    0.604733] rtc_cmos 00:02: setting system clock to 2016-01-06 20:38:19 UTC (1452112699)
[    0.604782] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.604783] EDD information not available.
[    0.604858] PM: Hibernation image not present or could not be loaded.
[    0.605172] Freeing unused kernel memory: 1460K (ffffffff81d37000 - ffffffff81ea4000)
[    0.605173] Write protecting the kernel read-only data: 12288k
[    0.605306] Freeing unused kernel memory: 32K (ffff8800017f8000 - ffff880001800000)
[    0.605376] Freeing unused kernel memory: 296K (ffff880001bb6000 - ffff880001c00000)
[    0.614347] random: systemd-udevd urandom read with 7 bits of entropy available
[    0.639150] hidraw: raw HID events driver (C) Jiri Kosina
[    0.649836] wmi: Mapper loaded
[    0.656474] [drm] Initialized drm 1.1.0 20060810
[    0.657934] ahci 0000:00:1f.2: version 3.0
[    0.671539] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0x2 impl SATA mode
[    0.671544] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo only pio slum part deso sadm sds apst 
[    0.675554] scsi host0: ahci
[    0.679593] scsi host1: ahci
[    0.679691] scsi host2: ahci
[    0.679761] scsi host3: ahci
[    0.679800] ata1: DUMMY
[    0.679802] ata2: SATA max UDMA/133 abar m2048@0xf7219000 port 0xf7219180 irq 43
[    0.679803] ata3: DUMMY
[    0.679804] ata4: DUMMY
[    0.681967] [drm] Memory usable by graphics device = 4096M
[    0.681971] checking generic (d0000000 753000) vs hw (d0000000 10000000)
[    0.681972] fb: switching to inteldrmfb from EFI VGA
[    0.682008] Console: switching to colour dummy device 80x25
[    0.682075] [drm] Replacing VGA console driver
[    0.688631] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    0.688634] [drm] Driver supports precise vblank timestamp query.
[    0.688750] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    0.710588] [drm:gen8_irq_handler [i915]] *ERROR* The master control interrupt lied (SDE)!
[    0.710761] [drm:gen8_irq_handler [i915]] *ERROR* The master control interrupt lied (SDE)!
[    0.711290] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    0.711630] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    0.711757] [drm] Initialized i915 1.6.0 20150522 for 0000:00:02.0 on minor 0
[    0.728050] fbcon: inteldrmfb (fb0) is primary device
[    0.728141] Console: switching to colour frame buffer device 480x135
[    0.728245] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    0.728247] i915 0000:00:02.0: registered panic notifier
[    0.887742] usb 1-5: new high-speed USB device number 2 using xhci_hcd
[    0.903756] usb 3-1: new high-speed USB device number 2 using ehci-pci
[    0.999840] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.036299] usb 3-1: New USB device found, idVendor=8087, idProduct=8001
[    1.036302] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.036574] hub 3-1:1.0: USB hub found
[    1.036640] hub 3-1:1.0: 8 ports detected
[    1.084415] ata2.00: ATA-8: TOSHIBA MQ02ABF100, DS001D, max UDMA/100
[    1.084418] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.086007] ata2.00: configured for UDMA/100
[    1.086183] scsi 1:0:0:0: Direct-Access     ATA      TOSHIBA MQ02ABF1 1D   PQ: 0 ANSI: 5
[    1.086498] sd 1:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.086502] sd 1:0:0:0: [sda] 4096-byte physical blocks
[    1.086524] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.086530] sd 1:0:0:0: [sda] Write Protect is off
[    1.086534] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.086563] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.123631] usb 1-5: New USB device found, idVendor=1bcf, idProduct=2b8a
[    1.123634] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.123636] usb 1-5: Product: Integrated_Webcam_HD
[    1.123637] usb 1-5: Manufacturer: SunplusIT Inc
[    1.223515]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9
[    1.224530] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.360086] usb 1-6: new full-speed USB device number 3 using xhci_hcd
[    1.489474] usb 1-6: New USB device found, idVendor=04f3, idProduct=2098
[    1.489477] usb 1-6: New USB device strings: Mfr=4, Product=14, SerialNumber=0
[    1.489478] usb 1-6: Product: Touchscreen
[    1.489480] usb 1-6: Manufacturer: ELAN
[    1.489579] usb 1-6: ep 0x2 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.497069] usbcore: registered new interface driver usbhid
[    1.497071] usbhid: USB HID core driver
[    1.560254] tsc: Refined TSC clocksource calibration: 2394.456 MHz
[    1.560257] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2283c236f90, max_idle_ns: 440795217409 ns
[    1.656324] usb 1-7: new full-speed USB device number 4 using xhci_hcd
[    1.785319] usb 1-7: New USB device found, idVendor=8087, idProduct=07dc
[    1.785322] usb 1-7: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.023746] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[    2.561235] clocksource: Switched to clocksource tsc
[    2.652470] random: nonblocking pool is initialized
[    2.705393] systemd[1]: RTC configured in localtime, applying delta of 60 minutes to system time.
[    3.054050] systemd[1]: Failed to insert module 'kdbus': Function not implemented
[    3.248522] systemd[1]: systemd 225 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[    3.248626] systemd[1]: Detected architecture x86-64.
[    3.261227] systemd[1]: Set hostname to <vulcan>.
[    4.036088] systemd[1]: syncthing-inotify@frydatom.service: Cannot add dependency job, ignoring: Unit syncthing-inotify@frydatom.service failed to load: No such file or directory.
[    4.036540] systemd[1]: Created slice Root Slice.
[    4.036610] systemd[1]: Listening on Journal Socket.
[    4.036643] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    4.036672] systemd[1]: Listening on udev Control Socket.
[    4.036683] systemd[1]: Reached target Remote File Systems (Pre).
[    4.036689] systemd[1]: Reached target User and Group Name Lookups.
[    4.036758] systemd[1]: Created slice System Slice.
[    4.037110] systemd[1]: Starting Setup Virtual Console...
[    4.037479] systemd[1]: Started Read required files in advance.
[    4.037986] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    4.038309] systemd[1]: Started Braille Device Support.
[    4.262734] systemd[1]: Starting Load Kernel Modules...
[    4.262788] systemd[1]: Listening on Journal Socket (/dev/log).
[    4.263208] systemd[1]: Mounting Debug File System...
[    4.263274] systemd[1]: Created slice User and Session Slice.
[    4.263289] systemd[1]: Reached target Slices.
[    4.263320] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    4.263342] systemd[1]: Listening on fsck to fsckd communication Socket.
[    4.263692] systemd[1]: Mounting Huge Pages File System...
[    4.264017] systemd[1]: Starting Uncomplicated firewall...
[    4.264501] systemd[1]: Starting Increase datagram queue length...
[    4.264601] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[    4.264670] systemd[1]: Created slice system-syncthing.slice.
[    4.264728] systemd[1]: Created slice system-getty.slice.
[    4.264876] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    4.293157] systemd[1]: Listening on Journal Audit Socket.
[    4.293177] systemd[1]: Reached target Encrypted Volumes.
[    4.293196] systemd[1]: Listening on udev Kernel Socket.
[    4.293576] systemd[1]: Starting udev Coldplug all Devices...
[    4.293951] systemd[1]: Mounting POSIX Message Queue File System...
[    4.294836] systemd[1]: Started Setup Virtual Console.
[    4.294978] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    4.296555] systemd[1]: Starting Create Static Device Nodes in /dev...
[    4.344512] systemd[1]: Started Uncomplicated firewall.
[    4.512973] systemd[1]: Started udev Coldplug all Devices.
[    4.539798] systemd[1]: Started Increase datagram queue length.
[    4.539915] systemd[1]: Listening on Syslog Socket.
[    4.540434] systemd[1]: Starting Journal Service...
[    4.706477] systemd[1]: Mounted Huge Pages File System.
[    4.706507] systemd[1]: Mounted POSIX Message Queue File System.
[    4.707162] systemd[1]: Mounted Debug File System.
[    5.127137] systemd[1]: Started Journal Service.
[    5.143045] lp: driver loaded but no devices found
[    5.178329] ppdev: user-space parallel port driver
[    5.771554] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
[    5.827443] systemd-journald[233]: Received request to flush runtime journal from PID 1
[    6.211386] dw_dmac INTL9C60:00: DesignWare DMA Controller, 8 channels
[    6.215166] input: DELL Wireless hotkeys as /devices/virtual/input/input6
[    6.256732] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    6.893276] AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>
[    6.893279] AMD IOMMUv2 functionality not available on this system
[    7.088532] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    7.272478] input: Dell WMI hotkeys as /devices/virtual/input/input7
[    7.275969] media: Linux media interface: v0.10
[    7.300658] input: ELAN Touchscreen as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:04F3:2098.0001/input/input8
[    7.300785] hid-multitouch 0003:04F3:2098.0001: input,hiddev0,hidraw0: USB HID v1.10 Device [ELAN Touchscreen] on usb-0000:00:14.0-6/input0
[    7.303224] i2c_hid i2c-MSFT0001:00: failed to retrieve report from device.
[    7.310807] i2c_hid i2c-MSFT0001:00: failed to retrieve report from device.
[    7.311591] i2c_hid i2c-MSFT0001:00: failed to retrieve report from device.
[    7.312396] i2c_hid i2c-MSFT0001:00: failed to retrieve report from device.
[    7.313186] i2c_hid i2c-MSFT0001:00: failed to retrieve report from device.
[    7.313241] input: MSFT0001:00 06CB:75BD UNKNOWN as /devices/pci0000:00/INT3433:00/i2c-5/i2c-MSFT0001:00/0018:06CB:75BD.0002/input/input10
[    7.313364] hid-multitouch 0018:06CB:75BD.0002: input,hidraw1: <UNKNOWN> HID v1.00 Mouse [MSFT0001:00 06CB:75BD] on 
[    7.479643] Intel(R) Wireless WiFi driver for Linux
[    7.479645] Copyright(c) 2003- 2015 Intel Corporation
[    7.479702] iwlwifi 0000:07:00.0: enabling device (0000 -> 0002)
[    7.480185] iwlwifi 0000:07:00.0: Unsupported splx structure
[    7.487697] Bluetooth: Core ver 2.20
[    7.487707] NET: Registered protocol family 31
[    7.487708] Bluetooth: HCI device and connection manager initialized
[    7.487711] Bluetooth: HCI socket layer initialized
[    7.487712] Bluetooth: L2CAP socket layer initialized
[    7.487716] Bluetooth: SCO socket layer initialized
[    7.553114] Linux video capture interface: v2.00
[    7.645832] iwlwifi 0000:07:00.0: Direct firmware load for iwlwifi-3160-15.ucode failed with error -2
[    7.645847] iwlwifi 0000:07:00.0: Direct firmware load for iwlwifi-3160-14.ucode failed with error -2
[    7.775666] iwlwifi 0000:07:00.0: loaded firmware version 25.30.13.0 op_mode iwlmvm
[    7.853430] usbcore: registered new interface driver btusb
[    7.867030] Bluetooth: hci0: read Intel version: 3707100100012d0d1a
[    7.867032] Bluetooth: hci0: Intel device is already patched. patch num: 1a
[    7.870264] AVX2 version of gcm_enc/dec engaged.
[    7.870266] AES CTR mode by8 optimization enabled
[    8.154883] iwlwifi 0000:07:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[    8.154951] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[    8.155202] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[    8.159785] snd_hda_intel 0000:00:03.0: enabling device (0000 -> 0002)
[    8.159891] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    8.159921] snd_hda_intel 0000:00:1b.0: enabling device (0000 -> 0002)
[    8.206000] snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC3234: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    8.206003] snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    8.206005] snd_hda_codec_realtek hdaudioC1D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    8.206006] snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0
[    8.206007] snd_hda_codec_realtek hdaudioC1D0:    inputs:
[    8.206009] snd_hda_codec_realtek hdaudioC1D0:      Headset Mic=0x19
[    8.206010] snd_hda_codec_realtek hdaudioC1D0:      Headphone Mic=0x1a
[    8.206012] snd_hda_codec_realtek hdaudioC1D0:      Internal Mic=0x12
[    8.298491] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    8.406731] input: HDA Intel PCH Headphone Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input12
[    8.435934] iwlwifi 0000:07:00.0 wlp7s0: renamed from wlan0
[    8.578299] uvcvideo: Found UVC 1.00 device Integrated_Webcam_HD (1bcf:2b8a)
[    8.586887] input: Integrated_Webcam_HD as /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/input/input13
[    8.586939] usbcore: registered new interface driver uvcvideo
[    8.586941] USB Video Class driver (1.1.1)
[    8.605185] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input14
[    8.733941] cfg80211: World regulatory domain updated:
[    8.733944] cfg80211:  DFS Master region: unset
[    8.733945] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[    8.733947] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    8.733948] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    8.733949] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[    8.733951] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[    8.733953] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[    8.733954] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[    8.733955] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[    8.733956] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[    8.889755] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    8.889757] Disabling lock debugging due to kernel taint
[    8.893585] fglrx: module verification failed: signature and/or required key missing - tainting kernel
[    8.902176] <6>[fglrx] Maximum main memory to use for locked dma buffers: 15586 MBytes.
[    8.902298] <6>[fglrx]   vendor: 1002 device: 6604 revision: 0 count: 1
[    8.902490] <6>[fglrx] ioport: bar 4, base 0xe000, size: 0x100
[    8.902499] pci 0000:08:00.0: enabling device (0000 -> 0003)
[    8.902655] <6>[fglrx] Kernel PAT support is enabled
[    8.902667] <6>[fglrx] module loaded - fglrx 15.20.3 [Sep  8 2015] with 1 minors
[   10.269888] intel_rapl: Found RAPL domain package
[   10.269892] intel_rapl: Found RAPL domain core
[   10.269894] intel_rapl: Found RAPL domain uncore
[   10.269896] intel_rapl: Found RAPL domain dram
[   10.325808] Adding 16687100k swap on /dev/sda8.  Priority:-1 extents:1 across:16687100k FS
[   19.072866] audit: type=1400 audit(1452109117.946:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=545 comm="apparmor_parser"
[   19.072872] audit: type=1400 audit(1452109117.946:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=545 comm="apparmor_parser"
[   19.074133] audit: type=1400 audit(1452109117.946:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=545 comm="apparmor_parser"
[   19.074138] audit: type=1400 audit(1452109117.946:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=545 comm="apparmor_parser"
[   19.074141] audit: type=1400 audit(1452109117.946:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=545 comm="apparmor_parser"
[   19.074143] audit: type=1400 audit(1452109117.946:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=545 comm="apparmor_parser"
[   19.080160] audit: type=1400 audit(1452109117.954:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=545 comm="apparmor_parser"
[   19.080176] audit: type=1400 audit(1452109117.954:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=545 comm="apparmor_parser"
[   19.080179] audit: type=1400 audit(1452109117.954:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=545 comm="apparmor_parser"
[   19.080183] audit: type=1400 audit(1452109117.954:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=545 comm="apparmor_parser"
[   19.451783] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.451786] Bluetooth: BNEP filters: protocol multicast
[   19.451790] Bluetooth: BNEP socket layer initialized
[   19.453572] cgroup: new mount options do not match the existing superblock, will be ignored
[   21.473709] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
[   21.473841] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[   21.474079] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[   21.597080] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[   21.597316] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[   21.610481] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
[   21.688547] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
[   23.964877] ip_tables: (C) 2000-2006 Netfilter Core Team
[   23.969752] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   24.008044] Ebtables v2.0 registered
[   24.139400] bridge: automatic filtering via arp/ip/ip6tables has been deprecated. Update your scripts to load br_netfilter if you need this.
[   24.178590] device virbr0-nic entered promiscuous mode
[   24.212979] [drm:gen8_irq_handler [i915]] *ERROR* The master control interrupt lied (SDE)!
[   24.279241] nf_conntrack version 0.5.0 (65536 buckets, 262144 max)
[   24.307549] virbr0: port 1(virbr0-nic) entered listening state
[   24.307564] virbr0: port 1(virbr0-nic) entered listening state
[   24.459602] virbr0: port 1(virbr0-nic) entered disabled state
[   25.066060] wlp7s0: authenticate with 80:1f:02:0e:0b:fa
[   25.069763] wlp7s0: send auth to 80:1f:02:0e:0b:fa (try 1/3)
[   25.150611] wlp7s0: authenticated
[   25.151292] wlp7s0: associate with 80:1f:02:0e:0b:fa (try 1/3)
[   25.155155] wlp7s0: RX AssocResp from 80:1f:02:0e:0b:fa (capab=0x411 status=0 aid=2)
[   25.157985] wlp7s0: associated
[   25.158010] IPv6: ADDRCONF(NETDEV_CHANGE): wlp7s0: link becomes ready
[   25.822041] <6>[fglrx] Firegl kernel thread PID: 1161
[   25.822086] <6>[fglrx] Firegl kernel thread PID: 1162
[   25.822146] <6>[fglrx] Firegl kernel thread PID: 1163
[   25.822246] <6>[fglrx] IRQ 49 Enabled
[   25.833118] <6>[fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   25.833119] <6>[fglrx] Reserved FB block: Unshared offset:f7b4000, size:4000 
[   25.833120] <6>[fglrx] Reserved FB block: Unshared offset:f7b8000, size:548000 
[   25.833121] <6>[fglrx] Reserved FB block: Unshared offset:ffff3000, size:d000 
[   30.995150] <6>[fglrx] IRQ 49 Disabled
[   36.506992] Bluetooth: RFCOMM TTY layer initialized
[   36.506998] Bluetooth: RFCOMM socket layer initialized
[   36.507002] Bluetooth: RFCOMM ver 1.11
[  666.866090] perf interrupt took too long (2518 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[ 4411.345409] wlp7s0: deauthenticating from 80:1f:02:0e:0b:fa by local choice (Reason: 3=DEAUTH_LEAVING)
[ 4411.359567] cfg80211: World regulatory domain updated:
[ 4411.359570] cfg80211:  DFS Master region: unset
[ 4411.359571] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[ 4411.359572] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[ 4411.359574] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[ 4411.359574] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[ 4411.359576] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[ 4411.359577] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[ 4411.359578] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[ 4411.359579] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[ 4411.359580] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[ 4412.631176] ------------[ cut here ]------------
[ 4412.631204] WARNING: CPU: 1 PID: 0 at /build/linux-AFqQDb/linux-4.2.0/drivers/gpu/drm/i915/intel_display.c:11102 intel_check_page_flip+0xfc/0x110 [i915]()
[ 4412.631206] Kicking stuck page flip: queued at 263617, now 263621
[ 4412.631207] Modules linked in: rfcomm drbg ansi_cprng ctr ccm xt_CHECKSUM iptable_mangle ipt_MASQUERADE nf_nat_masquerade_ipv4 iptable_nat nf_nat_ipv4 nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack nf_conntrack ipt_REJECT nf_reject_ipv4 xt_tcpudp bridge stp llc ebtable_filter ebtables ip6table_filter ip6_tables iptable_filter ip_tables x_tables bnep nls_iso8859_1 intel_rapl iosf_mbi x86_pkg_temp_thermal intel_powerclamp coretemp fglrx(POE) kvm_intel kvm snd_hda_codec_hdmi uvcvideo dell_led arc4 crct10dif_pclmul videobuf2_vmalloc snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel iwlmvm snd_hda_codec snd_hda_core snd_hwdep crc32_pclmul videobuf2_memops mac80211 snd_pcm aesni_intel btusb videobuf2_core snd_seq_midi btrtl snd_seq_midi_event btbcm v4l2_common btintel snd_rawmidi aes_x86_64
[ 4412.631243]  videodev snd_seq bluetooth iwlwifi lrw joydev gf128mul glue_helper input_leds hid_multitouch ablk_helper media dell_wmi cryptd sparse_keymap dell_laptop dcdbas dell_smm_hwmon amd_iommu_v2 serio_raw acpi_als snd_seq_device snd_timer mei_me kfifo_buf cfg80211 industrialio snd mei soundcore acpi_pad int3403_thermal shpchp int3400_thermal int3402_thermal acpi_thermal_rel int340x_thermal_zone lpc_ich dell_smo8800 dell_rbtn dw_dmac intel_smartconnect dw_dmac_core i2c_designware_platform i2c_designware_core mac_hid cuse parport_pc ppdev lp parport autofs4 usbhid i915 i2c_algo_bit drm_kms_helper ahci libahci drm wmi video i2c_hid hid
[ 4412.631278] CPU: 1 PID: 0 Comm: swapper/1 Tainted: P           OE   4.2.0-23-generic #28-Ubuntu
[ 4412.631280] Hardware name: Dell Inc. Inspiron 7548/0AM6R0, BIOS A05 07/20/2015
[ 4412.631281]  0000000000000000 e71d7133c45f5c74 ffff88042ec83d48 ffffffff817e94c9
[ 4412.631284]  0000000000000000 ffff88042ec83da0 ffff88042ec83d88 ffffffff8107b3d6
[ 4412.631286]  ffff88042ec83db8 ffff88041c33a800 ffff8804175f1000 ffff88041c33a9a8
[ 4412.631289] Call Trace:
[ 4412.631290]  <IRQ>  [<ffffffff817e94c9>] dump_stack+0x45/0x57
[ 4412.631297]  [<ffffffff8107b3d6>] warn_slowpath_common+0x86/0xc0
[ 4412.631299]  [<ffffffff8107b465>] warn_slowpath_fmt+0x55/0x70
[ 4412.631315]  [<ffffffffc018792c>] intel_check_page_flip+0xfc/0x110 [i915]
[ 4412.631328]  [<ffffffffc01505e5>] gen8_irq_handler+0x325/0x590 [i915]
[ 4412.631332]  [<ffffffff810d4284>] handle_irq_event_percpu+0x74/0x180
[ 4412.631334]  [<ffffffff810d43d9>] handle_irq_event+0x49/0x70
[ 4412.631336]  [<ffffffff810d7751>] handle_edge_irq+0x81/0x150
[ 4412.631339]  [<ffffffff810172b5>] handle_irq+0x25/0x40
[ 4412.631341]  [<ffffffff817f2eaf>] do_IRQ+0x4f/0xe0
[ 4412.631343]  [<ffffffff817f0e2b>] common_interrupt+0x6b/0x6b
[ 4412.631344]  <EOI>  [<ffffffff816870b0>] ? cpuidle_enter_state+0x130/0x270
[ 4412.631349]  [<ffffffff8168708b>] ? cpuidle_enter_state+0x10b/0x270
[ 4412.631351]  [<ffffffff81687227>] cpuidle_enter+0x17/0x20
[ 4412.631353]  [<ffffffff810bd4f2>] call_cpuidle+0x32/0x60
[ 4412.631355]  [<ffffffff81687203>] ? cpuidle_select+0x13/0x20
[ 4412.631357]  [<ffffffff810bd788>] cpu_startup_entry+0x268/0x320
[ 4412.631360]  [<ffffffff8104d3d3>] start_secondary+0x183/0x1c0
[ 4412.631362] ---[ end trace c8f1977da1f0a914 ]---
[ 4412.679388] PM: Syncing filesystems ... done.
[ 4412.959753] PM: Preparing system for sleep (mem)
[ 4413.195027] Freezing user space processes ... (elapsed 0.015 seconds) done.
[ 4413.211050] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[ 4413.212514] PM: Suspending system (mem)
[ 4413.212556] Suspending console(s) (use no_console_suspend to debug)
[ 4413.214877] sd 1:0:0:0: [sda] Synchronizing SCSI cache
[ 4413.229627] sd 1:0:0:0: [sda] Stopping disk
[ 4413.867497] PM: suspend of devices complete after 653.990 msecs
[ 4413.883497] PM: late suspend of devices complete after 15.977 msecs
[ 4413.884880] ehci-pci 0000:00:1d.0: System wakeup enabled by ACPI
[ 4413.885239] xhci_hcd 0000:00:14.0: System wakeup enabled by ACPI
[ 4413.899764] PM: noirq suspend of devices complete after 16.249 msecs
[ 4413.900205] ACPI: Preparing to enter system sleep state S3
[ 4413.911628] ACPI : EC: EC stopped
[ 4413.911628] PM: Saving platform NVS memory
[ 4413.911663] Disabling non-boot CPUs ...
[ 4413.912854] smpboot: CPU 1 is now offline
[ 4413.932805] smpboot: CPU 2 is now offline
[ 4413.947771] Broke affinity for irq 23
[ 4413.947777] Broke affinity for irq 43
[ 4413.948792] smpboot: CPU 3 is now offline
[ 4413.965387] ACPI: Low-level resume complete
[ 4413.965446] ACPI : EC: EC started
[ 4413.965446] PM: Restoring platform NVS memory
[ 4413.965872] Enabling non-boot CPUs ...
[ 4413.965915] x86: Booting SMP configuration:
[ 4413.965916] smpboot: Booting Node 0 Processor 1 APIC 0x2
[ 4413.981725]  cache: parent cpu1 should not be sleeping
[ 4413.981849] CPU1 is up
[ 4413.981876] smpboot: Booting Node 0 Processor 2 APIC 0x1
[ 4413.997753]  cache: parent cpu2 should not be sleeping
[ 4413.997865] CPU2 is up
[ 4413.997884] smpboot: Booting Node 0 Processor 3 APIC 0x3
[ 4414.009714]  cache: parent cpu3 should not be sleeping
[ 4414.009783] CPU3 is up
[ 4414.013228] ACPI: Waking up from system sleep state S3
[ 4414.038210] pci_raw_set_power_state: 45 callbacks suppressed
[ 4414.038213] fglrx_pci 0000:08:00.0: Refused to change power state, currently in D3
[ 4414.054271] ehci-pci 0000:00:1d.0: System wakeup disabled by ACPI
[ 4414.142076] xhci_hcd 0000:00:14.0: System wakeup disabled by ACPI
[ 4414.142134] PM: noirq resume of devices complete after 104.021 msecs
[ 4414.147846] PM: early resume of devices complete after 5.692 msecs
[ 4414.148802] rtc_cmos 00:02: System wakeup disabled by ACPI
[ 4414.153938] sd 1:0:0:0: [sda] Starting disk
[ 4414.161675] fglrx_pci 0000:08:00.0: Refused to change power state, currently in D3
[ 4414.184868] xhci_hcd 0000:00:14.0: port 6 resume PLC timeout
[ 4414.199965] xhci_hcd 0000:00:14.0: port 5 resume PLC timeout
[ 4414.426074] usb 1-5: reset high-speed USB device number 2 using xhci_hcd
[ 4414.778449] usb 1-7: reset full-speed USB device number 4 using xhci_hcd
[ 4414.907566] Bluetooth: hci0: turning off Intel device LED failed (-19)
[ 4415.018625] usb 1-6: reset full-speed USB device number 3 using xhci_hcd
[ 4415.147129] usb 1-6: ep 0x2 - rounding interval to 64 microframes, ep desc says 80 microframes
[ 4415.156225] PM: resume of devices complete after 1007.584 msecs
[ 4415.156645] PM: Finishing wakeup.
[ 4415.156646] Restarting tasks ... done.
[ 4415.175534] Bluetooth: hci0: read Intel version: 3707100100012d0d00
[ 4415.201567] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
[ 4416.203315] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[ 4416.315551] ata2.00: configured for UDMA/100
[ 4416.422809] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.0.1.2d.d.bseq
[ 4416.556691] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[ 4421.656397] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[ 4421.656678] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[ 4421.776561] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[ 4421.776813] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[ 4421.791288] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
[ 4421.835364] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
[ 4425.227916] wlp7s0: authenticate with 80:1f:02:0e:0b:fa
[ 4425.230631] wlp7s0: send auth to 80:1f:02:0e:0b:fa (try 1/3)
[ 4425.298149] wlp7s0: authenticated
[ 4425.298412] wlp7s0: associate with 80:1f:02:0e:0b:fa (try 1/3)
[ 4425.302363] wlp7s0: RX AssocResp from 80:1f:02:0e:0b:fa (capab=0x411 status=0 aid=1)
[ 4425.305227] wlp7s0: associated
[ 4425.305250] IPv6: ADDRCONF(NETDEV_CHANGE): wlp7s0: link becomes ready
[ 4457.719600] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe A FIFO underrun

```

lshw:
```

    description: Computer
    width: 64 bits
    capabilities: smbios-2.8 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 15GiB
     *-cpu
          product: Intel(R) Core(TM) i7-5500U CPU @ 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 2659MHz
          capacity: 3GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch ida arat epb pln pts dtherm intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap xsaveopt cpufreq
     *-pci
          description: Host bridge
          product: Broadwell-U Host Bridge -OPI
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=bdw_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Broadwell-U Integrated Graphics
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:f6000000-f6ffffff memory:d0000000-dfffffff ioport:f000(size=64)
        *-multimedia:0
             description: Audio device
             product: Broadwell-U Audio Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:48 memory:f7214000-f7217fff
        *-multimedia:1
             description: Audio device
             product: Wildcat Point-LP High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:47 memory:f7210000-f7213fff
        *-pci:0
             description: PCI bridge
             product: Wildcat Point-LP PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: e3
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:f0000000-f01fffff ioport:f0200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: Wildcat Point-LP PCI Express Root Port #4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: e3
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 memory:f7100000-f71fffff
           *-network
                description: Wireless interface
                product: Wireless 3160
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: wlp7s0
                version: 83
                serial: f4:06:69:7c:1d:2f
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.2.0-23-generic firmware=25.30.13.0 ip=192.168.2.112 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:46 memory:f7100000-f7101fff
        *-pci:2
             description: PCI bridge
             product: Wildcat Point-LP PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: e3
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:e000(size=4096) memory:f7000000-f70fffff ioport:e0000000(size=268435456)
           *-generic
                description: Unassigned class
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 0
                bus info: pci@0000:08:00.0
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list rom
                configuration: driver=fglrx_pci latency=255 maxlatency=255 mingnt=255
                resources: irq:16 memory:e0000000-efffffff memory:f7000000-f703ffff ioport:e000(size=256) memory:f7040000-f705ffff
        *-usb:0
             description: USB controller
             product: Wildcat Point-LP USB EHCI Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f721a000-f721a3ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.2.0-23-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.02
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@3:1
                   version: 0.03
                   capabilities: usb-2.00
                   configuration: driver=hub slots=8 speed=480Mbit/s
        *-isa
             description: ISA bridge
             product: Wildcat Point-LP LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: Wildcat Point-LP SATA Controller [AHCI Mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7219000-f72197ff
        *-serial UNCLAIMED
             description: SMBus
             product: Wildcat Point-LP SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7218000-f72180ff ioport:f040(size=32)
        *-usb:1
             description: USB controller
             product: Wildcat Point-LP USB xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:42 memory:f7200000-f720ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.2.0-23-generic xhci-hcd
                physical id: 0
                bus info: usb@2
                logical name: usb2
                version: 4.02
                capabilities: usb-3.00
                configuration: driver=hub slots=4 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.2.0-23-generic xhci-hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.02
                capabilities: usb-2.00
                configuration: driver=hub slots=11 speed=480Mbit/s
              *-usb:0
                   description: Video
                   product: Integrated_Webcam_HD
                   vendor: SunplusIT Inc
                   physical id: 5
                   bus info: usb@1:5
                   version: 47.11
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:1
                   description: Human interface device
                   product: Touchscreen
                   vendor: ELAN
                   physical id: 6
                   bus info: usb@1:6
                   version: 11.01
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
              *-usb:2
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: 7
                   bus info: usb@1:7
                   version: 0.01
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
        *-communication
             description: Communication controller
             product: Wildcat Point-LP MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:45 memory:f721c000-f721c01f
     *-scsi
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA MQ02ABF1
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: 1D
             serial: 35EQCCX1T
             size: 931GiB (1TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=e9a91a85-9bd8-4750-a3b2-2054f167d5e3 logicalsectorsize=512 sectorsize=4096
           *-volume:0 UNCLAIMED
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@1:0.0.0,1
                version: FAT32
                serial: c09b-f165
                size: 495MiB
                capacity: 499MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat label=ESP name=EFI system partition
           *-volume:1
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                version: FAT32
                serial: 1230-adc6
                size: 15MiB
                capacity: 39MiB
                capabilities: precious readonly hidden nomount fat initialized
                configuration: FATs=2 filesystem=fat label=DIAGS name=Basic data partition
           *-volume:2
                description: reserved partition
                vendor: Windows
                physical id: 3
                bus info: scsi@1:0.0.0,3
                logical name: /dev/sda3
                serial: 79958d2f-83c2-42c2-a974-6323c39a2e19
                capacity: 127MiB
                capabilities: nofs
                configuration: name=Microsoft reserved partition
           *-volume:3
                description: Windows NTFS volume
                vendor: Windows
                physical id: 4
                bus info: scsi@1:0.0.0,4
                logical name: /dev/sda4
                version: 3.1
                serial: 8832-9906
                size: 720MiB
                capacity: 749MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2015-07-01 15:16:53 filesystem=ntfs label=WINRETOOLS modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:4
                description: Windows NTFS volume
                vendor: Windows
                physical id: 5
                bus info: scsi@1:0.0.0,5
                logical name: /dev/sda5
                version: 3.1
                serial: 1255a1d9-f824-5546-882e-3c6f62604639
                size: 158GiB
                capacity: 158GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2015-07-01 15:17:00 filesystem=ntfs label=OS name=Basic data partition state=clean
           *-volume:5
                description: Windows NTFS volume
                vendor: Windows
                physical id: 6
                bus info: scsi@1:0.0.0,6
                logical name: /dev/sda6
                version: 3.1
                serial: eec8-36e5
                size: 424MiB
                capacity: 449MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2016-01-05 11:42:32 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:6
                description: EXT4 volume
                vendor: Linux
                physical id: 7
                bus info: scsi@1:0.0.0,7
                logical name: /dev/sda7
                logical name: /
                version: 1.0
                serial: cea9bfa6-81da-400b-a577-7b7c208bc428
                size: 747GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2016-01-04 19:11:39 filesystem=ext4 lastmountpoint=/ modified=2016-01-06 21:38:20 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-01-06 20:38:24 state=mounted
           *-volume:7
                description: Linux swap volume
                vendor: Linux
                physical id: 8
                bus info: scsi@1:0.0.0,8
                logical name: /dev/sda8
                version: 1
                serial: f03ebb99-64b3-4195-8a62-0696df93eb71
                size: 15GiB
                capacity: 15GiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
           *-volume:8
                description: Windows NTFS volume
                vendor: Windows
                physical id: 9
                bus info: scsi@1:0.0.0,9
                logical name: /dev/sda9
                version: 3.1
                serial: 68dc-2f9e
                size: 7536MiB
                capacity: 7566MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2015-07-01 17:16:09 filesystem=ntfs label=PBR Image modified_by_chkdsk=true mounted_on_nt4=true name=Microsoft recovery partition resize_log_file=true state=dirty upgrade_on_mount=true
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: virbr0-nic
       serial: 52:54:00:0f:8c:82
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s

```

cat /var/log/pm-suspend.log:
```

Initial commandline parameters: --quirk-radeon-off
St led  6 20:41:51 CET 2016: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux vulcan 4.2.0-23-generic #28-Ubuntu SMP Sun Dec 27 17:47:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
rfcomm                 69632  0
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
ipt_MASQUERADE         16384  3
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  2 nf_nat_ipv4,nf_nat_masquerade_ipv4
nf_conntrack_ipv4      16384  2
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  1
nf_conntrack          106496  5 nf_nat,nf_nat_ipv4,xt_conntrack,nf_nat_masquerade_ipv4,nf_conntrack_ipv4
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  6
bridge                114688  0
stp                    16384  1 bridge
llc                    16384  2 stp,bridge
ebtable_filter         16384  0
ebtables               36864  1 ebtable_filter
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  1
ip_tables              28672  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               36864  11 ip6table_filter,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ebtables,ipt_REJECT,iptable_mangle,ip6_tables
bnep                   20480  2
nls_iso8859_1          16384  1
arc4                   16384  2
iwlmvm                294912  0
fglrx               13447168  0
uvcvideo               90112  0
mac80211              733184  1 iwlmvm
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_hda_codec_hdmi     49152  1
videobuf2_core         49152  1 uvcvideo
intel_rapl             20480  0
iosf_mbi               16384  1 intel_rapl
x86_pkg_temp_thermal    16384  0
dell_led               16384  1
v4l2_common            16384  1 videobuf2_core
intel_powerclamp       16384  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
videodev              172032  3 uvcvideo,v4l2_common,videobuf2_core
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
btusb                  45056  0
coretemp               16384  0
media                  24576  2 uvcvideo,videodev
snd_hwdep              16384  1 snd_hda_codec
btrtl                  16384  1 btusb
kvm_intel             167936  0
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
kvm                   512000  1 kvm_intel
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
iwlwifi               200704  1 iwlmvm
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
crct10dif_pclmul       16384  0
btbcm                  16384  1 btusb
crc32_pclmul           16384  0
joydev                 20480  0
btintel                16384  1 btusb
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
dell_laptop            20480  0
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
bluetooth             516096  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
aesni_intel           167936  2
dcdbas                 16384  1 dell_laptop
hid_multitouch         20480  0
dell_smm_hwmon         16384  0
dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
amd_iommu_v2           20480  1 fglrx
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
input_leds             16384  0
ablk_helper            16384  1 aesni_intel
soundcore              16384  1 snd
serio_raw              16384  0
acpi_als               16384  0
cryptd                 20480  2 aesni_intel,ablk_helper
mei_me                 32768  0
kfifo_buf              16384  1 acpi_als
industrialio           61440  2 acpi_als,kfifo_buf
mei                    98304  1 mei_me
dell_smo8800           16384  0
dell_rbtn              16384  0
shpchp                 36864  0
int3403_thermal        16384  0
intel_smartconnect     16384  0
dw_dmac                16384  0
acpi_pad               20480  0
dw_dmac_core           24576  1 dw_dmac
i2c_designware_platform    16384  0
int3400_thermal        16384  0
int3402_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
int340x_thermal_zone    16384  2 int3402_thermal,int3403_thermal
lpc_ich                24576  0
i2c_designware_core    16384  1 i2c_designware_platform
mac_hid                16384  0
cuse                   16384  3
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
usbhid                 49152  0
i915                 1130496  4
i2c_algo_bit           16384  1 i915
drm_kms_helper        126976  1 i915
drm                   356352  5 i915,drm_kms_helper
ahci                   36864  3
libahci                32768  1 ahci
wmi                    20480  2 dell_led,dell_wmi
video                  36864  3 i915,dell_wmi,dell_laptop
i2c_hid                20480  0
hid                   118784  3 i2c_hid,hid_multitouch,usbhid
             total       used       free     shared    buffers     cached
Mem:      16343028    3332004   13011024    1045324     200368    1718816
-/+ buffers/cache:    1412820   14930208
Swap:     16687100          0   16687100
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'p2p-dev-wlp7s0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

St led  6 20:41:52 CET 2016: performing suspend
St led  6 20:42:01 CET 2016: Awake.
St led  6 20:42:01 CET 2016: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting standby to 36 (3 minutes)
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (nil)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

St led  6 20:42:02 CET 2016: Finished.
Initial commandline parameters: --quirk-vbe-post
St led  6 20:43:05 CET 2016: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux vulcan 4.2.0-23-generic #28-Ubuntu SMP Sun Dec 27 17:47:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
rfcomm                 69632  2
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  0
ccm                    20480  0
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
ipt_MASQUERADE         16384  3
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  2 nf_nat_ipv4,nf_nat_masquerade_ipv4
nf_conntrack_ipv4      16384  2
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  1
nf_conntrack          106496  5 nf_nat,nf_nat_ipv4,xt_conntrack,nf_nat_masquerade_ipv4,nf_conntrack_ipv4
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  6
bridge                114688  0
stp                    16384  1 bridge
llc                    16384  2 stp,bridge
ebtable_filter         16384  0
ebtables               36864  1 ebtable_filter
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  1
ip_tables              28672  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               36864  11 ip6table_filter,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ebtables,ipt_REJECT,iptable_mangle,ip6_tables
bnep                   20480  2
nls_iso8859_1          16384  1
arc4                   16384  2
iwlmvm                294912  0
fglrx               13447168  0
uvcvideo               90112  0
mac80211              733184  1 iwlmvm
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_hda_codec_hdmi     49152  1
videobuf2_core         49152  1 uvcvideo
intel_rapl             20480  0
iosf_mbi               16384  1 intel_rapl
x86_pkg_temp_thermal    16384  0
dell_led               16384  1
v4l2_common            16384  1 videobuf2_core
intel_powerclamp       16384  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
videodev              172032  3 uvcvideo,v4l2_common,videobuf2_core
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
btusb                  45056  0
coretemp               16384  0
media                  24576  2 uvcvideo,videodev
snd_hwdep              16384  1 snd_hda_codec
btrtl                  16384  1 btusb
kvm_intel             167936  0
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
kvm                   512000  1 kvm_intel
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
iwlwifi               200704  1 iwlmvm
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
crct10dif_pclmul       16384  0
btbcm                  16384  1 btusb
crc32_pclmul           16384  0
joydev                 20480  0
btintel                16384  1 btusb
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
dell_laptop            20480  0
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
bluetooth             516096  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
aesni_intel           167936  0
dcdbas                 16384  1 dell_laptop
hid_multitouch         20480  0
dell_smm_hwmon         16384  0
dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
amd_iommu_v2           20480  1 fglrx
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
input_leds             16384  0
ablk_helper            16384  1 aesni_intel
soundcore              16384  1 snd
serio_raw              16384  0
acpi_als               16384  0
cryptd                 20480  2 aesni_intel,ablk_helper
mei_me                 32768  0
kfifo_buf              16384  1 acpi_als
industrialio           61440  2 acpi_als,kfifo_buf
mei                    98304  1 mei_me
dell_smo8800           16384  0
dell_rbtn              16384  0
shpchp                 36864  0
int3403_thermal        16384  0
intel_smartconnect     16384  0
dw_dmac                16384  0
acpi_pad               20480  0
dw_dmac_core           24576  1 dw_dmac
i2c_designware_platform    16384  0
int3400_thermal        16384  0
int3402_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
int340x_thermal_zone    16384  2 int3402_thermal,int3403_thermal
lpc_ich                24576  0
i2c_designware_core    16384  1 i2c_designware_platform
mac_hid                16384  0
cuse                   16384  3
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
usbhid                 49152  0
i915                 1130496  4
i2c_algo_bit           16384  1 i915
drm_kms_helper        126976  1 i915
drm                   356352  5 i915,drm_kms_helper
ahci                   36864  3
libahci                32768  1 ahci
wmi                    20480  2 dell_led,dell_wmi
video                  36864  3 i915,dell_wmi,dell_laptop
i2c_hid                20480  0
hid                   118784  3 i2c_hid,hid_multitouch,usbhid
             total       used       free     shared    buffers     cached
Mem:      16343028    3134908   13208120     984068     200820    1665432
-/+ buffers/cache:    1268656   15074372
Swap:     16687100          0   16687100
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (nil)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

St led  6 20:43:06 CET 2016: performing suspend
St led  6 20:43:14 CET 2016: Awake.
St led  6 20:43:14 CET 2016: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting standby to 36 (3 minutes)
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Selected interface 'p2p-dev-wlp7s0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

St led  6 20:43:15 CET 2016: Finished.
Initial commandline parameters: --auto-quirks
St led  6 20:50:48 CET 2016: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux vulcan 4.2.0-23-generic #28-Ubuntu SMP Sun Dec 27 17:47:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
rfcomm                 69632  0
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
ipt_MASQUERADE         16384  3
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  2 nf_nat_ipv4,nf_nat_masquerade_ipv4
nf_conntrack_ipv4      16384  2
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  1
nf_conntrack          106496  5 nf_nat,nf_nat_ipv4,xt_conntrack,nf_nat_masquerade_ipv4,nf_conntrack_ipv4
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  6
bridge                114688  0
stp                    16384  1 bridge
llc                    16384  2 stp,bridge
ebtable_filter         16384  0
ebtables               36864  1 ebtable_filter
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  1
ip_tables              28672  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               36864  11 ip6table_filter,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ebtables,ipt_REJECT,iptable_mangle,ip6_tables
bnep                   20480  2
nls_iso8859_1          16384  1
arc4                   16384  2
snd_hda_codec_hdmi     49152  1
iwlmvm                294912  0
dell_led               16384  1
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
mac80211              733184  1 iwlmvm
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
uvcvideo               90112  0
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
intel_rapl             20480  0
iosf_mbi               16384  1 intel_rapl
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
snd_seq_midi           16384  0
coretemp               16384  0
videobuf2_vmalloc      16384  1 uvcvideo
snd_seq_midi_event     16384  1 snd_seq_midi
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_rawmidi            32768  1 snd_seq_midi
fglrx               13447168  0
kvm_intel             167936  0
kvm                   512000  1 kvm_intel
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
iwlwifi               200704  1 iwlmvm
btusb                  45056  0
videobuf2_core         49152  1 uvcvideo
btrtl                  16384  1 btusb
joydev                 20480  0
v4l2_common            16384  1 videobuf2_core
btbcm                  16384  1 btusb
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
btintel                16384  1 btusb
snd_timer              32768  2 snd_pcm,snd_seq
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
videodev              172032  3 uvcvideo,v4l2_common,videobuf2_core
aesni_intel           167936  2
bluetooth             516096  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
hid_multitouch         20480  0
media                  24576  2 uvcvideo,videodev
dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
dell_smm_hwmon         16384  0
acpi_als               16384  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
soundcore              16384  1 snd
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
mei_me                 32768  0
kfifo_buf              16384  1 acpi_als
input_leds             16384  0
cryptd                 20480  2 aesni_intel,ablk_helper
industrialio           61440  2 acpi_als,kfifo_buf
mei                    98304  1 mei_me
serio_raw              16384  0
amd_iommu_v2           20480  1 fglrx
dell_smo8800           16384  0
dell_rbtn              16384  0
dw_dmac                16384  0
int3403_thermal        16384  0
intel_smartconnect     16384  0
dw_dmac_core           24576  1 dw_dmac
shpchp                 36864  0
int3400_thermal        16384  0
lpc_ich                24576  0
acpi_thermal_rel       16384  1 int3400_thermal
i2c_designware_platform    16384  0
i2c_designware_core    16384  1 i2c_designware_platform
acpi_pad               20480  0
int3402_thermal        16384  0
int340x_thermal_zone    16384  2 int3402_thermal,int3403_thermal
mac_hid                16384  0
cuse                   16384  3
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
usbhid                 49152  0
i915                 1130496  4
i2c_algo_bit           16384  1 i915
ahci                   36864  3
drm_kms_helper        126976  1 i915
libahci                32768  1 ahci
drm                   356352  5 i915,drm_kms_helper
wmi                    20480  2 dell_led,dell_wmi
video                  36864  3 i915,dell_wmi,dell_laptop
i2c_hid                20480  0
hid                   118784  3 i2c_hid,hid_multitouch,usbhid
             total       used       free     shared    buffers     cached
Mem:      16343028    3677576   12665452    1006956     199844    2101092
-/+ buffers/cache:    1376640   14966388
Swap:     16687100          0   16687100
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'p2p-dev-wlp7s0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

St led  6 20:50:49 CET 2016: performing suspend
St led  6 20:51:00 CET 2016: Awake.
St led  6 20:51:00 CET 2016: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting standby to 36 (3 minutes)
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (nil)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

St led  6 20:51:01 CET 2016: Finished.
Initial commandline parameters: --quirk-vbestate-restore
St led  6 20:54:26 CET 2016: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux vulcan 4.2.0-23-generic #28-Ubuntu SMP Sun Dec 27 17:47:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
rfcomm                 69632  0
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
ipt_MASQUERADE         16384  3
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  2 nf_nat_ipv4,nf_nat_masquerade_ipv4
nf_conntrack_ipv4      16384  2
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  1
nf_conntrack          106496  5 nf_nat,nf_nat_ipv4,xt_conntrack,nf_nat_masquerade_ipv4,nf_conntrack_ipv4
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  6
bridge                114688  0
stp                    16384  1 bridge
llc                    16384  2 stp,bridge
ebtable_filter         16384  0
ebtables               36864  1 ebtable_filter
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  1
ip_tables              28672  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               36864  11 ip6table_filter,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ebtables,ipt_REJECT,iptable_mangle,ip6_tables
bnep                   20480  2
nls_iso8859_1          16384  1
uvcvideo               90112  0
arc4                   16384  2
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_hda_codec_hdmi     49152  1
videobuf2_core         49152  1 uvcvideo
iwlmvm                294912  0
dell_led               16384  1
v4l2_common            16384  1 videobuf2_core
fglrx               13447168  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
mac80211              733184  1 iwlmvm
videodev              172032  3 uvcvideo,v4l2_common,videobuf2_core
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
intel_rapl             20480  0
media                  24576  2 uvcvideo,videodev
iosf_mbi               16384  1 intel_rapl
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
kvm_intel             167936  0
iwlwifi               200704  1 iwlmvm
kvm                   512000  1 kvm_intel
btusb                  45056  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
joydev                 20480  0
btrtl                  16384  1 btusb
crct10dif_pclmul       16384  0
hid_multitouch         20480  0
crc32_pclmul           16384  0
btbcm                  16384  1 btusb
btintel                16384  1 btusb
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
dell_wmi               16384  0
bluetooth             516096  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
aesni_intel           167936  2
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
sparse_keymap          16384  1 dell_wmi
dell_smm_hwmon         16384  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
soundcore              16384  1 snd
ablk_helper            16384  1 aesni_intel
input_leds             16384  0
cryptd                 20480  2 aesni_intel,ablk_helper
serio_raw              16384  0
acpi_als               16384  0
amd_iommu_v2           20480  1 fglrx
mei_me                 32768  0
kfifo_buf              16384  1 acpi_als
mei                    98304  1 mei_me
industrialio           61440  2 acpi_als,kfifo_buf
acpi_pad               20480  0
dell_smo8800           16384  0
dell_rbtn              16384  0
dw_dmac                16384  0
int3403_thermal        16384  0
intel_smartconnect     16384  0
dw_dmac_core           24576  1 dw_dmac
shpchp                 36864  0
lpc_ich                24576  0
int3402_thermal        16384  0
int3400_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
int340x_thermal_zone    16384  2 int3402_thermal,int3403_thermal
i2c_designware_platform    16384  0
mac_hid                16384  0
i2c_designware_core    16384  1 i2c_designware_platform
cuse                   16384  3
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
usbhid                 49152  0
i915                 1130496  4
i2c_algo_bit           16384  1 i915
drm_kms_helper        126976  1 i915
ahci                   36864  3
libahci                32768  1 ahci
drm                   356352  5 i915,drm_kms_helper
wmi                    20480  2 dell_led,dell_wmi
video                  36864  3 i915,dell_wmi,dell_laptop
i2c_hid                20480  0
hid                   118784  3 i2c_hid,hid_multitouch,usbhid
             total       used       free     shared    buffers     cached
Mem:      16343028    3538016   12805012    1042556     197840    1887340
-/+ buffers/cache:    1452836   14890192
Swap:     16687100          0   16687100
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'p2p-dev-wlp7s0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

St led  6 20:54:27 CET 2016: performing suspend
St led  6 20:54:37 CET 2016: Awake.
St led  6 20:54:37 CET 2016: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting standby to 36 (3 minutes)
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (nil)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

St led  6 20:54:39 CET 2016: Finished.
Initial commandline parameters: --quirk-dpms-on
St led  6 20:56:13 CET 2016: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux vulcan 4.2.0-23-generic #28-Ubuntu SMP Sun Dec 27 17:47:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
rfcomm                 69632  2
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
ipt_MASQUERADE         16384  3
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  2 nf_nat_ipv4,nf_nat_masquerade_ipv4
nf_conntrack_ipv4      16384  2
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  1
nf_conntrack          106496  5 nf_nat,nf_nat_ipv4,xt_conntrack,nf_nat_masquerade_ipv4,nf_conntrack_ipv4
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  6
bridge                114688  0
stp                    16384  1 bridge
llc                    16384  2 stp,bridge
ebtable_filter         16384  0
ebtables               36864  1 ebtable_filter
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  1
ip_tables              28672  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               36864  11 ip6table_filter,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ebtables,ipt_REJECT,iptable_mangle,ip6_tables
bnep                   20480  2
nls_iso8859_1          16384  1
uvcvideo               90112  0
arc4                   16384  2
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_hda_codec_hdmi     49152  1
videobuf2_core         49152  1 uvcvideo
iwlmvm                294912  0
dell_led               16384  1
v4l2_common            16384  1 videobuf2_core
fglrx               13447168  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
mac80211              733184  1 iwlmvm
videodev              172032  3 uvcvideo,v4l2_common,videobuf2_core
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
intel_rapl             20480  0
media                  24576  2 uvcvideo,videodev
iosf_mbi               16384  1 intel_rapl
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
kvm_intel             167936  0
iwlwifi               200704  1 iwlmvm
kvm                   512000  1 kvm_intel
btusb                  45056  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
joydev                 20480  0
btrtl                  16384  1 btusb
crct10dif_pclmul       16384  0
hid_multitouch         20480  0
crc32_pclmul           16384  0
btbcm                  16384  1 btusb
btintel                16384  1 btusb
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
dell_wmi               16384  0
bluetooth             516096  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
aesni_intel           167936  2
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
sparse_keymap          16384  1 dell_wmi
dell_smm_hwmon         16384  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
soundcore              16384  1 snd
ablk_helper            16384  1 aesni_intel
input_leds             16384  0
cryptd                 20480  2 aesni_intel,ablk_helper
serio_raw              16384  0
acpi_als               16384  0
amd_iommu_v2           20480  1 fglrx
mei_me                 32768  0
kfifo_buf              16384  1 acpi_als
mei                    98304  1 mei_me
industrialio           61440  2 acpi_als,kfifo_buf
acpi_pad               20480  0
dell_smo8800           16384  0
dell_rbtn              16384  0
dw_dmac                16384  0
int3403_thermal        16384  0
intel_smartconnect     16384  0
dw_dmac_core           24576  1 dw_dmac
shpchp                 36864  0
lpc_ich                24576  0
int3402_thermal        16384  0
int3400_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
int340x_thermal_zone    16384  2 int3402_thermal,int3403_thermal
i2c_designware_platform    16384  0
mac_hid                16384  0
i2c_designware_core    16384  1 i2c_designware_platform
cuse                   16384  3
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
usbhid                 49152  0
i915                 1130496  4
i2c_algo_bit           16384  1 i915
drm_kms_helper        126976  1 i915
ahci                   36864  3
libahci                32768  1 ahci
drm                   356352  5 i915,drm_kms_helper
wmi                    20480  2 dell_led,dell_wmi
video                  36864  3 i915,dell_wmi,dell_laptop
i2c_hid                20480  0
hid                   118784  3 i2c_hid,hid_multitouch,usbhid
             total       used       free     shared    buffers     cached
Mem:      16343028    3564876   12778152     914172     200488    2081228
-/+ buffers/cache:    1283160   15059868
Swap:     16687100          0   16687100
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'p2p-dev-wlp7s0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

St led  6 20:56:14 CET 2016: performing suspend
St led  6 20:56:26 CET 2016: Awake.
St led  6 20:56:26 CET 2016: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting standby to 36 (3 minutes)
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Selected interface 'p2p-dev-wlp7s0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

St led  6 20:56:27 CET 2016: Finished.
Initial commandline parameters: --quirk-dpms-suspend
St led  6 20:57:06 CET 2016: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux vulcan 4.2.0-23-generic #28-Ubuntu SMP Sun Dec 27 17:47:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
rfcomm                 69632  2
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
ipt_MASQUERADE         16384  3
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  2 nf_nat_ipv4,nf_nat_masquerade_ipv4
nf_conntrack_ipv4      16384  2
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  1
nf_conntrack          106496  5 nf_nat,nf_nat_ipv4,xt_conntrack,nf_nat_masquerade_ipv4,nf_conntrack_ipv4
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  6
bridge                114688  0
stp                    16384  1 bridge
llc                    16384  2 stp,bridge
ebtable_filter         16384  0
ebtables               36864  1 ebtable_filter
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  1
ip_tables              28672  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               36864  11 ip6table_filter,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ebtables,ipt_REJECT,iptable_mangle,ip6_tables
bnep                   20480  2
nls_iso8859_1          16384  1
uvcvideo               90112  0
arc4                   16384  2
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_hda_codec_hdmi     49152  1
videobuf2_core         49152  1 uvcvideo
iwlmvm                294912  0
dell_led               16384  1
v4l2_common            16384  1 videobuf2_core
fglrx               13447168  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
mac80211              733184  1 iwlmvm
videodev              172032  3 uvcvideo,v4l2_common,videobuf2_core
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
intel_rapl             20480  0
media                  24576  2 uvcvideo,videodev
iosf_mbi               16384  1 intel_rapl
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
kvm_intel             167936  0
iwlwifi               200704  1 iwlmvm
kvm                   512000  1 kvm_intel
btusb                  45056  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
joydev                 20480  0
btrtl                  16384  1 btusb
crct10dif_pclmul       16384  0
hid_multitouch         20480  0
crc32_pclmul           16384  0
btbcm                  16384  1 btusb
btintel                16384  1 btusb
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
dell_wmi               16384  0
bluetooth             516096  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
aesni_intel           167936  2
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
sparse_keymap          16384  1 dell_wmi
dell_smm_hwmon         16384  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
soundcore              16384  1 snd
ablk_helper            16384  1 aesni_intel
input_leds             16384  0
cryptd                 20480  2 aesni_intel,ablk_helper
serio_raw              16384  0
acpi_als               16384  0
amd_iommu_v2           20480  1 fglrx
mei_me                 32768  0
kfifo_buf              16384  1 acpi_als
mei                    98304  1 mei_me
industrialio           61440  2 acpi_als,kfifo_buf
acpi_pad               20480  0
dell_smo8800           16384  0
dell_rbtn              16384  0
dw_dmac                16384  0
int3403_thermal        16384  0
intel_smartconnect     16384  0
dw_dmac_core           24576  1 dw_dmac
shpchp                 36864  0
lpc_ich                24576  0
int3402_thermal        16384  0
int3400_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
int340x_thermal_zone    16384  2 int3402_thermal,int3403_thermal
i2c_designware_platform    16384  0
mac_hid                16384  0
i2c_designware_core    16384  1 i2c_designware_platform
cuse                   16384  3
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
usbhid                 49152  0
i915                 1130496  4
i2c_algo_bit           16384  1 i915
drm_kms_helper        126976  1 i915
ahci                   36864  3
libahci                32768  1 ahci
drm                   356352  5 i915,drm_kms_helper
wmi                    20480  2 dell_led,dell_wmi
video                  36864  3 i915,dell_wmi,dell_laptop
i2c_hid                20480  0
hid                   118784  3 i2c_hid,hid_multitouch,usbhid
             total       used       free     shared    buffers     cached
Mem:      16343028    3733536   12609492    1070520     200800    2237704
-/+ buffers/cache:    1295032   15047996
Swap:     16687100          0   16687100
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'p2p-dev-wlp7s0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

St led  6 20:57:06 CET 2016: performing suspend
St led  6 20:57:22 CET 2016: Awake.
St led  6 20:57:22 CET 2016: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting standby to 36 (3 minutes)
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Selected interface 'wlp7s0'
'RESUME' command timed out.
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

St led  6 20:57:33 CET 2016: Finished.
Initial commandline parameters: --quirk-reset-brightness
St led  6 20:58:21 CET 2016: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux vulcan 4.2.0-23-generic #28-Ubuntu SMP Sun Dec 27 17:47:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
rfcomm                 69632  2
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
ipt_MASQUERADE         16384  3
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  2 nf_nat_ipv4,nf_nat_masquerade_ipv4
nf_conntrack_ipv4      16384  2
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  1
nf_conntrack          106496  5 nf_nat,nf_nat_ipv4,xt_conntrack,nf_nat_masquerade_ipv4,nf_conntrack_ipv4
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  6
bridge                114688  0
stp                    16384  1 bridge
llc                    16384  2 stp,bridge
ebtable_filter         16384  0
ebtables               36864  1 ebtable_filter
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  1
ip_tables              28672  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               36864  11 ip6table_filter,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ebtables,ipt_REJECT,iptable_mangle,ip6_tables
bnep                   20480  2
nls_iso8859_1          16384  1
uvcvideo               90112  0
arc4                   16384  2
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_hda_codec_hdmi     49152  1
videobuf2_core         49152  1 uvcvideo
iwlmvm                294912  0
dell_led               16384  1
v4l2_common            16384  1 videobuf2_core
fglrx               13447168  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
mac80211              733184  1 iwlmvm
videodev              172032  3 uvcvideo,v4l2_common,videobuf2_core
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
intel_rapl             20480  0
media                  24576  2 uvcvideo,videodev
iosf_mbi               16384  1 intel_rapl
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
kvm_intel             167936  0
iwlwifi               200704  1 iwlmvm
kvm                   512000  1 kvm_intel
btusb                  45056  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
joydev                 20480  0
btrtl                  16384  1 btusb
crct10dif_pclmul       16384  0
hid_multitouch         20480  0
crc32_pclmul           16384  0
btbcm                  16384  1 btusb
btintel                16384  1 btusb
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
dell_wmi               16384  0
bluetooth             516096  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
aesni_intel           167936  2
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
sparse_keymap          16384  1 dell_wmi
dell_smm_hwmon         16384  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
soundcore              16384  1 snd
ablk_helper            16384  1 aesni_intel
input_leds             16384  0
cryptd                 20480  2 aesni_intel,ablk_helper
serio_raw              16384  0
acpi_als               16384  0
amd_iommu_v2           20480  1 fglrx
mei_me                 32768  0
kfifo_buf              16384  1 acpi_als
mei                    98304  1 mei_me
industrialio           61440  2 acpi_als,kfifo_buf
acpi_pad               20480  0
dell_smo8800           16384  0
dell_rbtn              16384  0
dw_dmac                16384  0
int3403_thermal        16384  0
intel_smartconnect     16384  0
dw_dmac_core           24576  1 dw_dmac
shpchp                 36864  0
lpc_ich                24576  0
int3402_thermal        16384  0
int3400_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
int340x_thermal_zone    16384  2 int3402_thermal,int3403_thermal
i2c_designware_platform    16384  0
mac_hid                16384  0
i2c_designware_core    16384  1 i2c_designware_platform
cuse                   16384  3
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
usbhid                 49152  0
i915                 1130496  4
i2c_algo_bit           16384  1 i915
drm_kms_helper        126976  1 i915
ahci                   36864  3
libahci                32768  1 ahci
drm                   356352  5 i915,drm_kms_helper
wmi                    20480  2 dell_led,dell_wmi
video                  36864  3 i915,dell_wmi,dell_laptop
i2c_hid                20480  0
hid                   118784  3 i2c_hid,hid_multitouch,usbhid
             total       used       free     shared    buffers     cached
Mem:      16343028    3178800   13164228     996856     201244    1677624
-/+ buffers/cache:    1299932   15043096
Swap:     16687100          0   16687100
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'p2p-dev-wlp7s0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

St led  6 20:58:22 CET 2016: performing suspend
St led  6 20:58:31 CET 2016: Awake.
St led  6 20:58:31 CET 2016: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting standby to 36 (3 minutes)
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Selected interface 'wlp7s0'
'RESUME' command timed out.
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

St led  6 20:58:42 CET 2016: Finished.
Initial commandline parameters: --quirk-s3-bios
St led  6 20:59:17 CET 2016: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux vulcan 4.2.0-23-generic #28-Ubuntu SMP Sun Dec 27 17:47:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
rfcomm                 69632  2
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
ipt_MASQUERADE         16384  3
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  2 nf_nat_ipv4,nf_nat_masquerade_ipv4
nf_conntrack_ipv4      16384  2
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  1
nf_conntrack          106496  5 nf_nat,nf_nat_ipv4,xt_conntrack,nf_nat_masquerade_ipv4,nf_conntrack_ipv4
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  6
bridge                114688  0
stp                    16384  1 bridge
llc                    16384  2 stp,bridge
ebtable_filter         16384  0
ebtables               36864  1 ebtable_filter
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  1
ip_tables              28672  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               36864  11 ip6table_filter,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ebtables,ipt_REJECT,iptable_mangle,ip6_tables
bnep                   20480  2
nls_iso8859_1          16384  1
uvcvideo               90112  0
arc4                   16384  2
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_hda_codec_hdmi     49152  1
videobuf2_core         49152  1 uvcvideo
iwlmvm                294912  0
dell_led               16384  1
v4l2_common            16384  1 videobuf2_core
fglrx               13447168  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
mac80211              733184  1 iwlmvm
videodev              172032  3 uvcvideo,v4l2_common,videobuf2_core
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
intel_rapl             20480  0
media                  24576  2 uvcvideo,videodev
iosf_mbi               16384  1 intel_rapl
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
kvm_intel             167936  0
iwlwifi               200704  1 iwlmvm
kvm                   512000  1 kvm_intel
btusb                  45056  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
joydev                 20480  0
btrtl                  16384  1 btusb
crct10dif_pclmul       16384  0
hid_multitouch         20480  0
crc32_pclmul           16384  0
btbcm                  16384  1 btusb
btintel                16384  1 btusb
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
dell_wmi               16384  0
bluetooth             516096  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
aesni_intel           167936  2
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
sparse_keymap          16384  1 dell_wmi
dell_smm_hwmon         16384  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
soundcore              16384  1 snd
ablk_helper            16384  1 aesni_intel
input_leds             16384  0
cryptd                 20480  2 aesni_intel,ablk_helper
serio_raw              16384  0
acpi_als               16384  0
amd_iommu_v2           20480  1 fglrx
mei_me                 32768  0
kfifo_buf              16384  1 acpi_als
mei                    98304  1 mei_me
industrialio           61440  2 acpi_als,kfifo_buf
acpi_pad               20480  0
dell_smo8800           16384  0
dell_rbtn              16384  0
dw_dmac                16384  0
int3403_thermal        16384  0
intel_smartconnect     16384  0
dw_dmac_core           24576  1 dw_dmac
shpchp                 36864  0
lpc_ich                24576  0
int3402_thermal        16384  0
int3400_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
int340x_thermal_zone    16384  2 int3402_thermal,int3403_thermal
i2c_designware_platform    16384  0
mac_hid                16384  0
i2c_designware_core    16384  1 i2c_designware_platform
cuse                   16384  3
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
usbhid                 49152  0
i915                 1130496  4
i2c_algo_bit           16384  1 i915
drm_kms_helper        126976  1 i915
ahci                   36864  3
libahci                32768  1 ahci
drm                   356352  5 i915,drm_kms_helper
wmi                    20480  2 dell_led,dell_wmi
video                  36864  3 i915,dell_wmi,dell_laptop
i2c_hid                20480  0
hid                   118784  3 i2c_hid,hid_multitouch,usbhid
             total       used       free     shared    buffers     cached
Mem:      16343028    3255108   13087920    1072404     201532    1753228
-/+ buffers/cache:    1300348   15042680
Swap:     16687100          0   16687100
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'p2p-dev-wlp7s0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

St led  6 20:59:17 CET 2016: performing suspend
St led  6 20:59:28 CET 2016: Awake.
St led  6 20:59:28 CET 2016: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting standby to 36 (3 minutes)
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Selected interface 'wlp7s0'
'RESUME' command timed out.
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

St led  6 20:59:39 CET 2016: Finished.
Initial commandline parameters: --quirk-s3-mode
St led  6 21:00:19 CET 2016: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux vulcan 4.2.0-23-generic #28-Ubuntu SMP Sun Dec 27 17:47:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
rfcomm                 69632  2
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
ipt_MASQUERADE         16384  3
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  2 nf_nat_ipv4,nf_nat_masquerade_ipv4
nf_conntrack_ipv4      16384  2
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  1
nf_conntrack          106496  5 nf_nat,nf_nat_ipv4,xt_conntrack,nf_nat_masquerade_ipv4,nf_conntrack_ipv4
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  6
bridge                114688  0
stp                    16384  1 bridge
llc                    16384  2 stp,bridge
ebtable_filter         16384  0
ebtables               36864  1 ebtable_filter
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  1
ip_tables              28672  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               36864  11 ip6table_filter,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ebtables,ipt_REJECT,iptable_mangle,ip6_tables
bnep                   20480  2
nls_iso8859_1          16384  1
uvcvideo               90112  0
arc4                   16384  2
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_hda_codec_hdmi     49152  1
videobuf2_core         49152  1 uvcvideo
iwlmvm                294912  0
dell_led               16384  1
v4l2_common            16384  1 videobuf2_core
fglrx               13447168  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
mac80211              733184  1 iwlmvm
videodev              172032  3 uvcvideo,v4l2_common,videobuf2_core
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
intel_rapl             20480  0
media                  24576  2 uvcvideo,videodev
iosf_mbi               16384  1 intel_rapl
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
kvm_intel             167936  0
iwlwifi               200704  1 iwlmvm
kvm                   512000  1 kvm_intel
btusb                  45056  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
joydev                 20480  0
btrtl                  16384  1 btusb
crct10dif_pclmul       16384  0
hid_multitouch         20480  0
crc32_pclmul           16384  0
btbcm                  16384  1 btusb
btintel                16384  1 btusb
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
dell_wmi               16384  0
bluetooth             516096  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
aesni_intel           167936  2
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
sparse_keymap          16384  1 dell_wmi
dell_smm_hwmon         16384  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
soundcore              16384  1 snd
ablk_helper            16384  1 aesni_intel
input_leds             16384  0
cryptd                 20480  2 aesni_intel,ablk_helper
serio_raw              16384  0
acpi_als               16384  0
amd_iommu_v2           20480  1 fglrx
mei_me                 32768  0
kfifo_buf              16384  1 acpi_als
mei                    98304  1 mei_me
industrialio           61440  2 acpi_als,kfifo_buf
acpi_pad               20480  0
dell_smo8800           16384  0
dell_rbtn              16384  0
dw_dmac                16384  0
int3403_thermal        16384  0
intel_smartconnect     16384  0
dw_dmac_core           24576  1 dw_dmac
shpchp                 36864  0
lpc_ich                24576  0
int3402_thermal        16384  0
int3400_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
int340x_thermal_zone    16384  2 int3402_thermal,int3403_thermal
i2c_designware_platform    16384  0
mac_hid                16384  0
i2c_designware_core    16384  1 i2c_designware_platform
cuse                   16384  3
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
usbhid                 49152  0
i915                 1130496  4
i2c_algo_bit           16384  1 i915
drm_kms_helper        126976  1 i915
ahci                   36864  3
libahci                32768  1 ahci
drm                   356352  5 i915,drm_kms_helper
wmi                    20480  2 dell_led,dell_wmi
video                  36864  3 i915,dell_wmi,dell_laptop
i2c_hid                20480  0
hid                   118784  3 i2c_hid,hid_multitouch,usbhid
             total       used       free     shared    buffers     cached
Mem:      16343028    3202136   13140892    1009284     201876    1690260
-/+ buffers/cache:    1310000   15033028
Swap:     16687100          0   16687100
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'p2p-dev-wlp7s0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

St led  6 21:00:19 CET 2016: performing suspend
St led  6 21:00:30 CET 2016: Awake.
St led  6 21:00:30 CET 2016: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting standby to 36 (3 minutes)
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Selected interface 'wlp7s0'
'RESUME' command timed out.
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

St led  6 21:00:41 CET 2016: Finished.
Initial commandline parameters: --quirk-s3-mode
--quirk-s3-bios
St led  6 21:01:49 CET 2016: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux vulcan 4.2.0-23-generic #28-Ubuntu SMP Sun Dec 27 17:47:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
rfcomm                 69632  2
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
ipt_MASQUERADE         16384  3
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  2 nf_nat_ipv4,nf_nat_masquerade_ipv4
nf_conntrack_ipv4      16384  2
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  1
nf_conntrack          106496  5 nf_nat,nf_nat_ipv4,xt_conntrack,nf_nat_masquerade_ipv4,nf_conntrack_ipv4
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  6
bridge                114688  0
stp                    16384  1 bridge
llc                    16384  2 stp,bridge
ebtable_filter         16384  0
ebtables               36864  1 ebtable_filter
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  1
ip_tables              28672  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               36864  11 ip6table_filter,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ebtables,ipt_REJECT,iptable_mangle,ip6_tables
bnep                   20480  2
nls_iso8859_1          16384  1
uvcvideo               90112  0
arc4                   16384  2
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_hda_codec_hdmi     49152  1
videobuf2_core         49152  1 uvcvideo
iwlmvm                294912  0
dell_led               16384  1
v4l2_common            16384  1 videobuf2_core
fglrx               13447168  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
mac80211              733184  1 iwlmvm
videodev              172032  3 uvcvideo,v4l2_common,videobuf2_core
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
intel_rapl             20480  0
media                  24576  2 uvcvideo,videodev
iosf_mbi               16384  1 intel_rapl
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
kvm_intel             167936  0
iwlwifi               200704  1 iwlmvm
kvm                   512000  1 kvm_intel
btusb                  45056  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
joydev                 20480  0
btrtl                  16384  1 btusb
crct10dif_pclmul       16384  0
hid_multitouch         20480  0
crc32_pclmul           16384  0
btbcm                  16384  1 btusb
btintel                16384  1 btusb
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
dell_wmi               16384  0
bluetooth             516096  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
aesni_intel           167936  2
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
sparse_keymap          16384  1 dell_wmi
dell_smm_hwmon         16384  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
soundcore              16384  1 snd
ablk_helper            16384  1 aesni_intel
input_leds             16384  0
cryptd                 20480  2 aesni_intel,ablk_helper
serio_raw              16384  0
acpi_als               16384  0
amd_iommu_v2           20480  1 fglrx
mei_me                 32768  0
kfifo_buf              16384  1 acpi_als
mei                    98304  1 mei_me
industrialio           61440  2 acpi_als,kfifo_buf
acpi_pad               20480  0
dell_smo8800           16384  0
dell_rbtn              16384  0
dw_dmac                16384  0
int3403_thermal        16384  0
intel_smartconnect     16384  0
dw_dmac_core           24576  1 dw_dmac
shpchp                 36864  0
lpc_ich                24576  0
int3402_thermal        16384  0
int3400_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
int340x_thermal_zone    16384  2 int3402_thermal,int3403_thermal
i2c_designware_platform    16384  0
mac_hid                16384  0
i2c_designware_core    16384  1 i2c_designware_platform
cuse                   16384  3
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
usbhid                 49152  0
i915                 1130496  4
i2c_algo_bit           16384  1 i915
drm_kms_helper        126976  1 i915
ahci                   36864  3
libahci                32768  1 ahci
drm                   356352  5 i915,drm_kms_helper
wmi                    20480  2 dell_led,dell_wmi
video                  36864  3 i915,dell_wmi,dell_laptop
i2c_hid                20480  0
hid                   118784  3 i2c_hid,hid_multitouch,usbhid
             total       used       free     shared    buffers     cached
Mem:      16343028    3136084   13206944     942224     202200    1623336
-/+ buffers/cache:    1310548   15032480
Swap:     16687100          0   16687100
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'p2p-dev-wlp7s0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

St led  6 21:01:49 CET 2016: performing suspend
St led  6 21:02:03 CET 2016: Awake.
St led  6 21:02:03 CET 2016: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting standby to 36 (3 minutes)
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Selected interface 'wlp7s0'
'RESUME' command timed out.
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

St led  6 21:02:14 CET 2016: Finished.
Initial commandline parameters: --quirk-vga-mode-3
St led  6 21:03:09 CET 2016: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux vulcan 4.2.0-23-generic #28-Ubuntu SMP Sun Dec 27 17:47:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
rfcomm                 69632  2
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
ipt_MASQUERADE         16384  3
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  2 nf_nat_ipv4,nf_nat_masquerade_ipv4
nf_conntrack_ipv4      16384  2
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  1
nf_conntrack          106496  5 nf_nat,nf_nat_ipv4,xt_conntrack,nf_nat_masquerade_ipv4,nf_conntrack_ipv4
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  6
bridge                114688  0
stp                    16384  1 bridge
llc                    16384  2 stp,bridge
ebtable_filter         16384  0
ebtables               36864  1 ebtable_filter
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  1
ip_tables              28672  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               36864  11 ip6table_filter,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ebtables,ipt_REJECT,iptable_mangle,ip6_tables
bnep                   20480  2
nls_iso8859_1          16384  1
uvcvideo               90112  0
arc4                   16384  2
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_hda_codec_hdmi     49152  1
videobuf2_core         49152  1 uvcvideo
iwlmvm                294912  0
dell_led               16384  1
v4l2_common            16384  1 videobuf2_core
fglrx               13447168  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
mac80211              733184  1 iwlmvm
videodev              172032  3 uvcvideo,v4l2_common,videobuf2_core
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
intel_rapl             20480  0
media                  24576  2 uvcvideo,videodev
iosf_mbi               16384  1 intel_rapl
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
kvm_intel             167936  0
iwlwifi               200704  1 iwlmvm
kvm                   512000  1 kvm_intel
btusb                  45056  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
joydev                 20480  0
btrtl                  16384  1 btusb
crct10dif_pclmul       16384  0
hid_multitouch         20480  0
crc32_pclmul           16384  0
btbcm                  16384  1 btusb
btintel                16384  1 btusb
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
dell_wmi               16384  0
bluetooth             516096  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
aesni_intel           167936  2
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
sparse_keymap          16384  1 dell_wmi
dell_smm_hwmon         16384  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
soundcore              16384  1 snd
ablk_helper            16384  1 aesni_intel
input_leds             16384  0
cryptd                 20480  2 aesni_intel,ablk_helper
serio_raw              16384  0
acpi_als               16384  0
amd_iommu_v2           20480  1 fglrx
mei_me                 32768  0
kfifo_buf              16384  1 acpi_als
mei                    98304  1 mei_me
industrialio           61440  2 acpi_als,kfifo_buf
acpi_pad               20480  0
dell_smo8800           16384  0
dell_rbtn              16384  0
dw_dmac                16384  0
int3403_thermal        16384  0
intel_smartconnect     16384  0
dw_dmac_core           24576  1 dw_dmac
shpchp                 36864  0
lpc_ich                24576  0
int3402_thermal        16384  0
int3400_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
int340x_thermal_zone    16384  2 int3402_thermal,int3403_thermal
i2c_designware_platform    16384  0
mac_hid                16384  0
i2c_designware_core    16384  1 i2c_designware_platform
cuse                   16384  3
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
usbhid                 49152  0
i915                 1130496  4
i2c_algo_bit           16384  1 i915
drm_kms_helper        126976  1 i915
ahci                   36864  3
libahci                32768  1 ahci
drm                   356352  5 i915,drm_kms_helper
wmi                    20480  2 dell_led,dell_wmi
video                  36864  3 i915,dell_wmi,dell_laptop
i2c_hid                20480  0
hid                   118784  3 i2c_hid,hid_multitouch,usbhid
             total       used       free     shared    buffers     cached
Mem:      16343028    3141808   13201220     941700     202456    1622872
-/+ buffers/cache:    1316480   15026548
Swap:     16687100          0   16687100
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'p2p-dev-wlp7s0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

St led  6 21:03:09 CET 2016: performing suspend
St led  6 21:03:22 CET 2016: Awake.
St led  6 21:03:22 CET 2016: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting standby to 36 (3 minutes)
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Selected interface 'wlp7s0'
'RESUME' command timed out.
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

St led  6 21:03:33 CET 2016: Finished.
Initial commandline parameters: --quirk-vbemode-restore
--quirk-vbestate-restore
St led  6 21:20:44 CET 2016: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux vulcan 4.2.0-23-generic #28-Ubuntu SMP Sun Dec 27 17:47:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
rfcomm                 69632  0
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
ipt_MASQUERADE         16384  3
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  2 nf_nat_ipv4,nf_nat_masquerade_ipv4
nf_conntrack_ipv4      16384  2
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  1
nf_conntrack          106496  5 nf_nat,nf_nat_ipv4,xt_conntrack,nf_nat_masquerade_ipv4,nf_conntrack_ipv4
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  6
bridge                114688  0
stp                    16384  1 bridge
llc                    16384  2 stp,bridge
ebtable_filter         16384  0
ebtables               36864  1 ebtable_filter
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  1
ip_tables              28672  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               36864  11 ip6table_filter,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ebtables,ipt_REJECT,iptable_mangle,ip6_tables
bnep                   20480  2
nls_iso8859_1          16384  1
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
arc4                   16384  2
videobuf2_core         49152  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
iwlmvm                294912  0
videodev              172032  3 uvcvideo,v4l2_common,videobuf2_core
snd_hda_codec_hdmi     49152  1
intel_rapl             20480  0
dell_led               16384  1
iosf_mbi               16384  1 intel_rapl
x86_pkg_temp_thermal    16384  0
media                  24576  2 uvcvideo,videodev
fglrx               13447168  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          36864  5
mac80211              733184  1 iwlmvm
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
intel_powerclamp       16384  0
coretemp               16384  0
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
kvm_intel             167936  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
iwlwifi               200704  1 iwlmvm
kvm                   512000  1 kvm_intel
btusb                  45056  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
btrtl                  16384  1 btusb
joydev                 20480  0
crct10dif_pclmul       16384  0
btbcm                  16384  1 btusb
crc32_pclmul           16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
dell_wmi               16384  0
snd_timer              32768  2 snd_pcm,snd_seq
hid_multitouch         20480  0
btintel                16384  1 btusb
bluetooth             516096  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
aesni_intel           167936  2
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
sparse_keymap          16384  1 dell_wmi
dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
dell_smm_hwmon         16384  0
glue_helper            16384  1 aesni_intel
input_leds             16384  0
ablk_helper            16384  1 aesni_intel
amd_iommu_v2           20480  1 fglrx
cryptd                 20480  2 aesni_intel,ablk_helper
soundcore              16384  1 snd
serio_raw              16384  0
acpi_als               16384  0
mei_me                 32768  0
kfifo_buf              16384  1 acpi_als
industrialio           61440  2 acpi_als,kfifo_buf
mei                    98304  1 mei_me
shpchp                 36864  0
dell_smo8800           16384  0
dell_rbtn              16384  0
dw_dmac                16384  0
int3403_thermal        16384  0
intel_smartconnect     16384  0
dw_dmac_core           24576  1 dw_dmac
acpi_pad               20480  0
lpc_ich                24576  0
int3400_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
i2c_designware_platform    16384  0
i2c_designware_core    16384  1 i2c_designware_platform
int3402_thermal        16384  0
int340x_thermal_zone    16384  2 int3402_thermal,int3403_thermal
mac_hid                16384  0
cuse                   16384  3
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
usbhid                 49152  0
i915                 1130496  4
ahci                   36864  3
libahci                32768  1 ahci
i2c_algo_bit           16384  1 i915
drm_kms_helper        126976  1 i915
drm                   356352  5 i915,drm_kms_helper
wmi                    20480  2 dell_led,dell_wmi
video                  36864  3 i915,dell_wmi,dell_laptop
i2c_hid                20480  0
hid                   118784  3 i2c_hid,hid_multitouch,usbhid
             total       used       free     shared    buffers     cached
Mem:      16343028    3951768   12391260    1158032     200520    2321992
-/+ buffers/cache:    1429256   14913772
Swap:     16687100          0   16687100
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'p2p-dev-wlp7s0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

St led  6 21:20:44 CET 2016: performing suspend
St led  6 21:20:54 CET 2016: Awake.
St led  6 21:20:54 CET 2016: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting standby to 36 (3 minutes)
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (nil)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

St led  6 21:20:56 CET 2016: Finished.
Initial commandline parameters: --quirk-dpms-on
--quirk-dpms-suspend
St led  6 21:25:28 CET 2016: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux vulcan 4.2.0-23-generic #28-Ubuntu SMP Sun Dec 27 17:47:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
rfcomm                 69632  0
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
ipt_MASQUERADE         16384  3
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  2 nf_nat_ipv4,nf_nat_masquerade_ipv4
nf_conntrack_ipv4      16384  2
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  1
nf_conntrack          106496  5 nf_nat,nf_nat_ipv4,xt_conntrack,nf_nat_masquerade_ipv4,nf_conntrack_ipv4
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  6
bridge                114688  0
stp                    16384  1 bridge
llc                    16384  2 stp,bridge
ebtable_filter         16384  0
ebtables               36864  1 ebtable_filter
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  1
ip_tables              28672  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               36864  11 ip6table_filter,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ebtables,ipt_REJECT,iptable_mangle,ip6_tables
bnep                   20480  2
nls_iso8859_1          16384  1
snd_hda_codec_hdmi     49152  1
uvcvideo               90112  0
dell_led               16384  1
arc4                   16384  2
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
iwlmvm                294912  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
videobuf2_core         49152  1 uvcvideo
snd_hwdep              16384  1 snd_hda_codec
v4l2_common            16384  1 videobuf2_core
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
videodev              172032  3 uvcvideo,v4l2_common,videobuf2_core
mac80211              733184  1 iwlmvm
intel_rapl             20480  0
iosf_mbi               16384  1 intel_rapl
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
media                  24576  2 uvcvideo,videodev
dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
snd_rawmidi            32768  1 snd_seq_midi
joydev                 20480  0
iwlwifi               200704  1 iwlmvm
fglrx               13447168  0
kvm_intel             167936  0
btusb                  45056  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
kvm                   512000  1 kvm_intel
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
hid_multitouch         20480  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
bluetooth             516096  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
aesni_intel           167936  2
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
dell_smm_hwmon         16384  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
soundcore              16384  1 snd
input_leds             16384  0
cryptd                 20480  2 aesni_intel,ablk_helper
amd_iommu_v2           20480  1 fglrx
acpi_als               16384  0
mei_me                 32768  0
kfifo_buf              16384  1 acpi_als
serio_raw              16384  0
industrialio           61440  2 acpi_als,kfifo_buf
mei                    98304  1 mei_me
int3403_thermal        16384  0
dw_dmac                16384  0
lpc_ich                24576  0
dell_smo8800           16384  0
shpchp                 36864  0
dell_rbtn              16384  0
intel_smartconnect     16384  0
dw_dmac_core           24576  1 dw_dmac
int3400_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
i2c_designware_platform    16384  0
i2c_designware_core    16384  1 i2c_designware_platform
acpi_pad               20480  0
int3402_thermal        16384  0
mac_hid                16384  0
int340x_thermal_zone    16384  2 int3402_thermal,int3403_thermal
cuse                   16384  3
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
usbhid                 49152  0
i915                 1130496  4
ahci                   36864  3
libahci                32768  1 ahci
i2c_algo_bit           16384  1 i915
drm_kms_helper        126976  1 i915
drm                   356352  5 i915,drm_kms_helper
wmi                    20480  2 dell_led,dell_wmi
video                  36864  3 i915,dell_wmi,dell_laptop
i2c_hid                20480  0
hid                   118784  3 i2c_hid,hid_multitouch,usbhid
             total       used       free     shared    buffers     cached
Mem:      16343028    3706332   12636696     969424     200956    2113720
-/+ buffers/cache:    1391656   14951372
Swap:     16687100          0   16687100
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'p2p-dev-wlp7s0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

St led  6 21:25:29 CET 2016: performing suspend
St led  6 21:26:10 CET 2016: Awake.
St led  6 21:26:10 CET 2016: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting standby to 36 (3 minutes)
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (nil)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

St led  6 21:26:11 CET 2016: Finished.

```

---

### Post by fryda.tomas on 2016-01-07
Using  kernel 4.3.3-040303-generic from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3.3-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3.3-wily/) seems to solve this issue. I will test it for a few days before marking this thread as SOLVED.

---

