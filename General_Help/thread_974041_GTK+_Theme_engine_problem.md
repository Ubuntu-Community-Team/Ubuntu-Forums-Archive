---
title: "GTK+ Theme engine problem"
date: 2008-11-07
forum: General Help
---

### Post by wildman4god on 2008-11-07
I installed the slickness theme and when I went to apply it it gave me static about GTK+ theme engine not installed, I went to synaptic but I couldn't find which package to download, what do I need to install to get this theme to work correctly?

---

### Post by Idefix82 on 2008-11-07
I just downloaded this theme to have a look what is going on. Note, that I have no idea about how these themes work. But when I extracted the tar and opened the gtkrc file in the gkt-2.0 folder I found the following lines:
```

style "unstyle"
{
engine ""
{}
}

```

engine "" doesn't look right. I then searched for everything that uses the style "unstyle" and the only line I found is this:
```
class "SPColorSlider"		style "unstyle"
```

My suggestion is to comment out this line and to delete the style "unstyle" block altogether. Then repackage the tar and reinstall. See if that works.

---

### Post by wildman4god on 2008-11-07
No That didn't work, but thanks anyway.

---

### Post by NilsE on 2008-11-07
That is a common problem with older themes not yet adapted to 8.10.  Just put a legitimate engine name between the ""s and it will work.  I used the same engine as the first engine entry.

That entry is for the purpose of fixing a bug with the engine for certain functions that has been fixed in the new GTK.

---

### Post by wildman4god on 2008-11-07
Thanks for that.

---

