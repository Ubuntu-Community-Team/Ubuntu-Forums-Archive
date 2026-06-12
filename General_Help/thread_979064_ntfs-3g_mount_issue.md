---
title: "ntfs-3g mount issue"
date: 2008-11-11
forum: General Help
---

### Post by hso_eu on 2008-11-11
Hi

I'm on Ubuntu Intrepid and got a number of entries in my /etc/fstab to mount some ntfs volumes at boot.

i.e.
/dev/sdc2	/media/Backup ntfs-3g force 0 0

This has worked fine till today when I rebooted. The drives now don't mount.

I've tried:

'sudo mount -a' but get
ntfs-3g-mount: mount failed: Device or resource busy

I've also tried to mount individually using 'mount -t ntfs-3g ...' with the same result.


I am able to manually mount the volumes using evmsgui, so could this be a problem with ntfs-3g?

Any ideas anyone?

Thanks in advance.

---

### Post by taurus on 2008-11-11
It could be a problem with your ntfs partition.  Force mounting it every single time is not a good idea.  If it has windows on it, boot into windows and scan and defrag the partition.  Then, just mount it with ntfs-3g as a normal ntfs partition.

---

### Post by Yellow Pasque on 2008-11-11
Perhaps your motherboard has arbitrarily reassigned /dev/sd## links (this happens). Check:
```
sudo fdisk -l
sudo lshw -C disk -short
```
If this is the case, then mount by UUID/block ID.

---

