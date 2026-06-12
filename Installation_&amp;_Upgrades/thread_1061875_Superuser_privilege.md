---
title: "Superuser privilege"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by Draigcoch on 2009-02-06
I recently had a sudden break in my internet connection - this was while the update manager was working.

I now get the following error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct problem.
E: -cache -. open() failed, please report.

I have gone into 'Applications' then 'Terminal' and entered the required code.  I then get another error message:

requested operation requires superuser privilege


What does this mean and how do I get round this problem?

Thanks

---

### Post by damis648 on 2009-02-06
Open a terminal and instead type in:
```
sudo dpkg --configure -a
```
and that should fix your problem. :popcorn:

---

### Post by taurus on 2009-02-06
You need to read this, [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo).

---

