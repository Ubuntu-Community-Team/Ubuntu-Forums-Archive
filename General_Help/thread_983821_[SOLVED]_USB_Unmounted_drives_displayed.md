---
title: "[SOLVED] USB Unmounted drives displayed"
date: 2008-11-16
forum: General Help
---

### Post by jermanbdogg on 2008-11-16
Hello,

First off, as all other n00bs list. "HEY I AM A LINUX NEWBIE". I have a small annoyance that I was wondering if there was a fix/workaround for. I have an internal Multi-card reader (mounts and unmounts fine) I was wondering if there was a way to not list them in Nautilus and in "Places" on the panel. It really isn't a problem as everything works just fine, i am just one of those perfectionists that want everything to look the other way.

Thanks for your time and help :D

---

### Post by jermanbdogg on 2008-11-18
anyone????

---

### Post by cdtech on 2008-11-18
You could use the gnome editor:
```
$ gconf-editor
```
apps > nautilus > preferences
Uncheck the "media_automount" option

Hope this helps......

---

### Post by cdtech on 2008-11-18
Are they listed within your "/etc/fstab" file? Just asking....

---

### Post by jermanbdogg on 2008-11-18
I just checked. only the HD partitions are listed. Also I tried the gconf editor and unchecked the box. Nothing changed.

---

### Post by cdtech on 2008-11-18
> **jermanbdogg said:**
> I just checked. only the HD partitions are listed. Also I tried the gconf editor and unchecked the box. Nothing changed.

Did you logout and back in?

---

### Post by jermanbdogg on 2008-11-18
Sorry, forgot to mention that. First I tryed a normal logout-in. Nodda. Then a hard boot. Nothing changed, however, received a error message on bootup: "unable to enumerate USB device on port 5"

---

### Post by easoukenka on 2008-11-18
sorry not too much time for me but anything in your /media will be shown there.  You could alter your fstab to mount these devices somewhere else take a look in /etc/fstab and give it a whirl

---

### Post by jermanbdogg on 2008-11-18
unfortunately the only thing i have in my /media folder is is manually config'd NTFS HD, and two empty CD-Rom devices. I think the only thing that is annoying is the USB drives. My fstab file only has the HD partitions on it.

---

### Post by jermanbdogg on 2008-11-24
is there anyone that can help me out with this? :(

---

