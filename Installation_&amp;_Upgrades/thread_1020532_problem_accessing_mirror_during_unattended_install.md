---
title: "problem accessing mirror during unattended install"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by Mia_tech on 2008-12-24
I'm doing an unattended install of ubuntu and after the client downloads the preseed.cfg file, it tries to access the mirror I set on the .cfg file and is giving me error > the specified ubuntu mirror is either not available or does not have a valid release file on it the mirror I'm using is us.archive.ubuntu.com......here's part of the preseed.cfg file containing the mirror settings

```
### Mirror settings
# If you select ftp, the mirror/country string does not need to be set.
d-i mirror/protocol string http
d-i mirror/country string manual
d-i mirror/http/hostname string us.archive.ubuntu.com
d-i mirror/http/directory string /ubuntu/dists/intrepid/
d-i mirror/http/proxy string
```

does anyone know why I'm getting that error?

thanks

---

