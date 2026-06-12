---
title: "ls I/O Error in one folder on usb hdd"
date: 2017-11-28
forum: Hardware
---

### Post by zeitalex on 2017-11-28
one folder on usb hdd is suddenly appears empty. ls in this folder shows only message: Input Output Error
and in /var/log/syslog i get:
```
ntfs-3g[3494]: ntfs_mst_post_read_fixup_warn: magic: 0xfa810756  size: 4096   usa_ofs: 1890  usa_count: 64638: Das Argument ist ungültig
ntfs-3g[3494]: Actual VCN (0x298082501780805) of index buffer is different from expected VCN (0x0) in inode 0x419.
```
any help would be highly appreciated
Alex

---

