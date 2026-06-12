---
title: "Debug failed suspend/resume"
date: 2010-07-30
forum: Hardware
---

### Post by StefanX on 2010-07-30
I use the MSI Megabook S260 but unfortunately the suspend/resume functionality fails; not every time but about each second time.

I added "set -x" option to /etc/acpi/sleep.sh but the logs are not very helpful to me. I recognized that the sleep phase is followed instantly by the resume phase which should be wrong. Unfortunately I could not recognize any other hints. 

I read several instructions how to debug such a problem ([http://ubuntuforums.org/showthread.php?p=3066404](http://ubuntuforums.org/showthread.php?p=3066404) [http://ubuntuforums.org/showthread.php?t=1144999](http://ubuntuforums.org/showthread.php?t=1144999) [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend) [http://ubuntuforums.org/showthread.php?t=814939](http://ubuntuforums.org/showthread.php?t=814939) [https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume#Debugging%20Suspend](https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume#Debugging%20Suspend)). I am not a kernel hacker and confused about the different possibilities to debug the problem and which of them may be appropriate for my case. Also some of these instructions are old and I am doubt if they are still relevant. Please help me to identify the next steps to solve this problem.

kern.log:
```
Jul 30 19:10:16 msi kernel: [13069.036033] PM: Preparing system for mem sleep
Jul 30 19:10:16 msi kernel: [13069.036038] Freezing user space processes ... (elapsed 0.07 seconds) done.
Jul 30 19:10:16 msi kernel: [13069.106509] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Jul 30 19:10:16 msi kernel: [13069.106572] PM: Entering mem sleep
Jul 30 19:10:16 msi kernel: [13069.106590] Suspending console(s) (use no_console_suspend to debug)
Jul 30 19:10:16 msi kernel: [13069.120071] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Jul 30 19:10:16 msi kernel: [13069.120188] sd 0:0:0:0: [sda] Stopping disk
Jul 30 19:10:16 msi kernel: [13069.490309] PM: suspend of drv:sd dev:0:0:0:0 complete after 370.239 msecs
Jul 30 19:10:16 msi kernel: [13069.932139] PM: suspend of drv:psmouse dev:serio1 complete after 441.777 msecs
Jul 30 19:10:16 msi kernel: [13069.939058] ACPI handle has no context!
Jul 30 19:10:16 msi kernel: [13069.939099] eth1: Going into suspend...
Jul 30 19:10:16 msi kernel: [13069.941798] ipw2200 0000:01:09.0: PCI INT A disabled
Jul 30 19:10:16 msi kernel: [13069.941803] ACPI handle has no context!
Jul 30 19:10:16 msi kernel: [13069.972202] sdhci-pci 0000:01:05.2: PCI INT A disabled
Jul 30 19:10:16 msi kernel: [13069.988285] ata_piix 0000:00:1f.1: PCI INT A disabled
Jul 30 19:10:16 msi kernel: [13069.988490] Intel ICH 0000:00:1e.2: PCI INT A disabled
Jul 30 19:10:16 msi kernel: [13069.988520] ehci_hcd 0000:00:1d.7: PCI INT A disabled
Jul 30 19:10:16 msi kernel: [13069.988528] uhci_hcd 0000:00:1d.3: PCI INT D disabled
Jul 30 19:10:16 msi kernel: [13069.988535] uhci_hcd 0000:00:1d.2: PCI INT C disabled
Jul 30 19:10:16 msi kernel: [13069.988542] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Jul 30 19:10:16 msi kernel: [13069.988549] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Jul 30 19:10:16 msi kernel: [13070.038984] i915 0000:00:02.0: PCI INT A disabled
Jul 30 19:10:16 msi kernel: [13070.052290] PM: suspend of devices complete after 945.468 msecs
Jul 30 19:10:16 msi kernel: [13070.052294] PM: suspend devices took 0.948 seconds
Jul 30 19:10:16 msi kernel: [13070.068162] PM: late suspend of devices complete after 15.863 msecs
Jul 30 19:10:16 msi kernel: [13070.068939] ACPI: Preparing to enter system sleep state S3
Jul 30 19:10:16 msi kernel: [13070.069358] Disabling non-boot CPUs ...
Jul 30 19:10:16 msi kernel: [13070.069382] Back to C!
Jul 30 19:10:16 msi kernel: [13070.069382] CPU0: Thermal monitoring enabled (TM1)
Jul 30 19:10:16 msi kernel: [13070.069382] Force enabled HPET at resume
Jul 30 19:10:16 msi kernel: [13070.069382] ACPI: Waking up from system sleep state S3
Jul 30 19:10:16 msi kernel: [13070.084223] pci 0000:00:02.1: restoring config space at offset 0x4 (was 0x0, writing 0xfbd80000)
Jul 30 19:10:16 msi kernel: [13070.084229] pci 0000:00:02.1: restoring config space at offset 0x1 (was 0x900000, writing 0x900007)
Jul 30 19:10:16 msi kernel: [13070.084253] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Jul 30 19:10:16 msi kernel: [13070.084278] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Jul 30 19:10:16 msi kernel: [13070.084302] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Jul 30 19:10:16 msi kernel: [13070.084326] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Jul 30 19:10:16 msi kernel: [13070.084358] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
Jul 30 19:10:16 msi kernel: [13070.084377] pci 0000:00:1e.0: restoring config space at offset 0xf (was 0x60000, writing 0x600ff)
...startup seems to be executed without any problem...
```

---

