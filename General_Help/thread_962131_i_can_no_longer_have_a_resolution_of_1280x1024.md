---
title: "i can no longer have a resolution of 1280x1024"
date: 2008-10-28
forum: General Help
---

### Post by schimm1 on 2008-10-28
it used to be that when i booted up, my reso would be 800x600, but that would be fine and good, i'd just open up terminal and type xrandr -s 1280x1024 and it'd be fixed

now i have no 1280x1024, i'm stuck in 1280x800

anyone know how to fix this?

---

### Post by jeyaganesh on 2008-10-29
Try the following command,

sudo dpkg-reconfigure xserver-xorg

Then follow the on-screen instruction, select key board layout and screen resolution. Exit.

Then restart the x-window by 'Alt+Ctrl+Back space'. It mostly fix the resolution problem.:)

---

### Post by schimm1 on 2008-10-29
> **jeyaganesh said:**
> Try the following command,

sudo dpkg-reconfigure xserver-xorg

Then follow the on-screen instruction, select key board layout and screen resolution. Exit.

Then restart the x-window by 'Alt+Ctrl+Back space'. It mostly fix the resolution problem.:)


didn't work, it didn't give me any options about resolution at all, just keyboard

did i mention i'm using hardy?

---

