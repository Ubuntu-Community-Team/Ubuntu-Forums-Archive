---
title: "Please help: How do I enable integrated GPU on Coffee Lake CPU in Ubuntu 18.x"
date: 2018-09-18
forum: Hardware
---

### Post by canadrian on 2018-09-18
I am so far unable to get Plex/ffmpeg to recognize the integrated GPU in my Core i7-8700 CPU. From my research it appears this is a common issue related to Coffee Lake CPUs, not just this specific model.

I started on vanilla Ubuntu 18.04, but also tried installing a mainline 4.17 kernel on 18.04, as well as upgrading to Ubuntu 18.10 with default kernel as well as latest mainline 4.18 kernel. None of these have resolved the issue.

Additional troubleshooting attempted:
[LIST]
[*]```
usermod -aG video USERNAME
```
[*]Editing /etc/default/grub with the following options:
```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet i915.alpha_support=1"
```
Later changed to:
```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet intel_pstate=skylake_hwp i915.enable_guc=-1 i915.alpha_support=1"
```
(using ```
sudo update-grub
``` after each change)
[*]Confirmed integrated GPU is enabled in BIOS
[*]Installed latest graphics drivers from [http://ppa.launchpad.net/oibaf/graphics-drivers/](http://ppa.launchpad.net/oibaf/graphics-drivers/)
[*]Followed the entire process to build QuickSync-enabled binaries from [here]("https://gist.github.com/Brainiarc7/4f831867f8e55d35cbcb527e15f9f116")
[/LIST]

Nothing seems to be working. From what I've read, my current kernel version includes support for Coffee Lake graphics, but they simply are not recognized. Here are some additional details to aid in troubleshooting:

[LIST]
[*]The error Plex logs when trying to use hardware transcoding:
```
ERROR - [FFMPEG] - No VA display found for device: /dev/dri/renderD128.
```
[*]CPU: i7-8700
[*]Motherboard: MSI Z370 Gaming Plus (MS-7B61)
[*]Ubuntu version: 18.10 Cosmic Cuttlefish (development branch)
[*]Current kernel: 4.18.0-7-generic
[*]```
vainfo
error: failed to initialize display
```
[*]```
sudo lshw -C video
*-display UNCLAIMED
   description: VGA compatible controller
   product: Intel Corporation
   vendor: Intel Corporation
   physical id: 2
   bus info: pci@0000:00:02.0
   version: 00
   width: 64 bits
   clock: 33MHz
   capabilities: pciexpress msi pm vga_controller bus_master cap_list
   configuration: latency=0
   resources: memory:de000000-deffffff memory:c0000000-cfffffff ioport:f000(size=64) memory:c0000-dffff
```
[*]```
lsmod | grep i915
```
(nothing)
[*]```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Device 3e92
```
[*]```
ls /dev/dri
ls: cannot access '/dev/dri': No such file or directory
```
[/LIST]
I would really appreciate any help getting this working. Let me know if there's any further information you'd like me to collect.

---

### Post by canadrian on 2018-10-04
For anyone who stumbles across this thread in a search: after using ukuu to update to mainline kernel 4.18.11-041811-generic, hardware video transcoding with Quick Sync now works. If you update your kernel to 4.18.11-041811-generic and that alone doesn't solve the issue, perhaps the updated video drivers from the oibaf PPA are needed too; I already had those installed prior to updating my kernel.

---

