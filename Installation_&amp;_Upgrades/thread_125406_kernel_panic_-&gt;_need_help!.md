---
title: "kernel panic -&gt; need help!"
date: 2006-02-03
forum: Installation &amp; Upgrades
---

### Post by chugru on 2006-02-03
I'm a new kubuntu breezy user, and have been trying to set my box to run on a newly downloaded linux tree. My guide for setting up the kernel is [https://wiki.ubuntu.com/KernelByHandHowto](https://wiki.ubuntu.com/KernelByHandHowto) 

After using **make oldconfig** and then checking over **menuconfig**, I followed the Howto steps, including these new grub entries:```
title=Kubuntu, kernel 2.6.12
  root  (hd0,0)
  kernel  /vmlinuz root=/dev/hda1
  boot

title=Linux Stable
  root  (hd0,0)
  kernel /vmlinuz.stable root=/dev/hda1
  initrd /initrd.stable
  boot


```

Rebooting produces **kernel panic**, and I'm forced to reboot with my "Linux Stable" boot menu entry (title=Linux Stable in grub), which points to a copy of my original kernel.


Here's the **kernel panic** error message: ```
VFS: Cannot open root device "hda1" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

Googling didn't help me. Does anyone have a suggestion of what steps to take??

Thanks...

---

