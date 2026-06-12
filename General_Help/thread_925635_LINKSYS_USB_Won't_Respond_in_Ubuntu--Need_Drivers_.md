---
title: "LINKSYS USB Won't Respond in Ubuntu--Need Drivers? Works in Windows..."
date: 2008-09-20
forum: General Help
---

### Post by peqkid on 2008-09-20
I cant seem to get my wireless network adapter (WUSB54Gv2) to work on ubuntu...It works on my windows partition, not ubuntu. Any suggestions?

---

### Post by pytheas22 on 2008-09-20
Please post the output of the following commands so that we can figure out which driver you need to install:
```

lshw -C Network
lspci -nn
lsusb
uname -m
```

---

