---
title: "USB Help"
date: 2008-11-29
forum: Hardware
---

### Post by the3dman on 2008-11-29
After I installed UNR Ubuntu via a flash drive on my laptop, under Computer it shows a USB drive as being plugged in. The problem is that I dont have a usb drive plugged in. Not a huge issue but it just bothers me lol. Any idea on how to make it go away?

---

### Post by the3dman on 2008-11-30
Nobody?

---

### Post by 3rdalbum on 2008-11-30
Do you have a memory card reader in your computer? Does the "drive" show any contents if you put a memory card in?

Go into the terminal (Applications > Accessories > Terminal) and post the output of this command:

```
sudo fdisk -l
```

If there's any sort of flash memory being recognised by the system, we should be able to see what it is through that command.

---

### Post by the3dman on 2008-11-30
Thank you, I feel dumb. I didn't even think that was for the built in memory card reader. I guess I didn't think that would be detected as a USB Drive. Thanks again.

---

