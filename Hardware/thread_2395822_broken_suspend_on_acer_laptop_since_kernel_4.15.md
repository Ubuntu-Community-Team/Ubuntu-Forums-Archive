---
title: "broken suspend on acer laptop since kernel 4.15"
date: 2018-07-07
forum: Hardware
---

### Post by nick87720z on 2018-07-07
I got it first time when tried to install Lubuntu 18.04 i386 (for laptop with only 2Gb of ram).
On attempt to suspend it does software preparations, but nothing with hardware - led, that should blink, flashes constantly and no hearable click, usually made on poweroff or successful suspend).
It is ok in Elementary OS Loki (64bit though), using kernel 4.4, and in Lubuntu 16.04 - with kernel 4.13, which was installed instead of 4.4 by default by linux-generic-hwe-16.04 (instead of just linux-generic).
But since some time this also moved to kernel 4.15 and i got old known suspend problem.

Kernel 4.13 is still installed, yet i could just install linux-generic, but i tried to figure out, what is changed in 4.15.
Though I worry, how long kernel 4.13 will be kept before autocleaned - probably better to move to 4.4 and make it default in grub.

As for power - it seems to be managed by acpi. I noticed toshiba laptop has toshiba_acpi module loaded, an aspire with kernel 4.13 has some acpi modules as well:  sdhci_acpi, snd_intel_sst_acpi.
However, adding them to /etc/modules (or its symlink /etc/modules-load.d/modules.conf) doesn' help.
Found arount advises about acpi_rev_override=1 (kernel option),
vm.laptop_mode=5 (in /etc/sysctl.d/laptop.conf)
or disabling usb3 xhci make no difference.

After getting sorted lsmod lists for both 4.13 and 4.15 kernels: ```
lsmod | cut -d' ' -f1
```
and comparing, i found, that much more items are missing, with only one new: zstd_compress (142 modules in 4.15 against 160 in 4.13).
Total list of not loaded modules:
- intel_int0002_vgpio
- intel_smartconnect
- sdhci
- sdhci_acpi
- serdev
- snd_compress
- snd_intel_sst_acpi
- snd_intel_sst_core
- snd_pcm_dmaengine
- snd_soc_core
- snd_soc_rl6231
- snd_soc_rl5640
- snd_soc_rl5645
- snd_soc_rl5670
- snd_soc_sst_atom_hifi2_platform
- snd_soc_sst_match
- spi_pxa2xx_platform

Laptop model is Acer Aspire ES1-511 (or as on sticker - Acer E15).

After adding of two two mentioned acpi modules i got loaded:
+ sdhci
+ sdhci_acpi
+ snd_compress
+ snd_intel_sst_acpi
+ snd_intel_sst_core
+ snd_pcm_dmaengine
+ snd_soc_acpi
+ snd_soc_acpi_intel_match
+ snd_soc_core
+ snd_soc_sst_atom_hifi2_platform

suspend issue is still there.

---

### Post by Hello1024 on 2018-08-10
I can confirm this issue occurs on an Acer Aspire E 15 - E5-511G-P239 with the 4.15.0-30-generic kernel.

Seems to hang somewhere in the suspend process.  Interestingly, the fan controller seems to have the fan set to minimum speed, yet occasionally increase to maximum speed for 5 seconds or so, which is behaviour unlike linux' thermal management even with a bursty workload.

---

