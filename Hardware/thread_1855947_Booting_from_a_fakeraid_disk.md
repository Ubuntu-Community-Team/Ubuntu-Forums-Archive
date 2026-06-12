---
title: "Booting from a fakeraid disk"
date: 2011-10-07
forum: Hardware
---

### Post by [S|G] on 2011-10-07
I recently installed Ubuntu on my MSI GT780R laptop and ran into problems due to its fakeraid setup. From the installer I managed to see all partitions correctly and partioned my disk in this fashion:

isw_bighgecdc_Volume0p1 - MSI recovery partition
isw_bighgecdc_Volume0p2 - Windows Boot partition
isw_bighgecdc_Volume0p3 - Windows System partition
isw_bighgecdc_Volume0p4 - Extended partition
isw_bighgecdc_Volume0p5 - Another NTFS partition
isw_bighgecdc_Volume0p6 - Swap
isw_bighgecdc_Volume0p7 - Ubuntu EXT4 partition (Ubuntu was installed here)

The problem is that even though Ubuntu installed just fine it cannot boot. Grub is able to load the kernel but it drops to a busybox shell with a warning that it cannot find the root partition (it looks for the disk's UUID).

On the busybox shell I can see the physical disks (sda and sdb) on /dev but I can't see anything on /dev/mapper, so I suppose it isn't loading the modules needed to populate the disks.

I did manage to install Ubuntu on an external USB disk and it boots just fine from there and I'm able to read all partitions. Windows also boots fine even from the local grub.

Anyone knows how can I make the kernel "see" the fakeraid on startup? Thanks!

---

### Post by [S|G] on 2011-10-07
Adding some more information: I've checked my running modules after booting from the USB disk and I've added the dm_raid45 module to the notebook's initramfs, but the system still does not boot.

From the system running from the USB, I can see this:

# dmsetup status
isw_bighgecdc_Volume0p7: 0 99174400 linear 
isw_bighgecdc_Volume0p6: 0 4194304 linear 
isw_bighgecdc_Volume0p5: 0 1619709952 linear 
isw_bighgecdc_Volume0p3: 0 209715200 linear 
isw_bighgecdc_Volume0p2: 0 204800 linear 
isw_bighgecdc_Volume0: 0 1953536512 striped 2 8:0 8:16 1 AA
isw_bighgecdc_Volume0p1: 0 20518912 linear

However when I run dmsetup from the busybox prompt after the failed boot attempt it says that there are no volumes configured.

---

### Post by [S|G] on 2011-10-07
I managed to find a solution :) Here's what I did after booting from the external disk's Ubuntu, in case it helps anyone:

1 - Mount the laptop's disk in /media/ubuntu (can be done by just opening the disk in nautilus)
2 - Open a terminal
3 - Prepare the system in the local disk for you to chroot into:
```

$ sudo mount --bind /sys /media/ubuntu/sys
$ sudo mount --bind /proc /media/ubuntu/proc
$ sudo mount --bind /dev /media/ubuntu/dev

```

4 - Chroot into the system:

```

$ sudo chroot /media/ubuntu

```

5 - Install the dmraid package:

```

# apt-get install dmraid

```

6 - Reboot from the local disk


It is possible that I didn't need to mess with the kernel modules like I did before. In any case it works like a charm now!

---

