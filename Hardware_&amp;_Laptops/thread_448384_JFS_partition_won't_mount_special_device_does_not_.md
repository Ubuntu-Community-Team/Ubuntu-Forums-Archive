---
title: "JFS partition won't mount: special device does not exist"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by fxer on 2007-05-19
I just did a clean install of Feisty, and for 1 of my hard drives I ran the command "mkfs.jfs /dev/sdb" and it seems to have worked, GParted shows /dev/sdb1 to be the full size of the drive and JFS formatted.

However when I tried "sudo mount -t jfs /dev/sdb1 /myth" I got an error about incorrect filetype, so I rebooted. Now when I type the command, I get the error "mount: special device /dev/sdb1 does not exist"

Anyone know what's going on?

---

### Post by fxer on 2007-05-19
Perhaps it doesn't matter, but the drives that used to be /dev/hda and /dev/hdb in edgy are now /dev/sda and /dev/sdb in this fresh install of feisty, both are IDE drives

---

