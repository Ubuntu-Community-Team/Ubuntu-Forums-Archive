---
title: "Wget to write all files on a directory on a file instead of downloading?"
date: 2008-10-17
forum: General Help
---

### Post by Fixman on 2008-10-17
Is there any way to wget (or any other program) prints (or writes a file) all files in a directory (on HTTP, not FTP) without downloading them?

---

### Post by lakris61 on 2008-10-17
Hi!
Not sure what You mean, but You could explore the option --no-remove-listing:

> wget --no-remove-listing [ftp://my.ftphost.com](ftp://my.ftphost.com)
less .listing


/Lakris

Oops, sorry didn't see You explicitly said no ftp... :(

---

