---
title: "add/remove applications won't populate (ubuntu 8.10)"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by ndipity on 2009-02-24
Hi all,
Forgive me for asking what may be a stupid question, but I am really new to Linux... 
I recently installed ubuntu 8.10 and at first was able to search for and add new applications with no problem. Now, when I open the add/remove applications window all I get is "There is no matching application available", and there are no longer any categories off to the left, only "all". This is the same whether I'm showing all available applications, installed applications, etc.
If anyone could tell me how to fix this I'd really appreciate it. Thanks!

---

### Post by cariboo on 2009-02-24
Try going to System-->Administration-->Synaptic Package Manager and click the reload button to update the repositories.

Jim

---

### Post by ndipity on 2009-02-24
> **cariboo907 said:**
> Try going to System-->Administration-->Synaptic Package Manager and click the reload button to update the repositories.

Jim
Thanks Jim,
I am able to install programs through the synaptic package manager, but reloading there didn't seem to help the issue with add/remove programs - I'm still not seeing anything listed there... is there anything else I might try?
Sara

---

### Post by plucky on 2009-02-25
> **ndipity said:**
> Thanks Jim,
I am able to install programs through the synaptic package manager, but reloading there didn't seem to help the issue with add/remove programs - I'm still not seeing anything listed there... is there anything else I might try?
Sara

Try from a terminal ```
sudo apt-get install --reinstall gnome-app-install
```

Some people have been having problems with this especially after installing Adobe Air.

Good Luck

---

### Post by ndipity on 2009-02-25
> **plucky said:**
> Try from a terminal ```
sudo apt-get install --reinstall gnome-app-install
```

Some people have been having problems with this especially after installing Adobe Air.

Good Luck

Thanks, that did the trick!

---

