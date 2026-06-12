---
title: "Cannot mout drives using NTFS-3g"
date: 2008-10-08
forum: Hardware
---

### Post by saquib on 2008-10-08
I cant mount using NTFS-3g anymore! I'm getting the following message:
Mount is denied because setuid and setgid root ntfs-3g is insecure with the
external FUSE library.

I can mount my external FAT drives, but unable to mount any NTFS drives! please help!

---

### Post by Yellow Pasque on 2008-10-08
See this: [http://ubuntuforums.org/showthread.php?p=5173521#post5173521](http://ubuntuforums.org/showthread.php?p=5173521#post5173521)

The half-@$$ed workaround is to remove the entry for the NTFS partition from /etc/fstab. The correct workaround would be to remove Ubuntu's ntfs-3g package and nuild ntfs-3g from source and making sure it doesn't configure with "--with-fuse=external"

---

