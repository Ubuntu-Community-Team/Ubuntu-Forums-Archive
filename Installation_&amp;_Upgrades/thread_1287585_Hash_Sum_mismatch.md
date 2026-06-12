---
title: "Hash Sum mismatch"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by kilaka on 2009-10-10
Hi all,

I have a "Hash Sum mismatch" error for specific packages.

I think this is a bug but i'm not sure.

Other packages get updated and installed without any problem. The ones below give the following errors:

> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/i/icu/libicu38_3.8.1-3ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/i/icu/libicu38_3.8.1-3ubuntu1.1_i386.deb)
  Hash Sum mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_3.0.1-9ubuntu3.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_3.0.1-9ubuntu3.1_i386.deb)
  Hash Sum mismatch
Whats do you think ?
--Alik

---

### Post by Partyboi2 on 2009-10-11
Hi, have you tried changing your download server in Software Sources (System>Admin>Software Sources) to another one?

---

### Post by kilaka on 2009-10-12
> **Partyboi2 said:**
> Hi, have you tried changing your download server in Software Sources (System>Admin>Software Sources) to another one?

Works!!! I chose the US server and everything got updated without any problem.
Thanks.

BTW, why do the packages from the Main server have a "Hash Sum mismatch"?

---

