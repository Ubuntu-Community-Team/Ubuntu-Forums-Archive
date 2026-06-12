---
title: "Quick help with Kernel update"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by pred2k on 2009-08-21
Hi, i want to update my Kernel (because the new vulnerability) on my rented dedicated server which is running with Ubuntu 8.10.

Current Kernel is a standard 2.6.24-23-generic

With apt-get upgrade i saw him downloading 2.6.27-14-generic

I'm not sure what to do, to use the new kernel. I already updated a kernel on my home-server with ubuntu, but i dont want to make mistakes at the update (because is a server from the hoster server4you.de).

after ```
apt-get upgrade
``` i did ```
update-grub
``` and got this message here:

> A new version of /boot/grub/menu.lst is available, but the version installed currently has been locally modified.
What would you like to do about menu.lst?
"Line by line differences between versions" shows this:
```

                           &#9474; --- /var/run/grub/menu.lst 2009-08-21 10:17:16.290525262 +0200                                         &#9474;
                           &#9474; +++ /tmp/file2lNYue 2009-08-21 10:17:16.000000000 +0200                                                &#9474;
                           &#9474; @@ -1,13 +1,33 @@                                                                                      &#9474;
                           &#9474;  ## ## End Default Options ##                                                                          &#9474;
                           &#9474;                                                                                                        &#9474;
                           &#9474; -title Ubuntu 8.04, kernel 2.6.24-23-generic                                                           &#9474;
                           &#9474; +title Ubuntu 8.10, kernel 2.6.27-14-generic                                                           &#9474;
                           &#9474;  root (hd0,0)                                                                                          &#9474;
                           &#9474; -kernel /vmlinuz-2.6.24-23-generic root=UUID=98c9b88d-2c73-4add-b588-53ac3308cb4f ro vga=ext           &#9474;
                           &#9474; +kernel /vmlinuz-2.6.27-14-generic root=UUID=98c9b88d-2c73-4add-b588-53ac3308cb4f ro acpi=ht vga=ext   &#9474;
                           &#9474; +initrd /initrd.img-2.6.27-14-generic                                                                  &#9474;
                           &#9474; +                                                                                                      &#9474;
                           &#9474; +title Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)                                           &#9474;
                           &#9474; +root (hd0,0)                                                                                          &#9474;
                           &#9474; +kernel /vmlinuz-2.6.27-14-generic root=UUID=98c9b88d-2c73-4add-b588-53ac3308cb4f ro acpi=ht single    &#9474;
                           &#9474; +initrd /initrd.img-2.6.27-14-generic                                                                  &#9474;
                           &#9474; +                                                                                                      &#9474;
                           &#9474; +title Ubuntu 8.10, kernel 2.6.27-11-generic                                                           &#9474;
                           &#9474; +root (hd0,0)                                                                                          &#9474;
                           &#9474; +kernel /vmlinuz-2.6.27-11-generic root=UUID=98c9b88d-2c73-4add-b588-53ac3308cb4f ro acpi=ht vga=ext   &#9474;
                           &#9474; +initrd /initrd.img-2.6.27-11-generic                                                                  &#9474;
                           &#9474; +                                                                                                      &#9474;
                           &#9474; +title Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)                                           &#9474;
                           &#9474; +root (hd0,0)                                                                                          &#9474;
                           &#9474; +kernel /vmlinuz-2.6.27-11-generic root=UUID=98c9b88d-2c73-4add-b588-53ac3308cb4f ro acpi=ht single    &#9474;
                           &#9474; +initrd /initrd.img-2.6.27-11-generic                                                                  &#9474;
                           &#9474; +                                                                                                      &#9474;
                           &#9474; +title Ubuntu 8.10, kernel 2.6.24-23-generic                                                           &#9474;
                           &#9474; +root (hd0,0)                                                                                          &#9474;
                           &#9474; +kernel /vmlinuz-2.6.24-23-generic root=UUID=98c9b88d-2c73-4add-b588-53ac3308cb4f ro acpi=ht vga=ext   &#9474;
                           &#9474;  initrd /initrd.img-2.6.24-23-generic                                                                  &#9474;
                           &#9474;                                                                                                        &#9474;
                           &#9474; -title Ubuntu 8.04, kernel 2.6.24-23-generic (recovery mode)                                           &#9474;
                           &#9474; +title Ubuntu 8.10, kernel 2.6.24-23-generic (recovery mode)                                           &#9474;
                           &#9474;  root (hd0,0)                                                                                          &#9474;
                           &#9474; -kernel /vmlinuz-2.6.24-23-generic root=UUID=98c9b88d-2c73-4add-b588-53ac3308cb4f ro single            &#9474;
                           &#9474; +kernel /vmlinuz-2.6.24-23-generic root=UUID=98c9b88d-2c73-4add-b588-53ac3308cb4f ro acpi=ht single    &#9474;
                           &#9474;  initrd /initrd.img-2.6.24-23-generic                                                                  &#9474;
                           &#9474;                                                                                                        &#9474;
                           &#9474;  ### END DEBIAN AUTOMAGIC KERNELS LIST
```

**Can i choose "install the package maintainer's version" ?**

I'm a little confused, when i login to the shell i always get this message:
> Dear customer,

Important information regarding kernel-updates:

If you want to use your own kernel, please make sure you don't touch the
kernel boot parameters (append) as some of our hardware requires the
parameters acpi=ht and/or noapic.

in this lines:
```
-kernel /vmlinuz-2.6.24-23-generic root=UUID=98c9b88d-2c73-4add-b588-53ac3308cb4f ro vga=ext
+kernel /vmlinuz-2.6.27-14-generic root=UUID=98c9b88d-2c73-4add-b588-53ac3308cb4f ro acpi=ht vga=ext
```

before there where just "ro vga=ext" as argument for the kernel.
Now "acpi=ht" was added.

The message from the hirer, says "acpi=ht" is required. But it wasn't configured before.

What other step do i have to do after update-grub?

---

### Post by pred2k on 2009-08-21
i choosed "install the package maintainer's version" and rebooted.
Everything is fine now.
Just where a little confused.

**SOLVED**

---

