---
title: "Nautilus Actions or Nautilus Scripts Help..."
date: 2008-08-02
forum: General Help
---

### Post by seerretsel on 2008-08-02
Is there either a Nautilus Action or Script which will enable me to right-click on a folder and select something like 'Empty Folder' which will then subsequently delete all the contents of that folder?  There is a right-click extension you can install in Windows which does exactly that same thing.  Surely, this must be possible in Linux(Ubuntu, Fedora, et al.).

---

### Post by mc4man on 2008-08-02
> Is there either a Nautilus Action or Script which will enable me to right-click on a folder and select something like 'Empty Folder

here's how you'd do that, though be advised it will [COLOR="Red"]delete ALL files in a folder and in _any sub folders if present_ immediately and without warning ![/COLOR]
I would test it out on some made up files, folders first.

Again only use when you want every file in a folder deleted including files in any subfolders if present.


easier to copy and paste parameters then to try to type
> %M -type f -exec shred  -n 0 -u  '{}' \;

---

