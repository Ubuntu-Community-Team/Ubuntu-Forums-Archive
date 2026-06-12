---
title: "boot failure- sbin/init missing? help"
date: 2005-11-12
forum: General Help
---

### Post by {{corona}} on 2005-11-12
hi i am running kubuntu breezy 5.10
after a crash of a number of applications under kde i did a soft reboot
and these errors came up
(these come up after selecting the rescue option that comes at boot startup- i think they are more detailed than ones that are come up when i do a normal start up on boot)
I copied them down from the screen and have retyped them..so if there are spell/typo mistakes, please excuse.
--------------------------
Begin: Running /scripts/local-premount
[4294675.50800] Attempting manual resume
[4294675.519000]swsusp: suspend partition has wrong signature?
Done.
[42944675.570000]EXT3-fs error (device hda9):ext3_check descriptors: Block bitmap for group 32 not in group (block 16877)!
[4294675.530000]EXT3-fs:group descriptors corrupted!
mount: Mounting /dev/hda9 on /root failed: invalid argument
Begin: Running /scripts/local-bottom...
Done.
Done.
Begin: Running /scripts/init-bottom...
Done.
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /dev on /root/dev failed: No such file or directory

Target filesystem doesn't have /sbin/init

BusyBox v1.00-preto (Debian 20040623-1ubuntu22) Built in shell (ash)
enter 'help' for a list of built in commands

/bin/sh: can't access tty; job control turned off
# " this is the prompt- this is where it stops"

-------------------------------

---

### Post by mlomker on 2005-11-14
I'd probably boot up on a Knoppix CD and run fsck against your drive.  If the drive is not corrupt then I'm not sure...

---

### Post by ajaustin on 2005-11-25
I have a very similar but different problem to corona's.  I don't get any indication of a hard disk failure and the problem has occurred immediately after applying the latest kernel upgrades.

I am using mirrored disks (md0 = boot, md1 = swap, md2 = /).  If I boot with the Ubuntu LiveCD I can mount as either /dev/hda3 or /dev/md2 and everything looks fine and I can see the filesystem, including sbin/init.

There are some links in the root directory that must have been put there by the kernel upgrade:-

```
initrd.img >- boot/initrd.img-2.6.23.-10-386
initrd.img.old >- boot/initrd.img-2.6.23.-9-386

vmlinuz >- boot/vmlinuz-2.6.23.-10-386
vmlinuz.old >- boot/vmlinuz-2.6.23.-9-386
```

I have renamed the links so that the -10- kernel is now .old and the initrd.img and vmlinuz point to the -9- kernel and then booting from the -9- kernel (which worked fine up to now), but this has not helped.  Booting with either kernel gives the same problem.

```

mdadm: /dev/md0 has been started with 2 drives
mdadm: /dev/md1 has been started with 2 drives
mdadm: /dev/md2 has been started with 2 drives

mount: Mounting /dev/hda3 on /root failed. Device or resource busy.
mount: Mounting /root/dev/ on /dev/.static/dev failed. No such file or directory.
mount: Mounting /dev on /root/dev failed. No such file or directory.
Target filesystem doesn't have /sbin/init.
```

Trying to mount from recovery mode gives:-
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

### Post by Tiede on 2006-01-18
I have the same problem, as in it complains about the target filesystem not having a /sbin/init
I looked at my menu.lst file and the old and new kernel both target /dev/hda5, which is  correct. Any other take on this issue?

---

