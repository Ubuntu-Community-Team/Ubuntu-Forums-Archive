---
title: "how to delete folders with a lock?"
date: 2008-08-23
forum: General Help
---

### Post by mack27 on 2008-08-23
Hi,
i was trying to play dvd files and i copied the folders from the disk onto the computer, hoping it would help. they appear on my desktop with a lock icon next to them. when i try to remove them (move to bin) access is denied, file unmovable. how do i delete those folders?

---

### Post by LateNiteTV on 2008-08-23
```
sudo rm -rfi /path/to/whatever
```

---

### Post by Iowan on 2008-08-23
Check the folder Properties. You may need to edit those to unlock them.

---

### Post by gjoellee on 2008-08-23
> **Iowan said:**
> Check the folder Properties. You may need to edit those to unlock them.

 thats recommended, if you use the "rm" wrong you may crash your system!

---

### Post by mack27 on 2008-08-23
> **Iowan said:**
> Check the folder Properties. You may need to edit those to unlock them.

thanks. it worked

---

### Post by mack27 on 2008-08-23
> **gjoellee said:**
> thats recommended, if you use the "rm" wrong you may crash your system!

yeah, i was afraid of that so i went with the properties of folders and edited them. thanks!

---

### Post by LateNiteTV on 2008-08-23
> **gjoellee said:**
> thats recommended, if you use the "rm" wrong you may crash your system!

hence the reason the "i" switch was passed so he can confirm that he really wants to do it.

---

