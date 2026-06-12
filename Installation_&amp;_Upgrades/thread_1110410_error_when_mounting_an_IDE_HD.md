---
title: "error when mounting an IDE HD"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by Will4 on 2009-03-29
hey guys,

I messed up with the HD, i right clicked on the HD icon and at the las tab (Volume) clicked the [settings] below and wrote everything i saw above. Exactly the same!! Stupidiot!!  

when trying to mount the IDE Hard Drive, it gives me this ERROR and won't mount it.
IT says

> impossible to mount the device <<Almacen>>

Details>

mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /) 

---

### Post by cariboo on 2009-03-29
Do you have any weird characters or spaces in the the volume label? eg: 

```
<<My External Drive>>
```

Linux doesn't deal well with illegal characters or spaces.

Jim

---

### Post by Will4 on 2009-03-29
No, the name is <<Almacen>>

i just messed up with the properties of the HD, i changed some lines. I'll tell you how

i right clicked on the HD icon, then [properties], then [Volume] and clicked on the [Settings] button below. After that I wrote on every space what i saw above and after that, BUM!! the ERROR message. 

does it have a fix?? it's all about mount_point containing weir characters. I think!! don't trust me on that...

Any idea??

---

