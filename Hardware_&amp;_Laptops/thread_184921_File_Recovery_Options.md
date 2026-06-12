---
title: "File Recovery Options?"
date: 2006-05-30
forum: Hardware &amp; Laptops
---

### Post by wr0x2 on 2006-05-30
I might be attempting to recover data from a memory stick that has been formatted. The FS would presumably be fat32. What utilities (preferably free) exist that I can use for this in linux?

---

### Post by az on 2006-05-30
[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

The version in the repos is too old.  Install build-essential and compile this.

you can make an image of your usb drive:

dd if=/dev/sda1 of=file
and then
foremost -o recovered -i file

---

### Post by wr0x2 on 2006-05-31
Thanks, I'll give it a shot.

---

