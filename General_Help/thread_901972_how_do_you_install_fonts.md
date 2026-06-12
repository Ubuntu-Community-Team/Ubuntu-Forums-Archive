---
title: "how do you install fonts?"
date: 2008-08-26
forum: General Help
---

### Post by Prominence on 2008-08-26
Title says all, how do you install fonts in Ubuntu?

---

### Post by PurposeOfReason on 2008-08-26
Easiest way is to drop them in ~/.fonts

---

### Post by Prominence on 2008-08-26
Is that a folder path?

---

### Post by Dr Small on 2008-08-26
> **Prominence said:**
> Is that a folder path?
Yes, and if it doesn't exist (which it should, on Gnome), just create it.
```
mkdir ~/.fonts
```

Then add your fonts to it.

---

### Post by Prominence on 2008-08-26
Thank you!

---

### Post by shirilover on 2008-08-26
And after you copy your fonts to ~/.fonts, you need to regenerate your font cache.
```

fc-cache -v ~/.fonts

```
You may need to prepend sudo if you get errors.

---

### Post by d0nut on 2008-08-28
it says I already have the file .fonts, but when I follow the path it is no where to be found.  Is it possible its a hidden file? And if so how do I "unhide" it.   Thanks.

---

### Post by Vivaldi Gloria on 2008-08-28
> **d0nut said:**
> it says I already have the file .fonts, but when I follow the path it is no where to be found.  Is it possible its a hidden file? And if so how do I "unhide" it.   Thanks.

Folders that star with a dot are hidden. To see them press CTRL+H in nautilus (file manager).

Btw, ~ is your home folder. So open your home folder, press ctrl+H and find .fonts folder there.

---

### Post by Crafty Kisses on 2008-08-28
The folder path or kfontviewer.

---

### Post by d0nut on 2008-08-28
> **Vivaldi Gloria said:**
> Folders that star with a dot are hidden. To see them press CTRL+H in nautilus (file manager).

Btw, ~ is your home folder. So open your home folder, press ctrl+H and find .fonts folder there.

Awesome!  Thank you very much!

---

