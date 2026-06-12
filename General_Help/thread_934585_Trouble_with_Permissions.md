---
title: "Trouble with Permissions"
date: 2008-09-30
forum: General Help
---

### Post by RyanfromtheShire on 2008-09-30
I deleted some files, and they're in my trash bin. When I try to delete it, it won't. Then when I try to change the permissions, I get this:

[IMG]http://img89.imageshack.us/img89/1275/screenshottv2.png[/IMG]

---

### Post by ju2wheels on 2008-09-30
Open a terminal and run the following:

```

sudo rm -rf ~/.local/share/Trash

```

---

### Post by RyanfromtheShire on 2008-09-30
> **ju2wheels said:**
> Open a terminal and run the following:

```

sudo rm -rf ~/.local/share/Trash

```



Thanks m8!

---

