---
title: "Keep USB Keyboard in Kernel on suspend"
date: 2007-12-01
forum: Hardware &amp; Laptops
---

### Post by dwns on 2007-12-01
I've been trying for a while to solve this problem, but without any progress.
When I put my computer to sleep/suspend, which works well, the only way to wake
it up is to press the powerbutton. I would like to wake it back up using the keyboard or mouse, though the computer is hard for my to reach.
  In Vista, I have dual boot, this works perfectly, therefore I think it shall work in Ubuntu.
I've been trying to put the usbmodules in the Whitelist in acpi-support, but it doesnt help.
It seems there's nothing to do with the configfiles, so I'm wondering if there's any other way to solve this..

this is from kern.log: (just before it goes to sleep)

Dec  1 21:22:23 jens-ubuntu kernel: [  228.101031] PM: Preparing system for mem sleep
Dec  1 21:22:23 jens-ubuntu kernel: [  228.101041] Stopping tasks ... done.
Dec  1 21:22:23 jens-ubuntu kernel: [  228.187587] Suspending console(s)
Dec  1 21:22:23 jens-ubuntu kernel: [  228.271852] sd 3:0:0:0: [sdb] Synchronizing SCSI cache
Dec  1 21:22:23 jens-ubuntu kernel: [  228.271963] sd 3:0:0:0: [sdb] Stopping disk
Dec  1 21:22:23 jens-ubuntu kernel: [  228.272115] sd 2:0:0:0: [sda] Synchronizing SCSI cache
Dec  1 21:22:23 jens-ubuntu kernel: [  228.363513] sd 2:0:0:0: [sda] Stopping disk
Dec  1 21:22:23 jens-ubuntu kernel: [  228.720411] pnp: Device 00:06 disabled.
Dec  1 21:22:23 jens-ubuntu kernel: [  228.735221] ACPI: PCI interrupt for device 0000:03:06.0 disabled
Dec  1 21:22:23 jens-ubuntu kernel: [  228.767681] NVRM: RmPowerManagement: 3
Dec  1 21:22:23 jens-ubuntu kernel: [  229.211546] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Dec  1 21:22:23 jens-ubuntu kernel: [  229.244201] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
Dec  1 21:22:23 jens-ubuntu kernel: [  229.244204] pci_set_power_state(): 0000:00:1f.1: state=3, current state=5
Dec  1 21:22:23 jens-ubuntu kernel: [  229.244298] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Dec  1 21:22:23 jens-ubuntu kernel: [  229.259541] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
Dec  1 21:22:23 jens-ubuntu kernel: [  229.259568] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
**Dec  1 21:22:23 jens-ubuntu kernel: [  229.259594] ACPI: PCI interrupt for device 0000:00:1d.1 disabled**
Dec  1 21:22:23 jens-ubuntu kernel: [  229.259620] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Dec  1 21:22:23 jens-ubuntu kernel: [  229.260354] Disabling non-boot CPUs ...
Dec  1 21:22:23 jens-ubuntu kernel: [  229.273693] CPU 1 is now offline
Dec  1 21:22:23 jens-ubuntu kernel: [  229.273697] SMP alternatives: switching to UP code
Dec  1 21:22:23 jens-ubuntu kernel: [  229.274257] CPU1 is down
Dec  1 21:22:23 jens-ubuntu kernel: [  229.274260] PM: Entering mem sleep
Dec  1 21:22:23 jens-ubuntu kernel: [    0.188275] Back to C!


0000:00:1d.1 is my keyboard device, which I'd like to be left in the kernel, but I think this is the line where it's killed:
"**Dec  1 21:22:23 jens-ubuntu kernel: [  229.259594] ACPI: PCI interrupt for device 0000:00:1d.1 disabled**"



Any ideas??

---

