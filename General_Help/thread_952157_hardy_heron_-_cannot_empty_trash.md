---
title: "hardy heron - cannot empty trash"
date: 2008-10-18
forum: General Help
---

### Post by TangerinePudding on 2008-10-18
Hi everyone, 

I've run into a problem with emptying my trash. I currently have a folder stuffed with files just sitting there occupying space. After sifting through files I've attempted to use the sudo nautilus and navigating to the trash, but when I try to I get the error message:

"trash": operation not supported.

Any other ideas as to how I can delete the folder?

---

### Post by Pro-reason on 2008-10-18
Do this:

```

sudo rm -frv ~/.local/share/Trash /root/.local/share/Trash

```

That will remove all your trash on your main partition.  If you have additional partitions mounted, you will have to delete “.Trash*” on each of them.

---

