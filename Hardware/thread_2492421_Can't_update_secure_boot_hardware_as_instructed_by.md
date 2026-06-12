---
title: "Can't update secure boot hardware as instructed by Software Center"
date: 2023-11-10
forum: Hardware
---

### Post by ghoracek on 2023-11-10
Dell XPS 13 (originally came with Ubuntu 16.04 as factory install -- user updated over years to Ubuntu 23.10

My computer is  behind several generations in secure boot -- on 190 and current is 370
Running the updater fails with below error:

Blocked executable in the ESP, ensure grub and shim up to date: /media/root/OS/efi.factory/boot/bootx64.efi Authenticode checksum [47b31a1c7867644b2ee8093b2d5fbe21e21f77c1617a2c08812f57ace0850e9f] is present in dbxfix

should I be worried.  if so how do I fix this?  Google was no help.

---

### Post by Yellow Pasque on 2023-11-10
[https://bugs.launchpad.net/dell/+bug/1990179](https://bugs.launchpad.net/dell/+bug/1990179)

First, make sure the system's BIOS/EFI is up to date. If you continue to get the message after that, temporarily move the file in question out of the way so the update can go through.

---

