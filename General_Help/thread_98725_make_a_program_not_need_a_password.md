---
title: "make a program not need a password"
date: 2005-12-04
forum: General Help
---

### Post by HokeyFry on 2005-12-04
how do you make a program that requires a password (i.e. synaptic package manager, networking, etc.) not need a password?

As a note, it is not synaptic or networking that i want to make availablem it is called Wi-Fi radar, and I want to make all users able to use this no matter what.

---

### Post by Perfect Storm on 2005-12-04
I think you can use this

```
sudo gedit /etc/sudoers
```

add to the buttom:

**<username>** ALL= NOPASSWD:/usr/bin/name-of-the-launcher

You might first check where your Wi-Fi radar launvher is installed.

---

