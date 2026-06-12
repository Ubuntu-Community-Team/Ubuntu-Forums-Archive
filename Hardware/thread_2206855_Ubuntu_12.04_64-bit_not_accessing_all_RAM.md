---
title: "Ubuntu 12.04 64-bit not accessing all RAM"
date: 2014-02-21
forum: Hardware
---

### Post by pkh2 on 2014-02-21
Hi,

I am running Ubuntu 12.04 64-bit on an AMD A4-5300 APU on an ASRock FM2A88x-ITX+ motherboard, and even though I have 4GB of ram installed, the system only uses 1.4.  I understand some RAM will be used for the APU, but there is an additional 2 GB that isn't being used.  

Some commands I have checked:

[FONT=courier new]
[/FONT][FONT=courier new]pkhlx@pkhlx-desktop:~$ uname -a[/FONT]
[FONT=courier new]Linux pkhlx-desktop 3.8.0-36-generic #52~precise1-Ubuntu SMP Mon Feb 3 21:54:46 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]pkhlx@pkhlx-desktop:~$ free -m[/FONT]
[FONT=courier new]             total       used       free     shared    buffers     cached[/FONT]
[FONT=courier new]Mem:          1421       1337         84          0          3        157[/FONT]
[FONT=courier new]-/+ buffers/cache:       1175        245[/FONT]
[FONT=courier new]Swap:         1458        463        995[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]pkhlx@pkhlx-desktop:~$ cat /proc/meminfo | grep -i memtotal[/FONT]
[FONT=courier new]MemTotal:        1455928 kB[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]pkhlx@pkhlx-desktop:~$ sudo lshw -short | grep 'System\ Memory' [/FONT]
[FONT=courier new]/0/f                       memory      4GiB System Memory[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]pkhlx@pkhlx-desktop:~$ sudo lshw | grep -A 8 bank [/FONT]
[FONT=courier new]        *-bank:0[/FONT]
[FONT=courier new]             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)[/FONT]
[FONT=courier new]             product: KHX1866C9D3/2GX[/FONT]
[FONT=courier new]             vendor: Kingston[/FONT]
[FONT=courier new]             physical id: 0[/FONT]
[FONT=courier new]             serial: 742089AB[/FONT]
[FONT=courier new]             slot: DIMM 0[/FONT]
[FONT=courier new]             size: 2GiB[/FONT]
[FONT=courier new]             width: 64 bits[/FONT]
[FONT=courier new]--[/FONT]
[FONT=courier new]        *-bank:1[/FONT]
[FONT=courier new]             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)[/FONT]
[FONT=courier new]             product: KHX1866C9D3/2GX[/FONT]
[FONT=courier new]             vendor: Kingston[/FONT]
[FONT=courier new]             physical id: 1[/FONT]
[FONT=courier new]             serial: 71207EAB[/FONT]
[FONT=courier new]             slot: DIMM 0[/FONT]
[FONT=courier new]             size: 2GiB[/FONT]
[FONT=courier new]             width: 64 bits[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]pkhlx@pkhlx-desktop:~/Desktop$ sudo dmidecode -t memory[/FONT]
[FONT=courier new]# dmidecode 2.11[/FONT]
[FONT=courier new]# SMBIOS entry point at 0x000f04d0[/FONT]
[FONT=courier new]SMBIOS 2.7 present.[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]Handle 0x000F, DMI type 16, 23 bytes[/FONT]
[FONT=courier new]Physical Memory Array[/FONT]
[FONT=courier new]	Location: System Board Or Motherboard[/FONT]
[FONT=courier new]	Use: System Memory[/FONT]
[FONT=courier new]	Error Correction Type: None[/FONT]
[FONT=courier new]	Maximum Capacity: 4 GB[/FONT]
[FONT=courier new]	Error Information Handle: Not Provided[/FONT]
[FONT=courier new]	Number Of Devices: 2[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]Handle 0x0011, DMI type 17, 34 bytes[/FONT]
[FONT=courier new]Memory Device[/FONT]
[FONT=courier new]	Array Handle: 0x000F[/FONT]
[FONT=courier new]	Error Information Handle: Not Provided[/FONT]
[FONT=courier new]	Total Width: 64 bits[/FONT]
[FONT=courier new]	Data Width: 64 bits[/FONT]
[FONT=courier new]	Size: 2048 MB[/FONT]
[FONT=courier new]	Form Factor: DIMM[/FONT]
[FONT=courier new]	Set: None[/FONT]
[FONT=courier new]	Locator: DIMM 0[/FONT]
[FONT=courier new]	Bank Locator: CHANNEL A[/FONT]
[FONT=courier new]	Type: DDR3[/FONT]
[FONT=courier new]	Type Detail: Synchronous Unbuffered (Unregistered)[/FONT]
[FONT=courier new]	Speed: 1333 MHz[/FONT]
[FONT=courier new]	Manufacturer: Kingston       [/FONT]
[FONT=courier new]	Serial Number: 742089AB[/FONT]
[FONT=courier new]	Asset Tag: A1_AssetTagNum0[/FONT]
[FONT=courier new]	Part Number: KHX1866C9D3/2GX   [/FONT]
[FONT=courier new]	Rank: 1[/FONT]
[FONT=courier new]	Configured Clock Speed: 1600 MHz[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]Handle 0x0013, DMI type 17, 34 bytes[/FONT]
[FONT=courier new]Memory Device[/FONT]
[FONT=courier new]	Array Handle: 0x000F[/FONT]
[FONT=courier new]	Error Information Handle: Not Provided[/FONT]
[FONT=courier new]	Total Width: 64 bits[/FONT]
[FONT=courier new]	Data Width: 64 bits[/FONT]
[FONT=courier new]	Size: 2048 MB[/FONT]
[FONT=courier new]	Form Factor: DIMM[/FONT]
[FONT=courier new]	Set: None[/FONT]
[FONT=courier new]	Locator: DIMM 0[/FONT]
[FONT=courier new]	Bank Locator: CHANNEL B[/FONT]
[FONT=courier new]	Type: DDR3[/FONT]
[FONT=courier new]	Type Detail: Synchronous Unbuffered (Unregistered)[/FONT]
[FONT=courier new]	Speed: 1333 MHz[/FONT]
[FONT=courier new]	Manufacturer: Kingston       [/FONT]
[FONT=courier new]	Serial Number: 71207EAB[/FONT]
[FONT=courier new]	Asset Tag: A1_AssetTagNum1[/FONT]
[FONT=courier new]	Part Number: KHX1866C9D3/2GX   [/FONT]
[FONT=courier new]	Rank: 1[/FONT]
[FONT=courier new]	Configured Clock Speed: 1600 MHz[/FONT]





