---
title: "Persistent “ubuntu” UEFI boot without any drive attached"
date: 2014-05-08
forum: Hardware
---

### Post by DrJohn999 on 2014-05-08
Having some trouble installing Trusty on my Asus P8Z77-B LK motherboard with UEFI boot. Disconnected all the drives and cleared NVRAM  yet still see a choice of “ubuntu” UEFI boot in the BIOS configuration. Very strange — has anyone else seen something like this?

---

### Post by oldfred on 2014-05-08
What does this show?
 # from live CD booted in UEFI mode and use efibootmgr
sudo efibootmgr -v

---

### Post by DrJohn999 on 2014-05-08
Thanks, I was able to delete the vestigial boot entry and get back to a cleanly bootable system. Now back to achieving a clean install!

---

