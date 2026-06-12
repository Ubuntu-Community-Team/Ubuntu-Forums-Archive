---
title: "Moving existing installation to USB drive?"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by Fafler on 2009-09-04
How can i move an Linux installation from a internal SATA drive to a USB flash drive? It's a vanilla Ubuntu 9.04 on encrypted LVM.

I want to do this to save battery and produce less heat on my laptop by using the SATA drive for data i rarely use and store / on the flash drive. Right now i'm going to use a 8 gb Kingston drive for testing, but if stability and performance is good enough i'll consider something like a MiniPCIe to USB adapter or a ExpressCard/34 flash drive.

I've tried some info i found on the net, but for some reason running Linux from a USB drive seems restricted to live-CD like enviroments.

---

### Post by ronparent on 2009-09-04
I don't know about linux as a general case but you can easily move ubuntu to wherever you please! Simply cut and paste using gparted from a live cd. You will probably have to setup grub to boot it. Keep in mind the new install will have the same uuid as the old install. So if you leave the old install on the computer you won't know for sure which one is booting! Have fun.

edit: I should have read the heading. The same applies to a usb drive. I know, I've done it.

---

### Post by Fafler on 2009-09-06
The problem with that is that i would need to shrink my LVM to 8 gb to make it fit on the USB drive.

Anyway, i found a way to make a new installation on the flash drive:

I installed Virtualbox and did

```
sudo VBoxManage internalcommands createrawvmdk -filename /home/fafler/usb.vmdk -rawdisk /dev/sdb
sudo virtualbox
```

After that Virtualbox was able to use the flash drive as a regular disk, and i just installed, rebooted the physical laptop with the flash drive connected, imported my WPA key from another flash drive, and now i'm writing this.

And i know sudo virtualbox is bad, but i needed R/W access. A temporary chmod didn't work as Ubuntu changes the permissions back a chort while after, and adding my user to disk didn't seem like a good choice either.

---

### Post by Fafler on 2009-09-06
Most of the time speed is almost as good as with the SATA drive. 90% of the time i use my laptop i'm using firefox and totem, and both appliations work fine from the flash drive. But write operations are really slow and the system tends to stall whenever a background process writes to the flash drive. Maybe another scheduler will improve performance. Any suggestions?

And of course, a new flash drive actually brought for the purpose and not just to get cheap removable storage will improve things as well.

Only one thing seems to be broken. Suspending works fine as far as i can tell, but the system won't restore. Even though the LED's come back on, the screen stays black and nothings happen.

---

