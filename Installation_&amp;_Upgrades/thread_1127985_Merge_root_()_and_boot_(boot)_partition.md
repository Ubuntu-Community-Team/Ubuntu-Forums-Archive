---
title: "Merge root (/) and boot (/boot) partition"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by thehkv on 2009-04-17
Hello everyone.
I just installed jaunty beta, but it wouldn't boot unless I gave it a separate boot partition. Later I figured it was maybe because my root partition was a logical one.(?)

Trying merge boot partition in root myself, I flagged my root partition as bootable and did the normal grub>root (hd0,5)>setup(hd0) and succeeded. But while booting, grub still says "booting from hd0,1" (which is sda2 i guess?) so my method didn't really work did it ?

here's relevant "fdisk -l" and "df -h" information

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             378        2988    20972857+   7  HPFS/NTFS
/dev/sda2               1           6       48163+  83  Linux
/dev/sda3            2989       30384   220058370    5  Extended
/dev/sda4               7         377     2980057+  82  Linux swap
/dev/sda5            4294       30384   209575926    7  HPFS/NTFS
/dev/sda6   *        2989        4293    10482349+  83  Linux

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              21G   16G  4.6G  78% /windows
/dev/sda2              46M   18M   26M  41% /boot
/dev/sda5             200G  195G  5.5G  98% /data
/dev/sda6             9.9G  3.5G  5.9G  38% /
```

I'm now afraid to remove sda2 or my system may not boot at all.
How can I safely remove it (by merging it in root) ?

---

### Post by ronparent on 2009-04-17
I believe that you probably need the separate boot partition because of the position of the linux install. You then need to restore the boot from the grub partition - ie sudo grub > root (hd0,1) > setup (hd0). At that point it should boot if sda6 is properly identified in the /boot partition menu.lst by uuid.

---

