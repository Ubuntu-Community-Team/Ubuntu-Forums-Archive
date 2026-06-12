---
title: "Home folder partition showing up in Places Bar"
date: 2008-11-18
forum: General Help
---

### Post by hardran3 on 2008-11-18
I am running Hardy on an Acer Aspire One. 8GB Internal flash for /, and a 16GB SDHC for /home. Everything is working great, except for the partition on the SDHC still shows up in the Places bar, and it is unmountable, obviously because it is already mounted

here is its fstab entry

```
UUID=uuid /home  ext2  noatime,nodiratime,errors=remount-ro  0  2
```

Is there anyway to make it disappear from the Places bar?

---

### Post by geirha on 2008-11-18
Filesystems on external drives will always show up in places unless you mount it in /mnt. I don't know where this is configured, but that would be the best fix, to add /home as such a special mount point prefix. 

You can mount that partition as /mnt/home instead, and then use mount binding to also mount it at /home. I think that should make it disappear from places as well.

```
UUID=uuid /mnt/home  ext2  noatime,nodiratime,errors=remount-ro  0  2
/mnt/home /home ext2 bind 0 0
```

Not the best solution, but since there wasn't any other replies yet ...

---

### Post by hardran3 on 2008-11-19
This did not work, but thanks for trying! 

It is strange because it should not be showing up at all, as the drive is not mounted in /media, it is mounted as /home.

It was working correctly before. The SD card that holds my /home was corrupted, so I had to reformat the card and remake my user. Only after this it started showing up in nautilus. It shows as an unmounted drive, which it is not, and if I try to mount it nautilus gives me an error saying "The drive is already mounted or busy." Nothing shows in my logs when I try this either.

---

