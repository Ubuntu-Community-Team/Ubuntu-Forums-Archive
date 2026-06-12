---
title: "Keyboard OFF after sleep"
date: 2011-04-21
forum: Hardware
---

### Post by metRo_ on 2011-04-21
Hi,
My keyboards goes OFF when i enter in sleep mode, so after i need to insert my pass but i can't because keyboard doesn't work :S

---

### Post by Zorael on 2011-04-22
Is it a USB keyboard?

If so, try creating a file like **/etc/pm/sleep.d/20_keyboard** that looks like this;
```
#!/bin/bash

case "$1" in
  suspend)
    modprobe -r usbhid hid
    ;;
  resume)
    modprobe hid usbhid
    ;;
esac
```

It may have to be set as executable (+x), not sure.

---

