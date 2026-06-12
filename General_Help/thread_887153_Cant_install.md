---
title: "Cant install"
date: 2008-08-11
forum: General Help
---

### Post by stevecov on 2008-08-11
When I try to install I get the error 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

What should I do to fix this?

---

### Post by tuxxy on 2008-08-11
Open a terminal and type

```
sudo dpkg --configure -a
```

---

### Post by louieb on 2008-08-11
Open a terminal window **Applications>Accessories>Terminal**
and type
```
sudo dpkg --configure -a
```

It will ask for your password.  Type it in and press enter.
(Note the command line does not echo anything back when you are typing the password - thats normal just type it in and press enter).

---

