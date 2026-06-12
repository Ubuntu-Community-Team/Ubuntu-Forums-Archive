---
title: "Two drives SATA &amp; IDE"
date: 2005-02-10
forum: Hardware &amp; Laptops
---

### Post by fatman on 2005-02-10
Been runnig Hoary on my soon-to-be HTPC machine off a SATA HDD.  (AMD64)
Took the old ATA drive out of my old machine to use in the HTPC as more storage.
SATA HDD is on the SATA bus, ATA HDD is on the secondary IDE bus (due to case geometry).  Ubuntu refuses to mount the ATA HDD (but the Knoppix LiveCD mounts it)

"sudo -t ext2 mount /dev/hdc8 /mnt/olddrive"  returns:  "mount: /dev/hdc8 already mounted or /mnt/olddrive busy"

but when I try "umount /dev/hdc8" , I get "umount: /dev/hdc8: not mounted"
and when I try "fuser /mnt/olddrive" I get nothing.

It appears to be able to read from the ATA HDD, as
"strings /dev/hdc8 | head" gives
```

ZAD@B
lost+found
matt
warrior
vTLEN
248659TCON
CountryTPE1
Travis TrittTIT2
Best Of Intentions
2>jCI

```

Any suggestions?

---

