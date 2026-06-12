---
title: "RAM not completely used"
date: 2010-04-17
forum: Hardware
---

### Post by athelas on 2010-04-17
Hi everybody.

Unfortunately I found out, that my Ubuntu (actually I am running Xubuntu 9.10 64bit) only recognises 2.9GB of my 4GB RAM and I don't know the reason.
My Bios tells me I have 4029MB RAM and WIndows recognises the hole 4GB RAM as well. So I guess it's not broken Has anybody an idea what's wrong?

---

### Post by howefield on 2010-04-17
At the risk of stating the obvious, are you sure it is 64 bit you are running ?

What's the output of

```
uname -a
```

---

### Post by athelas on 2010-04-17
Because I didn't want to embarrass myself here, I checked this befor :)

```
Linux celdrion-laptop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux

```

---

### Post by Slim Odds on 2010-04-17
I can't say for your specific case.

But here's what I can tell you.

64 bit Ubuntu has no problems addressing large amounts of memory as long as the hardware is properly configured (which yours seems to be since the other OS works).

How did you determine that it only sees 2.9GB?

What hardware are you using?

---

### Post by athelas on 2010-04-17
I've seen it in the gnome system monitor (i guess that's the right english name for it, i got everything in german...) and here is what **free **tells me:
```
             total       used       free     shared    buffers     cached
Mem:       3019880     860096    2159784          0      14512     223512
-/+ buffers/cache:     622072    2397808
Swap:      2048276     119000    1929276

```Hardware:
Acer Extensa 5630EZ
Intel Core 2 Duo T4200   2x 2,0 GHz
DDR2 memory 4GB
Mobile Intel GMA 4500M graphics

Is that what you wanted to know about my hardware or do you need more specifications?

---

### Post by gordintoronto on 2010-04-17
The GMA 4500M steals some memory, but I would not have expected it to be a gigabyte. Does it have a configuration program where you can check? Maybe start at Administration/sysinfo and see what it says about video.

---

### Post by replica2010 on 2010-04-17
Usually there's a BIOS setting. However, I'm having a problem on my x64 system where I set the BIOS to push PCI mmio behind 3.25gb, and grub no longer displays properly.  This issue was in Vista as well. Vista, though, will occasionally lie about how much memory it's actually using, because users with 4gb would get a bit annoyed when it said they only had 3gb. ;-)

---

### Post by Yellow Pasque on 2010-04-17
Near the begining of dmesg log:
```
dmesg | head -n 50
```
you should see something like:
```
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffbe000 - 000000007ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ffe0000 - 000000007ffee000 (reserved)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
```

Upgrading the BIOS may help too, but only do that if you really need the extra 0.5 GB or so of RAM. [http://www.acer.co.uk/acer/service.do?LanguageISOCtxParam=en&miu10einu24.current.attN2B2F2EEF=3734&sp=page15e&ctx2.c2att1=17&miu10ekcond13.attN2B2F2EEF=3734&CountryISOCtxParam=UK&ctx1g.c2att92=122&ctx1.att21k=1&CRC=2980211862](http://www.acer.co.uk/acer/service.do?LanguageISOCtxParam=en&miu10einu24.current.attN2B2F2EEF=3734&sp=page15e&ctx2.c2att1=17&miu10ekcond13.attN2B2F2EEF=3734&CountryISOCtxParam=UK&ctx1g.c2att92=122&ctx1.att21k=1&CRC=2980211862)

---

### Post by athelas on 2010-04-18
Yeah, my graphic card should steel some, but should that not be shown as used RAM?


OK, I checked now dmesgd log:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-20-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 (Ubuntu 2.6.31-20.58-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=2aca48de-a38e-4c7d-8825-f9cd3d4d1c71 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d400 (usable)
[    0.000000]  BIOS-e820: 000000000009d400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bb6a1000 (usable)
[    0.000000]  BIOS-e820: 00000000bb6a1000 - 00000000bb6a7000 (reserved)
[    0.000000]  BIOS-e820: 00000000bb6a7000 - 00000000bb7bc000 (usable)
[    0.000000]  BIOS-e820: 00000000bb7bc000 - 00000000bb80f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bb80f000 - 00000000bb908000 (usable)
[    0.000000]  BIOS-e820: 00000000bb908000 - 00000000bbb0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bbb0f000 - 00000000bbb18000 (usable)
[    0.000000]  BIOS-e820: 00000000bbb18000 - 00000000bbb1f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bbb1f000 - 00000000bbb64000 (usable)
[    0.000000]  BIOS-e820: 00000000bbb64000 - 00000000bbb9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bbb9f000 - 00000000bbbe2000 (usable)
[    0.000000]  BIOS-e820: 00000000bbbe2000 - 00000000bbbff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bbbff000 - 00000000bbc00000 (usable)
[    0.000000]  BIOS-e820: 00000000bbc00000 - 00000000bbe00000 (reserved)
[    0.000000]  BIOS-e820: 00000000bc000000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbbc00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 base 0BC000000 mask FFC000000 uncachable

```But honestly, I am not sure what it should tell me :(

---

