---
title: "Toshibe Satellite L505-13V ACPI problems"
date: 2010-10-02
forum: Hardware
---

### Post by NewbieLinuxer on 2010-10-02
Hi,
I have installed Ubuntu 10.04 LTS lucid on my new Toshiba L505-13V, I've experienced ACPI issues with installation (black screens and installation hanging etc.), but after searching i was able to boot and run Ubuntu without any booting issues with the "acpi=ht" fix in the grub.

However, Ubuntu isn't detecting my battery, FN keys are not working etc. which is really a bummer; so I searched for a while and it seems that the only way to do it is to compile a kernel due to bugs with the BIOS, and I have no idea how to compile a custom kernel.

This issue is really bugging me and quite a number of my friends who bought the same model.

Any suggestions/guides?

---

### Post by NewbieLinuxer on 2010-10-02
Bump

---

### Post by sirkeith on 2010-10-03
Here is another bump.

---

### Post by NewbieLinuxer on 2010-10-04
I managed to compile my own kernel with a patch provided in an excellent guide:
[http://au.ubuntuforums.org/showthread.php?t=1470732&page=2](http://au.ubuntuforums.org/showthread.php?t=1470732&page=2)

Tagging this thread as solved now :D

---

