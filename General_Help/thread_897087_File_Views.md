---
title: "File Views"
date: 2008-08-21
forum: General Help
---

### Post by Lifedeath on 2008-08-21
Howdy,

Is there an option to "lock" the way files are viewed in folders? e.g. I prefer to have everything in my Music folder (all subfolders and files) viewable as Lists instead of Icons, but find that the setting often changes itself back to the latter.

---

### Post by drs305 on 2008-08-21
Try running the following command. It should set list view as the default. 
```
gconftool-2 --type string --set /apps/nautilus/preferences/default_folder_viewer 'list_view'

```

This is a shortcut for starting "gconf-editor" and navigating to the same spot to set defaults. This will set ALL folders to the list-view, so it may not be exactly what you are looking for.

Nautilus is *supposed* to save each folder's viewing preferences, I believe.

---

### Post by Lifedeath on 2008-08-21
Thanks very much, that command did the trick.

---

