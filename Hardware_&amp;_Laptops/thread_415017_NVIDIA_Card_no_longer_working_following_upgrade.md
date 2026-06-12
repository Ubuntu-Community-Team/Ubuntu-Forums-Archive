---
title: "NVIDIA Card no longer working following upgrade"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by the_dark_light on 2007-04-20
My NVIDIA card no longer works on Ubuntu Feisty, following my upgrade from edgy.

Under edgy I was using NVIDIAs own driver (installed from their own binary) and that worked fine.

Since I upgraded to Feisty, I had to reinstall the driver (it no longer reached X when it booted, NVIDIA errors.  Sorry I can't remember them)

This corrects the problem for that session only.  The strange thing was that this happened every time I needed to reboot, so I had to run the NVIDIA installer every time I started up the computer.

Finally, out of desperation I uninstalled the driver and installed the driver through apt-get:

sudo apt-get install -y nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig --add-argb-glx-visuals

Now I get the following error when trying to start X: (truncated for the reason of preserving my sanity)

Error: API mismatch: the NVIDIA kernel module has the version 1.0-9631.  Please make sure the kernel module and all NVIDIA driver components have the same version.

Can anyone help resolve this? :confused:

---

### Post by etherealremnant on 2007-04-20
Its the stupid restricted modules manager that came with Feisty doing that to you.

It comes with the module for 9631 which overtakes the 9755 every time you reboot.

I'm trying to find a way around this myself. I tried uninstalling the restricted manager completely but that didn't work...

---

### Post by dank277 on 2007-04-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/restricted-manager/+bug/108128](https://bugs.launchpad.net/ubuntu/+source/restricted-manager/+bug/108128) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Look at my bug report (link attached).  I had the exact same problems, and this was my solution.

---

### Post by cainmark on 2007-04-21
Exact same problem.  Finally got my new nvidia card working in Edgy.  When I uprgraded, I had the kernel mismatch problem as well.

---

### Post by the_dark_light on 2007-04-21
in the end, my (rather extreme) solution was to simply perform a fresh install of Feisty.  No more gremlins, no problem (I'm now using the restricted drivers through synaptic, rather than NVIDIAs own installer)

---

