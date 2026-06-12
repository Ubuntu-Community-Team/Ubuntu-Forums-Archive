---
title: "How to edit etc/apt/sources.list"
date: 2008-08-13
forum: General Help
---

### Post by nyborjare on 2008-08-13
Need help in change sources.list

I want to add the following to the list:
# Remastersys
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/

When I open sources.list and paste this line into it and try to save I am told I do not have the rights to change.

I am new to this an need some support Please

Regards

---

### Post by null byte on 2008-08-13
```
gksudo gedit /etc/apt/sources.list
```
in Terminal.

---

### Post by hyper_ch on 2008-08-13
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by nyborjare on 2008-08-14
> **null byte said:**
> ```
gksudo gedit /etc/apt/sources.list
```
in Terminal.
Thank you so much for your support.

Matter solved.
Regards
michael

---

### Post by nyborjare on 2008-08-14
> **hyper_ch said:**
> [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
Thank you for information
Will read and learn
Regards
Michael

---

