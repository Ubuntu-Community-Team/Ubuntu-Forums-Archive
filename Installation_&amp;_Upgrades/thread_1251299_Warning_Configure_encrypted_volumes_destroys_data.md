---
title: "Warning: Configure encrypted volumes destroys data"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by chmac on 2009-08-27
If you're using the alternate installer to install an encrypted system, and you already have encrypted data on the disk, be very, very careful.

I was upgrading from 8.10 32-bit to 9.04 64-bit, so I fired up the alternate installer, configured my partition for use as a physical volume for encryption, clicked "configure encrypted volumes", entered a passphrase twice, then bingo, my entire encrypted disk was destroyed.

The installer asked "Are you happy with your partition layout", which I was. It wasn't clear that it was now going to create a newly encrypted partition, destroying any data on the existing partition.

Relevant links:
[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/420080](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/420080)
[http://ubuntuforums.org/showthread.php?t=1229776](http://ubuntuforums.org/showthread.php?t=1229776)

---

