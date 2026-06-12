---
title: "synaptic software"
date: 2008-07-14
forum: General Help
---

### Post by cnislev on 2008-07-14
Hello, I recently updated to Hardy and now get the following message when trying to open Synaptic Package Manager:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When trying stuff in Terminal I am told I need to be a super user. Not sure where to go from here...

---

### Post by linuxisfree on 2008-07-14
> **cnislev said:**
> Hello, I recently updated to Hardy and now get the following message when trying to open Synaptic Package Manager:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When trying stuff in Terminal I am told I need to be a super user. Not sure where to go from here...

Type the ff. in Terminal

```
sudo dpkg --configure -a
```

the "sudo" in the code allows you to essentially have root (super user) access.

---

### Post by avtolle on 2008-07-14
At terminal (Applications>>Accessories>>Terminal) do this: ```
sudo dipkg --configure -a
```Use of sudo makes you a supre user temporarily. BTW, it will ask for you to input your password. Do so, just be aware that you will not see anything when you do it. Then press Enter after putting in your password.

---

### Post by oldsoundguy on 2008-07-14
super user = sudo

so your command in terminal is: sudo dpkg --configure -a
enter your password.

---

