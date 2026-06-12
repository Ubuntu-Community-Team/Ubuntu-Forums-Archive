---
title: "USB Drive gets &quot;forgotten&quot;"
date: 2008-08-07
forum: General Help
---

### Post by KageKeeper on 2008-08-07
I have a 300 GB external hdd that is connected via USB.

On boot, it is detected with no problems and I can access it wonderfully.

Fairly often though, Hardy (or something) seems to forget about it and I lose the capability to access it. It does not show as being mounted and the only way I can fix the issue is to restart, which is a bit annoying.

Can anyone offer me any suggestions?

I am running Hardy Heron AMD64 version. Any other information needed I will supply.

Thanks so much.

---

### Post by drs305 on 2008-08-07
If desired, you could make an entry in fstab. By design, removable devices are not listed in fstab since the device name may change depending on what other devices are installed. For instance, it's possible a usb drive could be *sdd* on one boot but *sde* on another. One way around this is to make a label for the device or to use its uuid to identify it.

Placing the device in fstab is a solution and should work, again with the device should work normally through the Places menu or be mounted whenever it is accessed for the first time after boot.

To put it in fstab, determine it's uuid or make a label for it. To get the device's uuid, make sure it is plugged in and run:
```
sudo blkid
```

The command to make a label depends on the type of partitioning (ext2/3, ntfs, fat16/32, etc).

At this point, I will direct you to a tutorial I wrote about a gui-fstab editor. You don't have to use the app (pysdm) but all the information you should need is available on the page (labeling, fstab entries, etc). The link is in my signature line. 

If you have questions, come back here and post.

One final note: once it is listed correctly in fstab, if you find it still disappears, you can run the following. It will unmount all devices not being used (disregard the 'busy' messages) and remount them according to their fstab settings. 
```
sudo umount -a
sudo mount -a
```

---

