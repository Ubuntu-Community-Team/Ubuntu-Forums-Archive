---
title: "Cannot install any packages"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by Eric B on 2009-04-10
I can an error whenever I try to update, I get errors.

I also cannot run my most recent kernel.

I tried this that I found posted somewhere else.

```
mylaptop:~$ sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.broke
[sudo] password for XXXX: 
mylaptop:~$ 
mylaptop:~$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
mylaptop:~$ sudo dpkg --configure -a
Setting up linux-image-2.6.24-24-generic (2.6.24-24.51) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-24-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-24-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-24-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-24-generic; however:
  Package linux-image-2.6.24-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.24.26); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-24-generic:
 linux-ubuntu-modules-2.6.24-24-generic depends on linux-image-2.6.24-24-generic; however:
  Package linux-image-2.6.24-24-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-24-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-24-generic:
 linux-restricted-modules-2.6.24-24-generic depends on linux-image-2.6.24-24-generic; however:
  Package linux-image-2.6.24-24-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-24-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-24-generic; however:
  Package linux-restricted-modules-2.6.24-24-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-24-generic
 linux-image-generic
 linux-generic
 linux-ubuntu-modules-2.6.24-24-generic
 linux-restricted-modules-2.6.24-24-generic
 linux-restricted-modules-generic

```

Any ideas?

Thank you.

---

### Post by coffeecat on 2009-04-10
> **Eric B said:**
> Any ideas?

Yes. This is your problem:


> **Eric B said:**
> ```
Setting up linux-image-2.6.24-24-generic (2.6.24-24.51) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-24-generic

gzip: stdout: No space left on device
```

You've run out of space wherever your /boot contents are kept. It hasn't got room for the initrd.img image, so none of the 2.6.24-24 kernel is being installed. Do you have a separate boot partition, or do you keep /boot in your root partition?

---

### Post by Eric B on 2009-04-10
Ha. I just noticed that as well. Don't I feel dumb.

Thanks.

Oh, and yes, I keep a separate boot partition. I cleaned some old images.

---

