---
title: "No power management"
date: 2012-10-04
forum: Hardware
---

### Post by martinr on 2012-10-04
My desktop computer with LUbuntu 10.04 does not power down after hibernate or (soft) power-off. The OS does shut down but displays "power off" as the last line, then the computer just keeps running until I press the physical power button. It's like it's 1995 all over again.

When I run Windoze XP I can successfully hibernate and soft power down and the computer will automatically switch off. A previous Ubuntu installation (5.10) is able to soft power down and switch off the machine correctly (just tested it on the exact same setup and BIOS configuration with a live CD).

When I look in /var/log/messages I see the following logs related to APM and ACPI:
```
[    0.000000] ACPI Error: A valid RSDP was not found (20090903/tbxfroot-219)
[    0.138078] ACPI: Interpreter disabled.
[    0.147498] pci 0000:00:07.3: quirk: region 6100-613f claimed by PIIX4 ACPI
[    0.176084] pnp: PnP ACPI: disabled
[   36.661720] apm: BIOS not found.
```


When I run the Ubuntu 5.10 live CD (that does power down correctly) I see only the following message:
```
[  458.651844] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
```

I tried all variations of the boot parameters: noacpi apm=on / acpi=off apm=on / amp=off acpi=on,  but nothing seems to make a difference. mesgd shows the same log entries every time. The kernel module APM is present.

My processor is an AMD K6-2 with PowerNow powermanagement features, my mb is an [Aopen AX5T]("http://www.anandtech.com/show/57") with an Intel 430TX chipset, and my BIOS is supposed to [support ACPI]("http://www.tcs3.com/pdf/manuals/motherboards/acer/ax5t/ax5t-sn.pdf"), but surely supports APM. I'd like to enable APM because that used to work in the past (just to be on the safe side).

Does anybody know how to get APM working again?

Extra info:
```
$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 5
model           : 8
model name      : AMD-K6(tm) 3D processor
stepping        : 12
cpu MHz         : 400.948
cache size      : 64 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr cx8 pge mmx syscall 3dnow k6_mtrr up
bogomips        : 801.89
clflush size    : 32
cache_alignment : 32
address sizes   : 32 bits physical, 32 bits virtual
power management:
```

---

### Post by martinr on 2012-10-05
I did some additional testing with other Ubuntu versions and found the following results:

When I run the XUbuntu 6.04 live CD it also powers down correctly. I see only the following message:
```

$ dmesg|grep -i ACPI
[17179569.184000] ACPI: Unable to locate RSDP
[   65.039981] ACPI: Subsystem revision 20051216
[   65.040000] ACPI: Interpreter disabled.
[   65.040125] pnp: PnP ACPI: disabled
[   65.047908] PCI quirk: region 6100-613f claimed by PIIX4 ACPI
ubuntu@ubuntu:~$ dmesg|grep -i APM
[  323.121289] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
ubuntu@ubuntu:~$ uname -r
2.6.15-26-386

```

When testing Ubuntu 8.04 it starts to fail with the following messages in dmesg:
```

[    0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[   91.351868] ACPI: Interpreter disabled.
[   91.352453] pnp: PnP ACPI: disabled
[   91.369186] PCI quirk: region 6100-613f claimed by PIIX4 ACPI
[  100.233979] thermal: Unknown symbol acpi_processor_set_thermal_limit
[  365.835742] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[  365.836337] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[  365.838378] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[  365.839319] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash apci=off apm=on --
[  375.531578] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
2.6.24-16-generic

```
Although I have a 2003 bios version, APM stopped working from 8.04 onward. Is there a way around this? How can I get APM power management back in LUbuntu 10.04?

---

### Post by martinr on 2012-10-08
Bump?

---

### Post by martinr on 2012-10-11
Come one guys anybody?

Objective: get APM up and running on a pre 2000 machine (power management used to work like a charm under XUbuntu 6.04 and still works in WinXP)

Current state under LUbuntu 10.04:

"PM Control by APM" is activated in the BIOS.

Boot flags: "acpi=off,apm=on" are active.

dmesg shows:
```

[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-43-generic root=UUID=0c10db01-4a0d-4a9b-9b1d-635b04128078 ro quiet splash acpi=off apm=on
[    0.142071] ACPI: Interpreter disabled.
[    0.151487] pci 0000:00:07.3: quirk: region 6100-613f claimed by PIIX4 ACPI
[    0.180085] pnp: PnP ACPI: disabled
[   33.074352] apm: BIOS not found.
[  691.538053] apm: BIOS not found.
[  813.735874] apm: BIOS not found.

```

The apm kernel module is present:
Output from: grep -i apm /boot/config-2.6.32-43-generic
```
CONFIG_X86_APM_BOOT=y
CONFIG_APM=m
```

When attempting to load the kernel module I get:
```

# modprobe apm
FATAL: Error inserting apm (/lib/modules/2.6.32-43-generic/kernel/arch/x86/kernel/apm.ko): No such device

```

"#apm -v" prints:
```
#apm -v
No APM support in kernel
```

"apmd" is installed.

Why isn't my BIOS recognised any more, like it was in XUbuntu 6.04 (output from dmesg).
```

[  458.651844] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
```
And how do I get it recognised again?


Why the heck isn't APM working and how can I get it to function again under LUbuntu 10.04, anybody?

---

### Post by martinr on 2012-10-18
Bump bump

---

### Post by martinr on 2012-10-20
Bump bump bump

---

### Post by martinr on 2012-11-03
4*Bump
(When do I get a sticker?)

---

### Post by martinr on 2012-12-08
5*bump

---

