---
title: "acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration"
date: 2018-05-22
forum: Hardware
---

### Post by lennybruyninckx on 2018-05-22
Hi guys,

Can someone help me with this? I am not a experienced Linux/Ubuntu user so I totally don't know how I can solve this.

I have loads of hardware "errors" in my system log and this is one of them. I have searched on Google and Ubuntu forms but nothing came up which could solve this problem.

```
acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
```

```
acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability]
```

```
acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME]
```

```
acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
```

So what I can read from this is that something does not support something. I did not had this problem at all under Ubuntu 17.10. I changed my OS to Ubuntu 18.04 LTS because of the long term support. I did a "clean install" so I formatted my SSD and installed Ubuntu 18.04 LTS on it.
I also noticed that my sound card is now not fully supported anymore. My line in is gone, no options there which I had in Ubuntu 17.10.


Thank you for helping!

Kind regards,
Lenny Bruyninckx

---

### Post by Yellow Pasque on 2018-05-23
Have you tried booting with "pcie_aspm=off" parameter?
What model computer/laptop is this and is your BIOS/EFI up to date?

---

### Post by lennybruyninckx on 2018-05-23
I am using a desktop.

My MoBo is a MSI Z87-G45 Gaming and I am running the latest BIOS version on it (V1.9).
My processor is a Intel Core i7-4770K @ 3.50GHz
I have 24576 MB memory installed on it.
My graphics card is an MSI nVidia GeForce GTX 660 with 2 GB on memory.

Where can I find the "pcie_aspm" parameter?

---

### Post by Yellow Pasque on 2018-05-23
[https://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter](https://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter)

---

