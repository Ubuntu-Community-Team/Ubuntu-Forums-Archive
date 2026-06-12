---
title: "[SOLVED] samba shares not being remembered"
date: 2008-11-02
forum: General Help
---

### Post by freddybob on 2008-11-02
Got a weird folder sharing problem.  I'm guessing it is a permissions issue but I don't know.

In nautilus I right-click on a folder and enable sharing, all seems to work - the folder icon changes to indicate sharing is enabled.  But when I refresh the view the icon changes back to a normal unshared folder and when I look at the sharing options again the folder is not shared.

---

### Post by freddybob on 2008-11-02
purging samba and reinstalling it and ubuntu-desktop now means shares are remembered

problem is other machines cannot access these shares, I'm getting "Failed to mount Windows share" errors when I try (access should not require authentication)

what permissions should I set on the folders?

---

### Post by freddybob on 2008-11-02
ok, in Nautilus I looked at and re-applied the permissions on my home folder (/home/freddybob) and that seems to have solved it

my shares are sub-folders in my home folder

don't know how the permissions went wrong in the first place

---

