---
title: "Hibernate no longer works on new hard drive"
date: 2009-04-05
forum: Hardware
---

### Post by kfhughes on 2009-04-05
I upgraded my laptop with 8.10 installed from a 100GB drive to a 320GB drive.  I patitioned the new drive, booted from a LiveCD, tarred the old root file system to the new drive, put the new drive in, and booted up.  Before this, hibernate worked fine.

On the new drive, I discovered that I hadn't set up the swap partition, so ran mkswap and verified on reboot that Linux saw the partition.  When I now hibernate, everything seems to go correctly but when I power back up Grub comes up almost immediately (it used to take 15 seconds or so) and when I select which kernel to boot it ignores the disk image and does a cold boot, with numerous fsck problems since the file systems are not clean.

Is there something else I need to tell grub to make it look for the right swap partition, something I need to do to the kernels so they know, or something I need to do to make sure the image is being written to the right place?

---

### Post by mike-g2 on 2009-04-05
I'm running into the exact same problem but with a T60 and a new HD and I'm running 8.04.

Just for the record, initially I couldn't hibernate, it would go through the motions and then kick up the locked screen saver as if I had hibernated and then restarted.  Making sure that my swaps UUID values in /etc/fstab matched the ones I was getting from the blkid command fixed that problem.

So now my machine goes into hibernatation but when it comes out it does a complete reboot.

Attached is gzipped output from /var/log/messages from when I hibernated and it went into a full restart.

Anyone got any clues?

Mike

---

### Post by kfhughes on 2009-04-07
Solved the problem.  The UUID value for the swap partition needs to be set in /etc/initramfs-tools/conf.d/resume.  The postinstall script for initramfs-tools detects the swap partition and creates the file, then running update-initramfs on the kernel incorporates this info into the ram image.

I removed /etc/initramfs-tools/conf.d/resume by hand, reran /var/lib/dpkg/info/initramfs-tools.postinst by hand, then from synaptic did a reinstallation of my linux-image kernel (running update-initramfs should also accomplish this).

---

### Post by mike-g2 on 2009-04-07
Hi,

Thanks kfhughes for the post.  I followed your directions, but they didn't work until I (a) updated my /etc/initramfs-tools/conf.d/resume file by hand so that it reflected the new UUID for swap and (b) reinstalled both the linux-image-2.6.24-23 and linux-image-generic.  That did the trick!

Cool beans!

Mike

---

