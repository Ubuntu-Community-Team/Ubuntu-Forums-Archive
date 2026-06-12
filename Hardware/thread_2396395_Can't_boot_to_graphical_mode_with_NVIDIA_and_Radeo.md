---
title: "Can't boot to graphical mode with NVIDIA and Radeon GPU installed."
date: 2018-07-14
forum: Hardware
---

### Post by jb-morgado on 2018-07-14
I had a system with only a NVIDIA GTX 1080 in the primary PCI-e slot and it was working fine.

I now tried to install a Radeon 5450 in the secondary PCI-e slot and set the BIOS to use that slot to boot. The problem is that now, Ubuntu doesn't boot into the graphical Gnome Desktop Manager, it stays in console text  mode.

The last message I have at boot is **"started Gnome Desktop Manager**", but there is no manager present. There is also no error in the boot messages.

The only way to workaround the problem, is to blacklist all of NVIDIA modules in grub, that way it boots fine into the Gnome Desktop Manager (but of course, that make the NVIDIA card unusable).

Any ideas on how to fix this?

---

