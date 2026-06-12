---
title: "couldn't find physical volume"
date: 2007-04-08
forum: Hardware &amp; Laptops
---

### Post by bwald on 2007-04-08
Hello,

I recently installed an extra SATA crontroller and two SATA harddrives. I set up the two drives with a RAID1 configuration and then formated the RAID device as a physical volume and added it to a volume group and logical volume. Everything was going fine until we had a poweroutage and I turned the computer back on. I'm now getting an error during boot that says:

<code>
ERROR: /bin/lvm exited abnormally! (pid 325)
Activating logical volumes
Couldn't find device with uuid 'Tdwhgy-GuXu-dkyz-y3d0-K2Xh-UB1j-X61y3T'
Couldn't find all physical volumes for volume group VolGroup00.
Couldn't find device with uuid 'Tdwhgy-GuXu-dkyz-y3d0-K2Xh-UB1j-X61y3T'
Couldn't find all physical volumes for volume group VolGroup00.
Couldn't find device with uuid 'Tdwhgy-GuXu-dkyz-y3d0-K2Xh-UB1j-X61y3T'
Couldn't find all physical volumes for volume group VolGroup00.
Couldn't find device with uuid 'Tdwhgy-GuXu-dkyz-y3d0-K2Xh-UB1j-X61y3T'
Couldn't find all physical volumes for volume group VolGroup00.
ERROR: /bin/lvm exited abornomally (pid 326)
Creating root device
Mounting root filesystem
mount: error 6 mounting ext3
mount: error 2 mounting none
Switching to new root
switchroot: mount failed: 22
umount /initrd/dev failed: 2
Kernel panic - not syncing: Attempting to kill init!
</code>

Then it freezes and stops doing anything. I don't know what to do, and any help you can provide would be greatly appreciated.

Ben Wald

---

