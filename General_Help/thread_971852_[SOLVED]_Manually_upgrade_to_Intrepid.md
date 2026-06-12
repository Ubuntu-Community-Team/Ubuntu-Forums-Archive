---
title: "[SOLVED] Manually upgrade to Intrepid?"
date: 2008-11-05
forum: General Help
---

### Post by mistertee on 2008-11-05
Hi,

For some reason software update isn't finding Intrepid as an available update...is there a way to force an upgrade without rebuilding the system?

Thanks!

---

### Post by scouser73 on 2008-11-05
Hi, goto **System, Administration, Software Sources** click the **Updates** tab, in the drop-down menu **Release Upgrade** select **Normal releases**. In the Ubuntu Updates section, tick the 4 boxes, in the Automatic Updates section click on the drop-down menu and select Daily

---

### Post by tuxxy on 2008-11-05
or you could open terminal and run

```
update-manager -d
```

---

