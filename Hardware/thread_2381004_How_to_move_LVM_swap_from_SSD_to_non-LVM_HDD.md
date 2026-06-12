---
title: "How to move LVM swap from SSD to non-LVM HDD"
date: 2017-12-25
forum: Hardware
---

### Post by accounts0 on 2017-12-25
When I installed Ubuntu server to my SSD it automatically added ~16GB swap to the LVM layout, which for my tiny SSD is a considerable amount.

I'd like to remove the swap volume, extend the root volume into that space, & put swap on the HDD.

I can see in gparted that it's easy enough to shrink the HDD partition & add a swap partition to the end of that drive afterward. But I'm not so certain about the LVM operations. When I google I see there's some concern about grub, which I didn't expect to be necessary to deal with.

Is it as simple as this?
```

swapoff -a

lvremove /dev/Hostname-vg/swap_1

lvextend -r -l+100%FREE /dev/Hostname-vg/root
```

...And then just changing /etc/fstab to:
```

/dev/Hostname-vg/swap_1 none            swap    sw              0       0

```

Google brought this [0] tutorial to my attention, & I'm not following what it says about changes to make to grub. Could anyone advise on all this?

-Thanks




[0]
[http://creativeandcritical.net/help-articles/how-to-safely-delete-swap-volume-extend-root-volume-fedora-20](http://creativeandcritical.net/help-articles/how-to-safely-delete-swap-volume-extend-root-volume-fedora-20)

---

### Post by TheFu on 2017-12-28
gparted doesn't handle LVM anything.
16G for swap seems huge.  Generally, anything more than 4G is overkill and for a desktop 4G is the minimum swap regardless of actual RAM because bloated browsers need it.  The purpose of swap is to make a system "feel" slower when all the real RAM is used, to let the system users know they are getting into constrained RAM situations.

There are 2 exceptions for having huge swap sizes - 
a) you use hibernation (I never do over security issues)
b) you run a VPS and don't like your customers much

I always have to check the lvextend manpage to see the usage.  You can do that as easily as I.
If you aren't using LVM for the new swap, then you'll need to create the partition (/dev/sdM5 or something), then mkswap on it, then add that into the /etc/fstab as a swap partition. Do not use an LV or VG for the reference if you aren't using LVs for the swap.

For more specific instructions, post some **lsblk** output in code tags.

---

### Post by accounts0 on 2018-01-17
So the instructions here [1] worked flawlessly to remove the current LVM-based swap from the SSD. A few extra things I had to do:

-Simple 'lvdisplay' to find what to call the lvms in the tutorial for my specific case
-GRUB didn't have to change- ignored those steps no problem
-Resized HDD partition & created a swap partition in the reclaimed space using a LiveCD- in my case a Kubuntu 17.x booted UEFI just fine
-vol_id command not found had to use blkid to find new swap partition UUID for fstab; just copied the original line with the new UUID for the new swap partition



[1]
[http://creativeandcritical.net/help-articles/how-to-safely-delete-swap-volume-extend-root-volume-fedora-20](http://creativeandcritical.net/help-articles/how-to-safely-delete-swap-volume-extend-root-volume-fedora-20)

---

