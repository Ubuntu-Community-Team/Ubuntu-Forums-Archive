---
title: "Kernel 2.6.24-24 broke RAID array, won't boot"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by cfgauss on 2009-05-05
Today's upgrade to kernel 2.6.24-24-server on my Intrepid Ibex box has caused it not to boot. The kernel cannot find my root partition, /dev/md3. The previous kernel now gives me that same error.

I have a RAID array and when I boot from the Live CD,

# mdadm --assemble --scan

reassembles with RAID array without difficulty. I think it might have something to do with the initrd that came with the new kernel.

Is that possible?

If so, how do I make a new initrd as it seems that mkinitrd is no longer part of Intrepid Ibex.

Thanks for any hint you can provide on what might be wrong.

I'm running Ubuntu 8.04 (which may or may not be Intrepid Ibex.)

SOLVED: I needed to add irqpoll to the kernel boot line of 2.6.24-23-server. I had to do that a few kernels ago but didn't have it on the most recent kernel so the kernel upgrade didn't add it. Without irqpoll on this kernel, the RAID array is not assembled by the kernel drivers. I could *not* get 2.6.24-24-server working even with this addition and will soon be deleting it.

---

### Post by TomB19 on 2009-05-06
Have you tried 'chroot'ing into the system and then doing a 'update-initramfs'?


On another topic, I also have a software RAID root partition.  I have found it convenient to use a non-RAID boot partition, though.  Since I already have 10 drives in the system and no room for one more, I boot from a USB flash drive.  It works great.  For boot files, a 1 GB USB drive is cheap and more than fast enough.  ... just an idea.

---

### Post by cfgauss on 2009-05-06
> **TomB19 said:**
> Have you tried 'chroot'ing into the system and then doing a 'update-initramfs'?
Yes. I booted with an 8.10 Live CD, chrooted and
```
$ sudo update-initramfs -u -k all
```
and it generated new initrd's for all kernels in menu.lst. But I still get the following error, even when I use the old kernel, 2.6.24-23-generic in recovery mode:
```
VFS: Cannot open root device "md3" or unknown-block(0,0)
Please append a correct "root=" boot option; here are the available partitions:
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

```
Since it doesn't list any available partitions, it appears that the kernel is not assembling the RAID partitions. So I reconfigured:
```
$ sudo dpkg-reconfigure mdadm
```
I got a warning, which I believe I've gotten before:
```
cryptsetup: WARNING: found more than one resume device candidate:
/dev/md1
UUID=...
```
/dev/md1 is my swap partition. I then examined /etc/mdadm/mdadm.conf and discovered that it had incorrect UUID's. At least they were different from
```
$ sudo vol_id /dev/mdn
``` where n = 0,1,2,3. So I manually changed them, saving the old mdadm.conf. But it still can't find /dev/md3, my root partition, at boot. Does the kernel use /etc/mdadm/mdadm.conf to assemble the RAID partition? That wouldn't seem possible since /dev/md3 hasn't been mounted yet and it contains /etc/mdadm/mdadm.conf. The hard disks are all of the proper type: /dev/sdxy where x = a,b,c and y = 1,2,3,4 are all Linux raid autodetect and my old kernel had no problems assembling the array at boot and mounting /dev/md3. (Of course, now it won't.)

The server is important to my job here. Any suggestions will be gratefully received.

---

