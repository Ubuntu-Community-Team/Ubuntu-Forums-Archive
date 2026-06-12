---
title: "Jaunty Expresscard Hotplug"
date: 2009-04-23
forum: Hardware
---

### Post by FinalStar on 2009-04-23
I posted this in Desktop, but realized i should have probably put it here.

I just finished installing 9.04 and am trying to get my wireless Atheros card to work. Having the drivers already installed is nice, and the card works fine if I boot with it in the computer, but I want to get the hot plugging working again. I tried looking for pciehp but it doesn't seem to exist anymore. If i boot the computer with the card in, it actually looks like its loading the pciehp module. But lsmod shows nothing. I still cant locate it either.

Has anyone gotten hot plugging working in 9.04?

---

### Post by size_XXM on 2009-05-23
Hmm, looking through the configuration file for the jaunty kernel, the PCIe hotplugging was compiled into the kernel, there's no loadable module. Since this apparently isn't enough, you may need to pass the _force=1 option.
If you had the card hotplug working before, I assume you've done so by issuing ```
sudo modprobe pciehp pciehp_force=1
```
I don't hack around Linux that much but according to an unrelated bug report I stumbled upon ([link](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271700)), options for non-module parts of the kernel are passed at boot-time, ie. you put that option at the end of the kernel line in /boot/grub/menu.lst (see the link for a more detailed explanation and also the "# defoptions" line, where you should also put options you wish to preserve with kernel updates.

I installed Jaunty and was stumped by the lack of pciehp module but it seems this should work (haven't tried yet).

Hope this helps.

Edit: Tried it and works. Just add the option **pciehp.pciehp_force=1** to the kernel line of boot entries you wish to change this way (I put it on both normal and recovery mode options):
```
title           Ubuntu 9.04, kernel 2.6.28-11-generic
...
kernel          /boot/vmlinuz-2.6.28-11-generic root=... ro quiet splash **pciehp.pciehp_force=1**
initrd          /boot/initrd.img-2.6.28-11-generic
quiet
savedefault
```

---

### Post by nichot20 on 2009-06-08
> **size_XXM said:**
> Just add the option **pciehp.pciehp_force=1** to the kernel line of boot entries you wish to change this way (I put it on both normal and recovery mode options):
```
title           Ubuntu 9.04, kernel 2.6.28-11-generic
...
kernel          /boot/vmlinuz-2.6.28-11-generic root=... ro quiet splash **pciehp.pciehp_force=1**
initrd          /boot/initrd.img-2.6.28-11-generic
quiet
savedefault
```

I too found this worked, having been puzzled by the lack of the module. However on my Aspire one I found that doing so interfered with the operation of the wifi! :(

What happens is, on boot up I get several "unable to add..already exists" type messages flashing past and then when I am finally at the desktop when the wifi scans for AP's it seems to stop after finding the first one, and if that is not the one you want you are scuppered!

Removing the line from the grub options instantly restores wifi sanity!!

---

### Post by klecu on 2009-06-16
nichot20, do you have the ath_pci (madwifi) drivers, or the ath5k/ath9k drivers? I've had better success with the ath_pci driver, but the last few days, my wifi has been randomly disappearing from the system. Thought it might be related to pciehp_force=1 boot option, but I'm still testing that theory.

Check the AspireOne on Ubuntu community docs for info on the madwifi driver.

---

### Post by size_XXM on 2009-10-07
Hmm, still not working OotB in Karmic, some suggestions after months of usage:

Put the option to defaults - that way, the option will be added to any new kernel you get through update.

In grub 1 (jaunty and older):
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash **pciehp.force=1**
```

In grub 2, the def-options line is now in /etc/default/grub:
```
GRUB_CMDLINE_LINUX_DEFAULT="**pciehp.pciehp_force=1** quiet splash"
```
The menu.lst becomes /boot/grub/grub.cfg where you can change the commandline for the current kernels:
```
linux   /boot/vmlinuz-2.6.31-12-generic root=(omitted) ro   **pciehp.pciehp_force=1** quiet splash
```

---

