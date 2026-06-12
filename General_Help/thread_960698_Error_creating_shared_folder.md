---
title: "Error creating shared folder"
date: 2008-10-27
forum: General Help
---

### Post by rmcellig on 2008-10-27
When I try and create a shared folder I get this error. I have admin priveledges or at least I thought I did. What should I do?


'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

---

### Post by alienprdkt on 2008-10-27
type this in terminal:

gksu nautilus

then right-click folder you want to share, and try enabling share permissions.

---

### Post by alienprdkt on 2008-10-27
type this in terminal:

gksu nautilus

then right-click folder you want to share, and try enabling share permissions.

---

### Post by alienprdkt on 2008-10-27
type this in terminal:

gksu nautilus

then right-click folder you want to share, and try enabling share permissions.

---

### Post by plucky on 2008-10-27
> **rmcellig said:**
> When I try and create a shared folder I get this error. I have admin priveledges or at least I thought I did. What should I do?


'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

This is a known problem with sharing.

See this [thread](http://ubuntuforums.org/showthread.php?t=772706) for a solution.

Good Luck

---

