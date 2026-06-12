---
title: "KVM error, &quot;Cannot accsess storage file ... no such file or directory&quot;"
date: 2024-12-02
forum: Hardware
---

### Post by civilpolisen on 2024-12-02
As you can see, it's about 60% of all storage that's no longer found. 59% to be exact!
How can all just go disappear and how do I get it back...!?

x x x

Error when starting the Virtual Server


The missing disk! How do I restore toe lost space!?

---

### Post by TheFu on 2024-12-02
You are using LVM. To see what's happening, we need LVM information.  The most concise information comes from 3 commands:
```
sudo pvs
sudo vgs
sudo lvs
```

---

