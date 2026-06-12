---
title: "Where is the trash folder in Hardy?"
date: 2008-07-28
forum: General Help
---

### Post by carverj on 2008-07-28
I have just installed Hardy Heron and cannot locate where the deleted items are stored!!?

Thanks for helping me find this.

---

### Post by iaculallad on 2008-07-28
> **carverj said:**
> I have just installed Hardy Heron and cannot locate where the deleted items are stored!!?

Thanks for helping me find this.

Hardy Heron's Users Trash:

```
cd ~/.local/share/Trash
```

---

### Post by kernelhaxor on 2008-07-28
If you want the trash can icon on the desktop, type in a terminal:
```
gconf-editor
```
and in the resulting window, on the left pane, choose apps -> nautilus -> desktop 
On the right side, check the check box trash_icon_visible


Hope that helps

---

### Post by carverj on 2008-08-01
I use the command gksudo for root nautilus and delete files there. I can then see that my deleted files are being sent to /root/.local/share/Trash folder.
How do I then permanantly delete these files?

Thanks all

---

### Post by carverj on 2008-08-01
Solved it. Just right-click the files folder and click 'delete'

---

