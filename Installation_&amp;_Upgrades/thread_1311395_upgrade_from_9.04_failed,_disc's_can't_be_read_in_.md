---
title: "upgrade from 9.04 failed, disc's can't be read in 9.10"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by pandam@n on 2009-11-02
Hi everyone!

I have a rather odd problem.
I upgraded my Ubuntu 9.04 to 9.10 from the gui. Everything seemed to work out well. But when I rebooted nothing happened. So here is the problem:
2 of 4 discs can't be read by 9.10. One os those two are the Ubuntu-partition.
Everything can be mounted in 9.04 live-cd. But in 9.10 live CD it says that blockes may be bad. In short terms the / can't be mounted in 9.10 (it is ext3). When I try to boot the 2.6.31.1 kernel, it stops in the initramfs-console says that the uuid is wrong. I have checked that it is not wrong, only that the kernel can't read the disc at all.... So the menu.lst and the fstab is correct. Since the 9.04-livecd have no problems reading any of the 4 discs, I have not run any disc-check from the 9.10-livecd yet...

I see also that I don't have the newest kernel (cause I upgraded on saturday)
Is there any way to install the new kernel? or is there any way to downgrade to 9.04?

---

### Post by pandam@n on 2009-11-02
I have read a quite a lot in the forums, but seems like most solve their problem by running:

update-grub
dpkg --configute -a

But I have tried that as well from the 9.04-livecd

---

### Post by mushr00m on 2009-11-02
I am experiencing an identical problem after dist-upgrading.  uuids and fstab are good.  The 2.6.28-16-generic kernel loads (with no sound) and the 2.6.31.1 kernel drops to the initramfs command line.

I'm swapping out hard drives and starting a fresh install from USB key tonight.

---

### Post by pandam@n on 2009-11-04
> **mushr00m said:**
> I am experiencing an identical problem after dist-upgrading.  uuids and fstab are good.  The 2.6.28-16-generic kernel loads (with no sound) and the 2.6.31.1 kernel drops to the initramfs command line.

I'm swapping out hard drives and starting a fresh install from USB key tonight.

mhm, seems like 9.04 fresh install is the only choice left...

---

