---
title: "DV and ieee1394 [FIXED]"
date: 2004-11-06
forum: Hardware &amp; Laptops
---

### Post by wfx on 2004-11-06
The system will not creat the required dev entry by default.
So if you want to use a dv cam via firewire do
```

sudo mknod /dev/raw1394 c 171 0 && chmod 646 /dev/raw1394

```

---

