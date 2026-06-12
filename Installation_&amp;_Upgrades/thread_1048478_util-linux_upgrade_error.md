---
title: "util-linux upgrade error"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by indifferent51 on 2009-01-23
I cannot upgrade any packages on my 2.6.24-22-generic system because the util-linux package keeps error-ing out.  Here is the error:

E: /var/cache/apt/archives/util-linux_2.13.1-5ubuntu3_amd64.deb: subprocess new pre-removal script returned error exit status 9

Any ideas?  I already tred searching for answers and nothing worked so far.

Please help!

---

### Post by Partyboi2 on 2009-01-24
Can you please open a terminal (Applications>Accessories>Terminal) and post the whole output to
```
sudo apt-get upgrade
```This should reveal a bit more info on the error message

---

