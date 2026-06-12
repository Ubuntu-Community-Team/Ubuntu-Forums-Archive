---
title: "NVidia X Server Settings"
date: 2009-04-15
forum: Hardware
---

### Post by axlotxlikexvegas on 2009-04-15
Every time I boot up my settings aren't save so I have to set them every time I start up. When I try to save the settings I get "Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'". Can some one show me how to fix this?

---

### Post by SuperSonic4 on 2009-04-15
Load up the settings as root:
```
gksu nvidia-settings
```

xorg.conf is a system file which means only root has permission to write to it

---

### Post by axlotxlikexvegas on 2009-04-15
Thanks bro that worked.

---

