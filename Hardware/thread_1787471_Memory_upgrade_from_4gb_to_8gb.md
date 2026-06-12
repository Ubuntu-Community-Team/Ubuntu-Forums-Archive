---
title: "Memory upgrade from 4gb to 8gb"
date: 2011-06-21
forum: Hardware
---

### Post by lada on 2011-06-21
Howdy,

I updated my Lenovo T510 memory from 4gb to 8gb, but apparently only 4gb are detected by linux. Any ideas how to fix it ?

uname -a 
2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux

cat /proc/mtrr
reg01: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg02: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg03: base=0x100000000 ( 4096MB), size= 4096MB, count=1: write-back
reg04: base=0x200000000 ( 8192MB), size= 1024MB, count=1: write-back
reg05: base=0x23c000000 ( 9152MB), size=   64MB, count=1: uncachable

free -m
             total       used       free     shared    buffers     cached
Mem:          3888       1704       2183          0         88        672
-/+ buffers/cache:        944       2943
Swap:         8803          0       8803


dmesg | grep BIOS
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf27c000 (usable)
[    0.000000]  BIOS-e820: 00000000bf27c000 - 00000000bf282000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf282000 - 00000000bf35f000 (usable)
[    0.000000]  BIOS-e820: 00000000bf35f000 - 00000000bf371000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf371000 - 00000000bf3f2000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf3f2000 - 00000000bf40f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf40f000 - 00000000bf46f000 (usable)
[    0.000000]  BIOS-e820: 00000000bf46f000 - 00000000bf668000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf668000 - 00000000bf6e8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf6e8000 - 00000000bf70f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf70f000 - 00000000bf717000 (usable)
[    0.000000]  BIOS-e820: 00000000bf717000 - 00000000bf71f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf71f000 - 00000000bf76c000 (usable)
[    0.000000]  BIOS-e820: 00000000bf76c000 - 00000000bf778000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf778000 - 00000000bf77b000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf77b000 - 00000000bf78b000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf78b000 - 00000000bf78c000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf78c000 - 00000000bf79f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf79f000 - 00000000bf7ff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf7ff000 - 00000000bf800000 (usable)
[    0.000000]  BIOS-e820: 00000000bf800000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 0000000200000000 - 000000023c000000 (usable)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000]   #4 [00000f68d0 - 0000100000]   BIOS reserved
[    0.000000]   #6 [000009e800 - 000009f071]   BIOS reserved
[    0.000000]   #7 [000009f185 - 00000f68c0]   BIOS reserved
[    0.794162] ACPI: BIOS _OSI(Linux) query ignored
[    1.071268] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   43.725090] thinkpad_acpi: ThinkPad BIOS 6MET57WW (1.20 ), EC 6MHT37WW-1.12

---

### Post by nomko on 2011-06-21
[COLOR=black]I think you need the PAE kernel.[/COLOR]
 
What kind of CPU you have? 32-bit or 64-bit?

---

### Post by lada on 2011-06-21
Ubuntu 10.10 64 bit...Isn't PAE only for 32bit to support more memory.

---

### Post by mastablasta on 2011-06-21
does BIOS detect the added RAM?

---

### Post by nomko on 2011-06-21
> **lada said:**
> Ubuntu 10.10 64 bit...Isn't PAE only for 32bit to support more memory.
 
Yes, it does depend on your cpu (32-bit or 64-bit). Like mastablasta asks: does your BIOS see the extra 4 gig ram? Does your laptop even support more than 4 gig memory?

---

### Post by lada on 2011-06-21
Did check yet from bios itself but isn't following dump indicating that memory should be available to linux. 

dmesg | grep -i memory
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bf800000
[    0.000000] init_memory_mapping: 0000000100000000-000000023c000000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bf27c000 - 00000000bf282000
[    0.000000] PM: Registered nosave memory: 00000000bf35f000 - 00000000bf371000
[    0.000000] PM: Registered nosave memory: 00000000bf371000 - 00000000bf3f2000
[    0.000000] PM: Registered nosave memory: 00000000bf3f2000 - 00000000bf40f000
[    0.000000] PM: Registered nosave memory: 00000000bf46f000 - 00000000bf668000
[    0.000000] PM: Registered nosave memory: 00000000bf668000 - 00000000bf6e8000
[    0.000000] PM: Registered nosave memory: 00000000bf6e8000 - 00000000bf70f000
[    0.000000] PM: Registered nosave memory: 00000000bf717000 - 00000000bf71f000
[    0.000000] PM: Registered nosave memory: 00000000bf76c000 - 00000000bf778000
[    0.000000] PM: Registered nosave memory: 00000000bf778000 - 00000000bf77b000
[    0.000000] PM: Registered nosave memory: 00000000bf77b000 - 00000000bf78b000
[    0.000000] PM: Registered nosave memory: 00000000bf78b000 - 00000000bf78c000
[    0.000000] PM: Registered nosave memory: 00000000bf78c000 - 00000000bf79f000
[    0.000000] PM: Registered nosave memory: 00000000bf79f000 - 00000000bf7ff000
[    0.000000] PM: Registered nosave memory: 00000000bf800000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 0000000200000000
[    0.000000] Memory: 3969976k/9371648k available (5708k kernel code, 5255564k absent, 146108k reserved, 5382k data, 908k init)
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.001809] Initializing cgroup subsys memory
[    0.984190] Scanning for low memory corruption every 60 seconds
[    1.001125] Freeing initrd memory: 8616k freed
[    1.071359] Freeing unused kernel memory: 908k freed
[    1.071725] Freeing unused kernel memory: 416k freed
[    1.071923] Freeing unused kernel memory: 1644k freed
[   43.515533] Non-volatile memory driver v1.3
[   45.631174] VBoxDrv: dbg - g_abExecMemory=ffffffffa0e1cae0

---

### Post by lada on 2011-06-22
BIOS shows Installed Memory 8192MB as well.

---

### Post by nusch on 2011-10-20
Did you solved your problem? Maybe by anoter manufacter modules ? I also upgraded with 4GB to 8GB, on Lenovo Y530..

---

### Post by lada on 2011-11-03
No still the same, I've got ubuntu 11.10 64bit but still the same...

---

### Post by lada on 2011-11-03
Lenovo Bios 1.47 update solved the problem.

---

