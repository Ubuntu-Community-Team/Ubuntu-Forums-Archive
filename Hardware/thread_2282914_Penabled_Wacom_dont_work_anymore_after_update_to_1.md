---
title: "Penabled Wacom dont work anymore after update to 15.04"
date: 2015-06-17
forum: Hardware
---

### Post by zottelmann-h on 2015-06-17
Hello!

as i wrote in the title, both stylus and touchscreen of my Fujitsu T730 don't work anymore, after i upgrade from Ubuntu 14.04 to 15.04.
I followed the steps on the input wacom site, but when i check with  ```
dmesg | grep -i wacom
``` i only get:

```
wacom: module verification failed: signature and/or  required key missing - tainting kernel

```

So any help is welcome. I realy need the stylus/touch stuff working. And actually i dont want to reinstall 14.04 ;)

---

### Post by zottelmann-h on 2015-06-17
Update:

```
sudo inputattach --w8001 /dev/ttyS4
```

seems to work, but only as long as the terminal is running. so whats wrong? what can i do?

---

### Post by zottelmann-h on 2015-06-26
I really would like to know how to solve this :(

---

