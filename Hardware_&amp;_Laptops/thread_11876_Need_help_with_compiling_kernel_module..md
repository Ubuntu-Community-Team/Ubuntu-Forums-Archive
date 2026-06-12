---
title: "Need help with compiling kernel module."
date: 2005-01-20
forum: Hardware &amp; Laptops
---

### Post by zoarre on 2005-01-20
I've got a Netgear MA101 USB adapter that I would like to get functioning in Ubuntu. So far, I've fone the following:

```
1. sudo apt-get install at76c503a-sources
2. cd /usr/src
3. sudo tar -zxvf at76c503a.tar.gz
4. cd modules/at76c503a
5. sudo make
6. sudo make install
```
This doesn't see to have done anything, other than compile the module. My device isn't detected.

The uninstall script appears to expect a directory named *at76c503a* in */lib/modules/$(ARCH)/kernel/net/wireless*, but I don't see anything like that there.

I'm at a loss. Would anyone be kind enough to point out what I'm doing wrong? Thanks in advance.

---

### Post by mpie on 2005-01-20
TRY make && make modules && make install!!! :?:

---

