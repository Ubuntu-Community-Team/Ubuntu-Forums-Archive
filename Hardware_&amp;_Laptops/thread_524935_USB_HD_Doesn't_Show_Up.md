---
title: "USB HD Doesn't Show Up"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by rmcgibbo on 2007-08-13
I just got a 120GB WD Passport external USB HD for backing up my mac. I cloned the mac HD onto the drive, so its formatted as HFS+ (Journaled). I just plugged it into my Ubuntu box to transfer some files and... Big fat nothing. The drive's LED lights up, but Ubuntu doesn't respond at all. I plugged in my Flash USB stick, and that automatically mounts perfectly, but the OS seems to not realize that the portable HD is there. Anyone got any advice?

---

### Post by rmcgibbo on 2007-08-14
Anyone?

---

### Post by K.Mandla on 2007-08-14
When you plug in the drive, does it show up in the list given by this command?

```
sudo fdisk -l
```

---

### Post by rmcgibbo on 2007-08-14
I can physically feel that when first plugged into the Ubuntu Box, the drive spins and then stops, then spins and then stops, repeat.

No Show in fdisk:
robert@robert-desktop:~$ sudo fdisk -l

Disk /dev/hda: 15.0 GB, 15020457984 bytes
255 heads, 63 sectors/track, 1826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1744    14008648+  83  Linux
/dev/hda2            1745        1826      658665    f  W95 Ext'd (LBA)
/dev/hda5            1745        1826      658633+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         830     6666943+   7  HPFS/NTFS
/dev/hdb2             831        9729    71481217+   f  W95 Ext'd (LBA)
/dev/hdb5             831        2785    15703506    7  HPFS/NTFS
/dev/hdb6            2786        9729    55777648+   7  HPFS/NTFS

---

### Post by barisy on 2007-08-14
Yeah i tried that one too but i think we have something different like USB ports are closed or drivers are not installed ..

---

### Post by K.Mandla on 2007-08-14
Does your external have a pair of USB plugs, one for data and one for extra power?

I ask because I used to run a laptop hard drive in an enclosure, and some early USB ports don't supply enough power to bring the drive up to speed. The result was spin-stop-spin-stop-spin-stop for as long as I left it plugged in.

If you have an external with a pair of USB plugs, you might need to plug both in. This is a rather obscure issue and probably not what you're seeing, but I thought I'd mention it.

---

### Post by kekoav on 2007-12-19
I have same issue, I have a WD Passport 160GB.  I do an lsusb and it does not list the drive.  But I found that it is probably an issue with EHCI(usb 2.0) because when I do a 
 rmmod ehci_hcd

And then plug in the drive it works fine.  But it is painstakingly USB 1.1 slow.  There has got to be either an issue with the drive's USB 2.0 implementation, or the linux ehci kernel module, cause it works fine in windows...

Any ideas how to fix this and get the full usb 2.0 speeds?  It also isn't good to disable ehci because of course there are other usb devices which should enjoy usb 2.0 as well.

Thanks for your thoughts, I will probably return the drive soon if I can't get it to work right.

---

