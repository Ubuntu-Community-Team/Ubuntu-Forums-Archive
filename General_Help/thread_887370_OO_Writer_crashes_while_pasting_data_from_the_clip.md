---
title: "OO Writer crashes while pasting data from the clipboard"
date: 2008-08-12
forum: General Help
---

### Post by gibsorter on 2008-08-12
Hi @all,

I use OO 2.4.1 with Ubuntu 8.04. If I insert data (e.g. text with images) via paste through the clipboard in writer, the application crahes. The following output was created:
```
Fatal exception: Signal 11
Stack:
.
.
.
/usr/lib/openoffice/program/libucbhelper4gcc3.so(_ZN9ucbhelper7Content19openWriteableStreamEv+0x2e8)[0xb73e26d8]
/usr/lib/openoffice/program/libcomphelp4gcc3.so(_ZN10comphelper15MediaDescriptor14addInputStreamEv+0x2fb)[0xb74d6d2b]
.
.
.
```
Further tests revealed that writer crashes, if the data is at least as long as three pages and its source is in the internet. I'd saved a whole page offline and was able to insert all the data without crashing writer.

I'd found a few reports belonging to this error. The result is: actually, there is no solution for this problem except for:
1. Removing OO incl. ubuntu-desktop (!)
2. Load OO from oo.org and install it
3. Remember: before upgrading Ubuntu you'll have to reinstall the meta packet and the version of OO that comes along with Ubuntu :(

Does anyone know a better solution?

Cheers

---

### Post by Z47isthenew42 on 2008-10-07
> **gibsorter said:**
> Hi @all,

I use OO 2.4.1 with Ubuntu 8.04. If I insert data (e.g. text with images) via paste through the clipboard in writer, the application crahes. The following output was created:
```
Fatal exception: Signal 11
Stack:
.
.
.
/usr/lib/openoffice/program/libucbhelper4gcc3.so(_ZN9ucbhelper7Content19openWriteableStreamEv+0x2e8)[0xb73e26d8]
/usr/lib/openoffice/program/libcomphelp4gcc3.so(_ZN10comphelper15MediaDescriptor14addInputStreamEv+0x2fb)[0xb74d6d2b]
.
.
.
```
Further tests revealed that writer crashes, if the data is at least as long as three pages and its source is in the internet. I'd saved a whole page offline and was able to insert all the data without crashing writer.

I'd found a few reports belonging to this error. The result is: actually, there is no solution for this problem except for:
1. Removing OO incl. ubuntu-desktop (!)
2. Load OO from oo.org and install it
3. Remember: before upgrading Ubuntu you'll have to reinstall the meta packet and the version of OO that comes along with Ubuntu :(

Does anyone know a better solution?

Cheers

I've been having the same problem, and hope there's a better solution than the one you found.

---

