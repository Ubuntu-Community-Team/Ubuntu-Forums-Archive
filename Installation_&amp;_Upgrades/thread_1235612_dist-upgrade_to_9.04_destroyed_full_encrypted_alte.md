---
title: "dist-upgrade to 9.04 destroyed full encrypted alternate installation"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by ste][nke on 2009-08-09
Hello to the Ubuntu Community!  A long time ago I installed Ubuntu 8.10 i386 alternate on my notebook. I used the full encryption, root and swap controlled by LVM and encrypted using LUKS with one passphrase.   After I did a dist-upgrade by Ubuntu's update manager to 9.04 the boot up process stopped shortly before it asked for the passphrase (before). It dropped to the shell informing about a disk not being available by its uuid. I've corrected the entries in the initrd to absolute paths (/dev/sda1) instead of uuid.  Now the kernel asks for the passphrase again. But the passphrase is not accepted though I entered it correctly.  I tried to decrypt the partitions with several live-cds and different kernel versions. Even under Ubuntu 8.10 alternate the decryption did not succeed.  cryptsetup luksDump reports an existing header with one key. This seems to be ok, but the thing I noticed is that the encrypted partition shows up as a swap partition in gparted.   It would be great if someone could help me.  Thanks in advance

---

