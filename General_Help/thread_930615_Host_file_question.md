---
title: "Host file question"
date: 2008-09-26
forum: General Help
---

### Post by Linkin4 on 2008-09-26
I have seen many instances where people have configured their hosts file in the following manner:

127.0.0.1         localhost.localdomain    localhost      actual_hostname

why would someone point the hostname of the machine itself at the loopback address?

---

### Post by Dr Small on 2008-09-26
Because the loopback is the address of the system (127.0.0.1), so it is only natural to point the hostname to it also.

---

### Post by Linkin4 on 2008-09-26
More specifically, what purpose does it serve?

---

