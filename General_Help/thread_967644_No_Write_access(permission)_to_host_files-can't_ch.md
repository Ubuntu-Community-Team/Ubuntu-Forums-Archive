---
title: "No Write access(permission) to /host files-can't chown either"
date: 2008-11-02
forum: General Help
---

### Post by offline on 2008-11-02
I am trying a wubi installation of Ubuntu 8.04.1 on a windows 2000 pro--fat32 machine. The problem: I can't write to /host(for example to .../my documents/beginning javascript) the owner of the /host recursively is root. I can't change the owner with chown -R either. Interestingly after doing some search there seems to be no other people mentioning this. How can I fix this?
Since the /home is < 1GB (ridiculously useless) I at least need to write to /host.

---

### Post by ago on 2008-11-03
This is a fat32 limitation, it does not support file permissions.

---

### Post by offline on 2008-11-05
Hmmm. So by default wubi restricts write-access to the /host folders and becuse we have fat32 here, we can't do anything to change that when in ubuntu? What a mess really! Can there be a workaround I wonder...

---

