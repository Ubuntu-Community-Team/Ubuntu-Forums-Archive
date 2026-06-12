---
title: "xsupplicant -lcrypto problem"
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by Dukeman330 on 2005-07-15
I'm trying to configure the latest xsupplicant version (1.2pre1), since the current synaptic package doesn't seem to be working for me.  When I try to configure the source, I get this message:

checking for CRYPTO_new_ex_data in -lcrypto... no
configure: error: library 'crypto' is required for Open1x

Does anyone know how to get around this problem?  I've installed the latest openssl, and I tried to install the "libcrypto++" package as well, yet I don't have any "lcrypto" library on my system.  Any idea where I could find this?  Better yet, could someone post a package of 1.2pre1?  Thanks.

~Dukeman

---

### Post by sshataka on 2005-07-18
Found a forum entry that may help...  In a nutshell, install libssl-dev 0.9.7.

[http://ubuntuforums.org/showthread.php?t=28071&highlight=xsupplicant](http://ubuntuforums.org/showthread.php?t=28071&highlight=xsupplicant)

---

