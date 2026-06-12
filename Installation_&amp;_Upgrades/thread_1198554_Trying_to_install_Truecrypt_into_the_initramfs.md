---
title: "Trying to install Truecrypt into the initramfs"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by u-slayer on 2009-06-27
I'm trying to set up a crypto system that involves a combination of truecrypt and LUKS in the initrd image. I added truecrypt and all its libraries to the initrd image. Now when I try to mount a file from the (initramfs) prompt:

```

truecrypt --mount-options=nokernelcrypto /mnt/usb/test /mnt/test
Error: mount: mounting /dev/loop1 on /mnt/test failed: Invalid argument.

```

Of course I can't get it to tell which argument that might be. I don't think it's a kernel module issue because I'm using the nokernelcrypto option for truecrypt. I've notice some of the binaries in the initramfs behave differently. For example: mount -U doesn't work, you have to use mount /dev/disk/by-uuid/... instead. Has any tried this and gotten truecrypt to work in the initrd?

---

### Post by u-slayer on 2009-06-27
bump

---

