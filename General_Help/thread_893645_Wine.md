---
title: "Wine"
date: 2008-08-18
forum: General Help
---

### Post by sdalgl72 on 2008-08-18
Hey all,

I installed Wine and then installed PKR on it which didn't work so I uninstalled pkr and then uninstalled WINE only to still have the WINE category in my Applications list with the only folder being PKR any ideas how to resolve this?

---

### Post by ibuclaw on 2008-08-18
In nautilus (your filesystem browser), press Ctrl+H to show hidden files/folders and go into
```
.local -> share
```
And you'll see two directories of interest.

[LIST]
[*]**applications**
Where you will see the folder "wine".
[*]**desktop-directories**
Where you should see one or two files with the words "wine" in.
[/LIST]

Regards
Iain

---

### Post by sdalgl72 on 2008-08-18
> **tinivole said:**
> In nautilus (your filesystem browser), press Ctrl+H to show hidden files/folders and go into
```
.local -> share
```
And you'll see two directories of interest.

[LIST]
[*]**applications**
Where you will see the folder "wine".
[*]**desktop-directories**
Where you should see one or two files with the words "wine" in.
[/LIST]

Regards
Iain

Sorry I cant seem to find those folders

---

### Post by sdalgl72 on 2008-08-18
Thanks for your help just did a search for WINE and selected hidden files as well and deleted or reference to it.  Thanks for all your help though.

---

