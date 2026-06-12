---
title: "Need Driver for SIS 760m"
date: 2017-04-12
forum: Hardware
---

### Post by linuxn00b2 on 2017-04-12
Hi, i need drivers for the sis m760 because the resolution is stuck at 640x480.

---

### Post by mörgæs on 2017-04-12
'Need drivers' is a Windows way of thinking. In GNU/Linux the drivers are normally present in the kernel but they might need adjustment.

Please run ```
sudo lshw -C video
``` and post the results in CODE tags.

---

### Post by oldfred on 2017-04-12
What version of Ubuntu?

 The stock kernel of Ubuntu 17.04 is doing away with Direct Rendering Manager (DRM) support for a number of ancient graphics processors.
3Dfx Banshee/Voodoo3+, ATI Rage 128, Matrox G200/G400, SIS, VIA, and Savage hardware
This was done because they expose insecure APIs to user-space. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276)

---

### Post by linuxn00b2 on 2017-04-22
```

```*-display UNCLAIMED       
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:d0000000-d7ffffff memory:dfee0000-dfefffff ioport:cc00(size=128) memory:c0000-dffff

---

### Post by Yellow Pasque on 2017-04-23
This may be of interest: [https://ubuntuforums.org/showthread.php?t=2350126&p=13599531#post13599531](https://ubuntuforums.org/showthread.php?t=2350126&p=13599531#post13599531)
(note there's a typo and that "sudo apt-get install xutils.dev" should be "xutils-dev")

---

### Post by lah-ca on 2017-04-26
> **Temüjin said:**
> This may be of interest: [https://ubuntuforums.org/showthread.php?t=2350126&p=13599531#post13599531](https://ubuntuforums.org/showthread.php?t=2350126&p=13599531#post13599531)
(note there's a typo and that "sudo apt-get install xutils.dev" should be "xutils-dev")

Hi,

Mörgæs brought this to my attention.  I will fix it in the two places the summary/tutorial exists.

Thx.

---

