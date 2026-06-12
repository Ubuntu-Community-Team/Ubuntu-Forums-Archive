---
title: "Wastebasket, can't delete a directory."
date: 2008-08-28
forum: General Help
---

### Post by chrispche on 2008-08-28
I have an entire directory which contains pictures and other stuff which I can't delete. I have tried the hidden trash directory. Is there any other hidden directory or something else I can do to empty the trash completely?

---

### Post by Taxman415a on 2008-08-28
So I assume you tried to delete the directory through the GUI by selecting move to trash, and now when you try to empty the trash it doesn't work? Can you tell us what error message you get or explain in more detail what you are doing?

---

### Post by WRDN on 2008-08-28
Type this in the Terminal:

```
sudo rm -rfI ~/.local/share/Trash
```

When prompted to "remove all arguments recursively?", just enter "y".

---

### Post by drs305 on 2008-08-28
If you want to know why you can't delete it and the various methods to safely remove trash, here is a tutorial:
[Disk Full? - Check Your Trash Bin(s)]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by chrispche on 2008-08-29
> **WRDN said:**
> Type this in the Terminal:

```
sudo rm -rfI ~/.local/share/Trash
```

When prompted to "remove all arguments recursively?", just enter "y".

Thanks that did it.

---

