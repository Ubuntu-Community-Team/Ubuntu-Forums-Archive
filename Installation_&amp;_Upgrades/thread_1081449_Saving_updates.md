---
title: "Saving updates"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by mrl777 on 2009-02-26
Is there a way to save all the system updates that one has downloaded so if you reload the OS you can then restore the updates you have downloaded... rather than having to get the updates from the web all over again?

---

### Post by ajgreeny on 2009-02-26
They will already be in /var/cache/apt/archives.  You can use aptoncd if you wish to make an iso file every so often and then just install and use aptoncd on the new OS to add back everything.

---

### Post by mrl777 on 2009-02-26
> **ajgreeny said:**
> They will already be in /var/cache/apt/archives.  You can use aptoncd if you wish to make an iso file every so often and then just install and use aptoncd on the new OS to add back everything.

Do you also now how to save Tomboy notes?  I can't find find the file.

---

### Post by ajgreeny on 2009-02-27
They are html files in a hidden folder* ~/.tomboy* in your home folder.  Just save the whole .tomboy folder and it will have all your notes.

---

