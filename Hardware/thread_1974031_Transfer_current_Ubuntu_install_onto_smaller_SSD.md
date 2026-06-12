---
title: "Transfer current Ubuntu install onto smaller SSD"
date: 2012-05-05
forum: Hardware
---

### Post by larrythemule on 2012-05-05
Hi everyone, 

I want to put a solid state disk into my laptop. At the moment I have 120GB conventional hard disk with about 90GB of free space, that I can't really see ever being used. Ubuntu is the only operating system on the disk.

From reading other forums I'm aware that I will need a USB to SATA connection and using the tools in live mode of an install disk or USB, I will need to resize the partition on the old disk and transfer it over to the SSD. 

I'm not completely sure of the exact procedure though, can anyone give me some more detailed instructions please?

Thanks everyone.

---

### Post by ahallubuntu on 2012-05-05
Yes, you've got the right idea.

First, boot a live CD or live USB.  You'll want to run gparted from there.  If by chance gparted isn't installed in the live environment, install it.  Or grab a copy of the Parted Magic Linux distro that includes gparted already and burn that CD and boot it instead.

You don't mention your partition scheme.  Can we assume you have just one big partition for / and a swap partition?  If that's the case, and you have one big / partition, use gparted from live media to shrink it down to say 40GB (assuming your SSD is a bit larger than that).

At that point there are a number of ways to proceed.  You could try cloning with Clonezilla (included on Parted Magic) and see if you can do it semi-automatically, assuming you have a USB hard drive adapter/enclosure to connect both the SSD and old hard drive at the same time.  If you don't have the USB adapter but have access to a large external hard drive (or one large enough to contain a 40GB file), you could try copying the partition to a  file on external drive, then swap in your new SSD and restore the partition.  There's a nice program called partimage (also on Parted Magic) that can do this, but the dd terminal program is a crude way to do it too:

```
sudo dd if=/dev/sda1 of=/media/extdrive/myimage.bin bs=4096
```

and then you can restore it to your new drive in a similar way.

(Be CAREFUL with the dd command - don't type it incorrectly, it can be very destructive if you do!!!)

After that, you'd need to resize the new partition again on the SSD but make enough room for a swap partition, which you'll have to create again in gparted.  When that's done, you can edit /etc/fstab to update the UUID of the swap partition.

Re-installing Grub may be required as a last step.

---

### Post by larrythemule on 2012-05-05
Great. Thanks for your advice :)

I think I'm going to go with Parted Magic, assuming you can create a bootable USB stick with that distro (laptop has no working cd drive).

Hopefully it is easy to put the disk image on an external hard disk, I have one but I'm worried I'll wipe it when transferring my image over. 

I followed everything upto this point. How big should I make the swap partition? How do I update the UUID and what should the new value be? Is re-installing Grub something I can do with a tool?


> **ahallubuntu said:**
> 

After that, you'd need to resize the new partition again on the SSD but make enough room for a swap partition, which you'll have to create again in gparted.  When that's done, you can edit /etc/fstab to update the UUID of the swap partition.

Re-installing Grub may be required as a last step.

Thanks again :)

---

