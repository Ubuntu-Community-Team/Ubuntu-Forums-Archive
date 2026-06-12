---
title: "Deleting Memory stick icon?"
date: 2008-05-14
forum: Hardware
---

### Post by Swinkid on 2008-05-14
Hey,
I recently put my memory stick into my laptop, a icon appears on my desktop allowing me to open my stick when i double click it, but how can i turn this off, also i cannot delete the icon that was there, Just says: "There was an error getting information about "ALEX 83.volume"." when i insert it again, another icon appears (the same one) but that goes when removing my stick.
Thanks, Swinkid. (new Ubuntu User)

---

### Post by nick_h on 2008-05-14
Type:
```
gconf-editor
```
Under apps/nautilus/desktop you will see the option "volumes visible".

---

