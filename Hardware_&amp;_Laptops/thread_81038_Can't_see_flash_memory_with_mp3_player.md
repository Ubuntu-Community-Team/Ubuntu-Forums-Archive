---
title: "Can't see flash memory with mp3 player"
date: 2005-10-23
forum: Hardware &amp; Laptops
---

### Post by calvinpriest on 2005-10-23
I have a Rio Forge mp3 player, and I can access the internal memory (64mb) but not the memory that belongs to the flash card.

I found the following page which describes *exactly* what's happening, only it's for Fedora:
[http://www.linuxquestions.org/questi...05/02/3/286931](http://www.linuxquestions.org/questi...05/02/3/286931)

It recommends adding "options scsi_mod max_scsi_luns=15" to /etc/modules.conf. Things are different in Ubuntu, so I tried creating a new file in /etc/modprobe.d and pasting this into it. No luck unfortunately.

It appears that what's happening isn't specific to my device, it could be happening to any scsi device that has more than one partition.

The part that successfully mounts is /dev/sda1. The part that doesn't is /dev/sdb1. An entry shows up under "Computer" but when I try to double click it it gives: "Error: given UDI is not a mountable volume".

Anyone have any ideas?

---

### Post by Jenda on 2005-10-23
Warning: I'm not an expert!
But you might wanna try mounting it manually:
```
sudo mount /dev/sdb1 /whereever
```

Are you sure it's sdb1? A second partition should be sda2.

---

### Post by calvinpriest on 2005-10-23
Ok, so the whole flash/non-flash memory issue turned out to be a red herring.  It was a simple matter that there turned out to be a bunch of deleted files hidden on the player in a trash folder.  Once I deleted those I had plenty of space.  Doh!

---

