---
title: "cannot mount encrypted ISO after 8.10 upgrade"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by vaxman- on 2009-01-10
I used to mount (8.04) several encrypted ISOs with the following command:

```
$ sudo mount -t iso9660 ~/myenc.iso /mnt/iso -o loop=/dev/loop0,encryption=aes256

```
after upgrade to 8.10, I get:

```
ioctl: LOOP_SET_STATUS: Invalid argument, requested cipher or key length (256 bits) not supported by kernel
```


I can't believe that 256 bit encryption was removed.

What's up?

---

### Post by vaxman- on 2009-01-16
Nevermind.  cryptoloop and aes in my /etc/modules file were overwritten.  I put both bask in the modules file and I can now make and mount encrypted filesystems.

Difference files or change report would be welcome when upgrading.

---

