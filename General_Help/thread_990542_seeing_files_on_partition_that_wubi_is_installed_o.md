---
title: "seeing files on partition that wubi is installed on"
date: 2008-11-22
forum: General Help
---

### Post by br3athe on 2008-11-22
hi 
I have installed wubi on a ntfs partition ( D:  in windows )
I can see the folders / files in the C drive on windows from ubuntu , but not the d drive where the ubuntu install is , any ideas 
thanks

---

### Post by break19 on 2008-11-23
From what I understand about how Wubi does it's magic, you -won't- be able to see any files there. Wubi's install is to a "fake" partition, similar to how vmware creates a drive, by making a file.

Wubi's install is on a single file inside that window partition.. 

I could be wrong about the ability to see the files there, But I do not believe so.

---

### Post by ago on 2008-11-25
They are visible under /host

---

