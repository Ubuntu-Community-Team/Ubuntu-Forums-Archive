---
title: "Mounted samba filesystems not working after resume"
date: 2006-04-06
forum: Hardware &amp; Laptops
---

### Post by saurabhnanda on 2006-04-06
Hi,

I usually mount two samba filesystems using a custom init.d script after my laptop has booted. After I resume from a hibernate, both the filesystems stop working. The smbmount processes associated with each filesystem still appear in the process list, but doing any operation with those filesystems results in an Input/output error.

How can I fix this problem?

I'm on Ubuntu Breezy Badger 5.10 with a 2.6.12-10-386 kernel (with a fixed DSDT). My laptop is an Acer 4061NWLCi.

---

### Post by mccyron on 2006-04-06
How do you mount a samba file system in Ubuntu?

mount -t smbfs //user@Server/share /mount-pt

...doesn't work here as it does in other Linux/Unix.

---

