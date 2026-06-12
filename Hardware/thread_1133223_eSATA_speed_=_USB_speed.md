---
title: "eSATA speed = USB speed"
date: 2009-04-22
forum: Hardware
---

### Post by Dave In Sidney on 2009-04-22
I just added an ACOMData 1TB external drive to the system as a backup device. As the server's MB (MSI K7N2 Delta-L) doesn't natively support eSATA, I use an ST-Lab PCI:eSATA card that also drives an internal SATA drive (there's also an internal IDE drive in the case).

I ran 2 tests backing up the same file structure with rsync - first via USB 2.0 and then via eSATA - and both generated roughly the same speeds (2.3 MBytes/sec) from a very lightly used Hardy Heron server.

The backups are mainly JPGs and OGGs so I don't expect compression is required.

Any thoughts as to how to get the value that eSATA promises?

TIA,
Dave

---

### Post by Dave In Sidney on 2009-05-02
Resolved. After writing this I realized I was using compression in rsync.

---

