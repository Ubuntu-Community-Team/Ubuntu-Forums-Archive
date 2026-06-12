---
title: "Kernel oops when inserting pcmcia cf reader"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by qrdl on 2007-05-02
Hello!

I have Acer Aspire 5101 AWLMi with single core AMD Turion64 CPU with Ubuntu 7.04 amd64 installed. When inserting PCMCIA CompactFlash card reader I get the dmesg output listed in attached file. I think this bug is Ubuntu-specific because nothing similar happened in Debian Etch and openSUSE 10.2 (both have 2.6.18 kernels). Currently I have 2.6.20-15 kernel installed.

Any ideas?

PS. I've posted a bug report about this bug [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/111690](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/111690)

---

### Post by qrdl on 2007-05-02
So...

Any help is welcome

---

### Post by qrdl on 2007-05-02
Up...

---

### Post by qrdl on 2007-05-03
Unfortunately there is now quick solution. The pata_pcmcia is broken in current ubuntu's kernel (and upstream), so anyone having the same issue should wait for next release :(

---

