---
title: "Searching multiply drives with gnome search tool"
date: 2008-09-02
forum: General Help
---

### Post by jabryl on 2008-09-02
How can I search all my hard drives at once? I've tried the "Include other filesystems option" it didn't do anything.

---

### Post by jabryl on 2008-09-02
bump

---

### Post by mssever on 2008-09-02
Under look in folder, did you choose Filesystem?

By the way, it's considered bad etiquette to bump threads more than once per day.

---

### Post by jabryl on 2008-09-02
> **mssever said:**
> Under look in folder, did you choose Filesystem?

By the way, it's considered bad etiquette to bump threads more than once per day.

Yes, I tried that. It didn't work.
I can use the "Look in folder" option to search individual drives but not all of them at once.

---

### Post by mssever on 2008-09-02
> **jabryl said:**
> Yes, I tried that. It didn't work.
I can use the "Look in folder" option to search individual drives but not all of them at once.
Have you verified that the partitions are mounted? (Type mount for a list of currently-mounted partitions.) If they're mounted, then I can't imagine how that could possibly fail, because mounted partitions appear to the system merely as part of the directory structure.

---

### Post by jabryl on 2008-09-02
OK, I figured it out.

File System has to be selected under Look in folder.

Select more options has to be expanded.

Then I had to go into the configuration editor, under apps, gnome-search-tool, select. The box for include_other_filesystems needs to be checked. This option needs to be set in the configuration editor, it does not work if it's selected in the search program itself.


It's clearly a bug of some sort. This is one of the most bizarre workarounds I've ever had to do.

---

