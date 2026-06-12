---
title: "Turn off Harddrive on netbook"
date: 2010-06-30
forum: Hardware
---

### Post by josejosetomas on 2010-06-30
Hello, I have a WIND U120. I have ubuntu netbookremix 10.04.
HOw can I turn off the harddrive? because I am running from USB and I don't want to have the harddrive draining energy from the battery. I need to have install the harddrive because some times I need to boot from windows. How can you help me. Thanks

---

### Post by mikewhatever on 2010-06-30
You could turn on aggressive power management:
```
sudo hdparm -B 1 S -1 /dev/sdX
```
Take a look at 'man hdparm' for more options.

---

### Post by kerry_s on 2010-06-30
if your running from usb, the drive should not be active if it's not mounted.

---

### Post by josejosetomas on 2010-06-30
Thanks... Kerry you mean: If the harddrive is not mounted is not spinning? I want to save battery... And I am a little new on linux. Thanks

---

