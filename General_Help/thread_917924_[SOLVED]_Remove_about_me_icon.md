---
title: "[SOLVED] Remove about me icon"
date: 2008-09-12
forum: General Help
---

### Post by Soulcage on 2008-09-12
I set a icon in about me and now I don't want it there. I selected "no image" but there still is a icon at the lock screen window.
How do I completely remove it?

---

### Post by ibuclaw on 2008-09-12
Open Nautilus and press **Ctrl+H** your "About Me" logo is stored in your home folder.
I can't remember the name of the file, but you should see it as a thumbnail.

Regards
Iain

---

### Post by Rhubarb on 2008-09-12
The file is called **.face**
You can get rid of it thus:

Open up a terminal (Applications --> Accessories --> Terminal), and enter this in:
```
rm ~/.face
```

---

### Post by Soulcage on 2008-09-12
Thanks so much!!

---

