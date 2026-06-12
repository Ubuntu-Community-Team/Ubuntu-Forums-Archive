---
title: "Software RAID 5 and Windows"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by dutch_gecko on 2007-11-02
I will shortly be aquiring two drives which are identical to a pair I already own, and want to stuff them together as a RAID 5. At the moment my drives are running on a FakeRaid 0, and using dmraid means that I can access the data in both windows and linux (yes, I'm still tied to M$).

I don't plan on splashing out on a raid controller to add these drives, which means that I now have to figure out a way of getting them to work on a software raid setup. This in itself is fine - I'm not particularly worried about CPU usage or the like, but I need the array to be accessible to both OSes.

Sadly, I haven't found much info on getting a software raid to work across platforms. I know that in linux I can use mdadm to create my array, and I know that in windows I can apply some registry h@x to get access to its raid software, but how can I get one to work in the other?

I don't mind some overhead, but running a virtual machine is IMO taking it a bit far so I'd like to avoid that if possible. Has anyone done something like this before?

---

### Post by fowie on 2007-12-18
I'd be interested in knowing the same thing.  Have you found any solutions?  I would be ok with Raid-0 even, just something I could use in both windows and linux.  I've set up my two data drives as RAID0 in Vista and I can see the drives in linux but they're SFS not NTFS, so even though I can create a raid0 array using mdadm with them, the /dev/md0 that is created is still an SFS and it won't mount (even with -t ntfs).  I have found a few posts that say you can use dmraid if it's a particular fakeraid (such as nvidia's fakeraid) (post #230334 for example).  Anyone figured this out with windows native software RAID?

---

### Post by dutch_gecko on 2007-12-19
Hey Fowie

I did some more hunting around after this post and found only two solutions.

One involved running a very lightweight linux distro as a virtual machine under windows, and using samba to share data between the two - cumbersome, but it works.

The other solution is to grab a cheap disk controller and use the controller's drivers in windows, and dmraid (for fakeraid) in ubuntu.

Check your motherboard manual to make sure it isn't fitted with some kind of "hardware" raid capability, since using Raid 0 over dmraid is thankfully very easy. Otherwise I'm afraid you're probably out of luck.

I personally decided to give up on windows - I've almost managed it :)

---

### Post by fowie on 2007-12-22
Thanks for the reply, the motherboard's got hardware to do a fake raid 0 which is all I really want, but dmraid doesn't seem to pick that up.  My current solution has been to recompile the kernel with the IDE 821x driver installed instead of the it821x sata/pata driver.  Now I can see the drives but even though I can use mkfs and fdisk on them, I can't mount them, all I get is:
```

 sudo mount -t vfat /dev/hda1 /Striped/
mount: special device /dev/hda1 does not exist

```
even though fdisk shows
```

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b151b14

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3037    24393678+   7  HPFS/NTFS
/dev/sda2            3038        4756    13807867+  83  Linux
/dev/sda3            4757        4865      875542+   5  Extended
/dev/sda5            4757        4865      875511   82  Linux swap / Solaris

Disk /dev/hda: 160.0 GB, 160052674560 bytes
255 heads, 63 sectors/track, 19458 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007997c

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       19458   156296353+   b  W95 FAT32

```

---

