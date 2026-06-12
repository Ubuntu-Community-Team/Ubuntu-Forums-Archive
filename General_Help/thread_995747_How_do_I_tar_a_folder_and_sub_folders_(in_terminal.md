---
title: "How do I tar a folder and sub folders (in terminal)"
date: 2008-11-28
forum: General Help
---

### Post by Johnsie on 2008-11-28
I want to tar all the files in a folder and any subfolders within that folder. What is the command to do that in terminal? I  have no gui.

---

### Post by flanagan on 2008-11-28
According to "man tar":

    tar -cvvf foo.tar foo/

will pack up the folder foo and everything underneath it.

---

### Post by ideewoww on 2008-11-28
Idee jewelry wholesale,supply,necklace supply, earrings supply,ring supply, hangs falls supply, jewelry wholesale,925 silver jewelry wholesale,gem,makeup,hairdressing[img]http://www.ideewomen.com/cn/uploads/1.jpg[/img]http://www.ideejewelry.com/

---

### Post by prshah on 2008-11-28
> **Johnsie said:**
> I want to tar all the files in a folder and any subfolders within that folder. What is the command to do that in terminal? I  have no gui.

```
tar -c --bzip2 -f foo.tar foo/
``` will add compression to the tar file.

---

### Post by m_l17 on 2008-11-28
> **prshah said:**
> ```
tar -c --bzip2 -f foo.tar foo/
``` will add compression to the tar file.

You should name it foo.tar.[COLOR="Red"]bz2[/COLOR], when using the bzip2 compression.

Take a look at this Wiki entry:

[https://help.ubuntu.com/community/FileCompression#GNU%20Tar%20(.tar)]("https://help.ubuntu.com/community/FileCompression#GNU%20Tar%20(.tar)")

---

