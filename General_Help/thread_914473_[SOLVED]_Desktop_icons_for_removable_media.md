---
title: "[SOLVED] Desktop icons for removable media"
date: 2008-09-08
forum: General Help
---

### Post by tgerbert on 2008-09-08
I have ubuntu studio 8.04 on my desktop, and when I insert removable media it shows up in the applications menu under places, but I would also like to have icons on the desktop as well...any ideas?

---

### Post by Cl0ud9 on 2008-09-08
Try unmounting then manually mounting the removable media in a directory in /media,
For example /media/usbdevice

I did this with an external hard drive once, and after the initial manual mount it would auto mount for me and give me an icon on the desktop.

---

### Post by robz0rz on 2008-09-09
You want removable media to appear on your desktop? You may want to try [Ubuntu Tweak]("http://ubuntu-tweak.com/"). It gives you little handy options like what you want in a graphical user interface.

Download&install the program from [here]("http://ubuntu-tweak.com/downloads") (either download the "package for all" or follow the instructions "how to add the source").
Once you installed it, click Desktop, Desktop Icons, and you'll get some options you can tick, like for example "Show Mounted Volumes on Desktop".

Hope I could help :)

---

### Post by billgoldberg on 2008-09-09
Press "alt+f2" enter "gconf-editor".

Navigate to "apps -> naulilus -> desktop" and make sure the last box is tagged.

That way all removable media will appear on the desktop.

No need to use third party software for things you can do just as fast and natively.

---

### Post by tgerbert on 2008-09-10
> **billgoldberg said:**
> Press "alt+f2" enter "gconf-editor".

Navigate to "apps -> naulilus -> desktop" and make sure the last box is tagged.

That way all removable media will appear on the desktop.

No need to use third party software for things you can do just as fast and natively.

That was easy, thanks!

---

### Post by sayakb on 2008-09-10
Please mark the thread as solved. (Thread tools->Mark thread as solved)

---

