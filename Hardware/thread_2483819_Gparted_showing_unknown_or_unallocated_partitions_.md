---
title: "Gparted showing unknown or unallocated partitions on HDD"
date: 2023-02-09
forum: Hardware
---

### Post by leopheard on 2023-02-09
Hi all,

I have noticed recently that my HDD has two partitions that seem to have errors. **Screenshots attached**.

I have somehow got a /dev/sda3 7.89 Gb partition with an unknown filesystem and another with no mount point and filesystem 'unallocated'.

The info markers on sda3 are attached.

Was this made by Ubuntu for a reason, was there file corruption or something or is it just an error? Can I just delete the bottom 2 partitions, then resize sda2? The boot point will be fine?

Also, I have absolutely no idea how my mount point on my main HDD is:

```
Mounted on /, /var/snap/firefox/common/host-hunspell
```

Any advice would be greatly appreciated.

---

### Post by ajgreeny on 2023-02-09
My suspicion is that **/dev/sda3** is a swap partition but is not included in **/etc/fstab** for some reason. To confirm this (or not) can you please show us the output of ```
cat /etc/fstab
``` and also to show us your current mounted filesystems show us the output of ```
mount | grep /dev/sd
``` as I am uncertain about why there appears to be two mountpoints shown for /dev/sda2, though this may be related to the use of snap applications, in your case firefox which I don't have as a snap.

You can forget about the 1.02MB partition as that is simply related to the way partitioning is still done using blocks; my disk always has a similar 1.02MB unallocated space at the end.

---

### Post by deadflowr on 2023-02-09
> Mounted on /, /var/snap/firefox/common/host-hunspell
This actually the Firefox snap package workaround they implemented in order for Firefox to be able to use the system-wide installed dictionary packages.
So it is normal, or as normal as anything snap related can be.

---

### Post by ajgreeny on 2023-02-10
Thanks **deadflowr**.
I do not have any snaps on my systems so was certainly not aware of this, nor many of the other snap difficulties that users seem to keep finding.

---

