---
title: "Automount, internal hard drive"
date: 2009-10-31
forum: Hardware
---

### Post by edoiks on 2009-10-31
I want to automount an internal hard drive. In 9.04 I used Hal policy:

```

<device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">true</merge>
      </match>
    </match>
  </device>

```but now (in 9.10) it is not working, for some purposes I don't want to use fstab. 
I want internal drives to be mounted like an external drives are.

---

