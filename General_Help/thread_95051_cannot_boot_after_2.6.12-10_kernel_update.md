---
title: "cannot boot after 2.6.12-10 kernel update"
date: 2005-11-25
forum: General Help
---

### Post by ajaustin on 2005-11-25
This problem has occurred immediately after applying the latest kernel upgrades.

```

mdadm: /dev/md0 has been started with 2 drives
mdadm: /dev/md1 has been started with 2 drives
mdadm: /dev/md2 has been started with 2 drives

mount: Mounting /dev/hda3 on /root failed. Device or resource busy.
mount: Mounting /root/dev/ on /dev/.static/dev failed. No such file or directory.
mount: Mounting /dev on /root/dev failed. No such file or directory.
Target filesystem doesn't have /sbin/init.
```

I am using mirrored disks (md0 = boot, md1 = swap, md2 = /).  If I boot with the Ubuntu LiveCD I can mount as either /dev/hda3 or /dev/md2 and everything looks fine and I can see the filesystem, including /sbin/init.

There are some links in the root directory that must have been put there by the kernel upgrade:-

```
initrd.img >- boot/initrd.img-2.6.23.-10-386
initrd.img.old >- boot/initrd.img-2.6.23.-9-386

vmlinuz >- boot/vmlinuz-2.6.23.-10-386
vmlinuz.old >- boot/vmlinuz-2.6.23.-9-386
```

I have renamed the links so that the -10- kernel is now .old and the initrd.img and vmlinuz point to the -9- kernel and then booting from the -9- kernel (which worked fine up to now), but this has not helped.  Booting with either kernel gives the same problem.

If I try to mount /dev/hda3 from the prompt in recovery mode I get:-

```
#mount /dev/hda3 /mnt
mount: /proc/filesystems: No such file or directory
```

My guess is that it is something to do with the kernel upgrade caused the problem and that the "Device or resource busy" is the beginning of it, but I don't know what to do now.

Tony

---

### Post by ajaustin on 2005-11-25
I have figured out what has caused this now.

The update had changed all references to root=/dev/md2 to root=/dev/hda3 in my /boot/grub/menu.lst file!

I've changed them back and all is well now.

Tony

---

