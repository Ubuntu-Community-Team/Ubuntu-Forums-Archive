---
title: "How to turn off fsck of vfat drives on bootup?"
date: 2005-01-18
forum: Hardware &amp; Laptops
---

### Post by Shambler on 2005-01-18
I want to turn off the filesystem check of my two vfat drives on bootup (somehow the downloaded torrent files make fsck think that every unfinished download is a corrupt file...). But it don't know how to do that. Could anyone help?

---

### Post by hardcandy on 2005-01-19
I believe in the /etc/fstab file set the options as noted here:
[http://www.humbug.org.au/talks/fstab/fstab_options.html](http://www.humbug.org.au/talks/fstab/fstab_options.html)

"man mount" as well.

---

