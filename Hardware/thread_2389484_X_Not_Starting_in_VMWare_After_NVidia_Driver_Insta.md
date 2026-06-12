---
title: "X Not Starting in VMWare After NVidia Driver Installed"
date: 2018-04-17
forum: Hardware
---

### Post by jizzyjugs on 2018-04-17
So I have an Ubuntu Gnome boot partition on a physical drive on my system that is working as expected when using it on its own.
I also configured VMWare in another OS on another drive to point to and boot the physical device on which Ubuntu resides.
This worked fine using the vmware gfx driver for the VM and the nouveau driver otherwise. However, after replacing nouveau with the nvidia-390 driver, I can now no longer get X/GDM to start when booting in VMWare.
It appears to be related to X being unable to load the GLX extension using the vmware driver.

Any way that I can get this configuration working again?

Here's the relevant output of lspci in VM:
```

$ lspci | grep VGA
00:0f.0 VGA compatible controller: VMware SVGA II Adapter

```
And with the system running on the hardware itself:
```

$ lspci | grep VGA
65:00.0 VGA compatible controller: NVIDIA Corporation Device 1b06 (rev a1)

```

And I've attached my Xorg.log from the VM.

---

