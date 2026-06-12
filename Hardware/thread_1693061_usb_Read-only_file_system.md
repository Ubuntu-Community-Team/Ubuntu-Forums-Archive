---
title: "usb Read-only file system"
date: 2011-02-22
forum: Hardware
---

### Post by jacko's on 2011-02-22
Hello I install Chrunchbang on my usb stick to try it out. Only problem now is as described above.
I've tried something along these lines from other posts
sudo chmod -R 777 /media/X
sudo chmod - /dev/disk/by-id usb-xx
sudo chown -hR jacko /media/X

Now I'm here because I'm starting to feel the fury only known to computer nerds when they hit a wall repeatedly.
I'm sure I've just missed something small. But I'm too tired at this point, and I have a lot of school assignments in the next three days.

---

### Post by fjgaude on 2011-02-22
One other thing to try:

```
sudo chown -R jacko:jacko /media/X
```

Can you not see the drive as mounted on the desktop?

---

