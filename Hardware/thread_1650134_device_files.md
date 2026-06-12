---
title: "device files"
date: 2010-12-21
forum: Hardware
---

### Post by Mosabama on 2010-12-21
Hey,

how to know which device file is linux using for the sound card for example? or VGA ? or anything.

is there any way to know that using lspci or lsusb or lshw ?

---

### Post by garvinrick4 on 2010-12-21
```
lspci -v | less 
```

---

### Post by Mosabama on 2010-12-21
Thank you, but I see that this command displays the kernel module its using .. I need to know the device file. for example /dev/audio.

---

### Post by Mosabama on 2010-12-21
any one?

---

