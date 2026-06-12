---
title: "Mounting and desktop icons...."
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by dfrandin on 2008-02-27
Is there a way to configure (or trick) Ubuntu into NOT putting a mounted drive icon on my desktop?
I dualboot XP and Ubuntu and Ubuntu insists on putting both the DellUtility partition and my XP NTFS partition icons on the desktop.. I like the NTFS partition there, but would like to get rid of the DellUtility one.. I also get this when I open a TrueCrypt volume, which I'd prefer to not see on the desktop, since I have a symbolic link to its mount point in my home directory.. Is this possible??

Thanks
Dave

---

### Post by jan quark on 2008-02-28
you can try the following

run
```

gksudo gconf-editor
```

navigate to 
apps > nauitilus > desktop

and uncheck the volumes you do not want to be displayed

---

### Post by dfrandin on 2008-02-29
I tried the gconf-editor, under apps > nauitilus > desktop, only found a "volumes_visible" checkbox. Tried unchecking it, logging out/in, still see the mounted volume icons.. Any other ideas??

Thanks
Dave

---

