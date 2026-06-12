---
title: "mount NTFS"
date: 2005-12-04
forum: General Help
---

### Post by HokeyFry on 2005-12-04
how do you mount an NTFS filesystem? I want to mount it to a folder but when I type

"sudo mount /dev/hda3 /home/alex/temp"

it asks me to specify a filesystem type. I did "man mount" but i still dont understand how to do this.

---

### Post by aysiu on 2005-12-04
```
sudo mount -t ntfs /dev/hda3 /home/alex/temp
```

---

### Post by Ocxic on 2005-12-04
If you are able to mount the drive, yet unable to access it try

sudo mount /dev/hda3 /home/alex/temp  -t ntfs -o umask=0222

---