and here is dmesg memory info:


[FONT=courier new][    0.000000] Initializing cgroup subsys cpuset[/FONT]
[FONT=courier new][    0.000000] Initializing cgroup subsys cpu[/FONT]
[FONT=courier new][    0.000000] Linux version 3.8.0-36-generic (buildd@aatxe) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #52~precise1-Ubuntu SMP Mon Feb 3 21:54:46 UTC 2014 (Ubuntu 3.8.0-36.52~precise1-generic 3.8.13.14)[/FONT]
[FONT=courier new][    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-36-generic.efi.signed root=UUID=3fae943a-1f89-4183-9df8-d322334b15a0 ro quiet splash[/FONT]
[FONT=courier new][    0.000000] KERNEL supported cpus:[/FONT]
[FONT=courier new][    0.000000]   Intel GenuineIntel[/FONT]
[FONT=courier new][    0.000000]   AMD AuthenticAMD[/FONT]
[FONT=courier new][    0.000000]   Centaur CentaurHauls[/FONT]
[FONT=courier new][    0.000000] e820: BIOS-provided physical RAM map:[/FONT]
[FONT=courier new][    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009ffff] usable[/FONT]
[FONT=courier new][    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000005aec1fff] usable[/FONT]
[FONT=courier new][    0.000000] BIOS-e820: [mem 0x000000005aec2000-0x000000005aef1fff] reserved[/FONT]
[FONT=courier new][    0.000000] BIOS-e820: [mem 0x000000005aef2000-0x000000005b1c4fff] usable[/FONT]
[FONT=courier new][    0.000000] BIOS-e820: [mem 0x000000005b1c5000-0x000000005b27cfff] ACPI NVS[/FONT]
[FONT=courier new][    0.000000] BIOS-e820: [mem 0x000000005b27d000-0x000000005d18bfff] reserved[/FONT]
[FONT=courier new][    0.000000] BIOS-e820: [mem 0x000000005d18c000-0x000000005d18cfff] usable[/FONT]
[FONT=courier new][    0.000000] BIOS-e820: [mem 0x000000005d18d000-0x000000005d392fff] ACPI NVS[/FONT]
[FONT=courier new][    0.000000] BIOS-e820: [mem 0x000000005d393000-0x000000005d4e8fff] usable[/FONT]
[FONT=courier new][    0.000000] BIOS-e820: [mem 0x000000005d4e9000-0x000000005e030fff] reserved[/FONT]
[FONT=courier new][    0.000000] BIOS-e820: [mem 0x000000005e031000-0x000000005e071fff] usable[/FONT]
[FONT=courier new][    0.000000] BIOS-e820: [mem 0x000000005e072000-0x000000005e7f0fff] reserved[/FONT]
[FONT=courier new][    0.000000] BIOS-e820: [mem 0x000000005e7f1000-0x000000005e7fffff] usable[/FONT]
[FONT=courier new][    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved[/FONT]
[FONT=courier new][    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved[/FONT]
[FONT=courier new][    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed00fff] reserved[/FONT]
[FONT=courier new][    0.000000] BIOS-e820: [mem 0x00000000fed40000-0x00000000fed44fff] reserved[/FONT]
[FONT=courier new][    0.000000] BIOS-e820: [mem 0x00000000fed80000-0x00000000fed8ffff] reserved[/FONT]
[FONT=courier new][    0.000000] BIOS-e820: [mem 0x00000000ff800000-0x00000000ffffffff] reserved[/FONT]
[FONT=courier new][    0.000000] NX (Execute Disable) protection: active[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]
[/FONT]






Is this a BIOS bug, like the one reported here:  [http://askubuntu.com/questions/106976/why-doesnt-ubuntu-detect-all-of-my-ram-on-64-bit](http://askubuntu.com/questions/106976/why-doesnt-ubuntu-detect-all-of-my-ram-on-64-bit)  ?

thanks for your help

---

### Post by pkh2 on 2014-02-21
OK yes it was a BIOS bug, I just updated to latest version of motherboard BIOS and I now am detecting 3.2 GB.  Thanks for your help anyway!

---

