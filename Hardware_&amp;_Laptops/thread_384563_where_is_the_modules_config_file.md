---
title: "where is the modules config file?"
date: 2007-03-14
forum: Hardware &amp; Laptops
---

### Post by Zyphrexi on 2007-03-14
I was looking to remove the module for one of my sound cards to force all applications to use a specific soundcard. Now I know I could simply physically remove it, but I don't want to do that. Trouble is, I took a look at /etc/modules [no modules.conf here :( ) and well I see a few modules, but where the heck is the massive extended list that I *know* loads every time?

---

### Post by Dr. Nick on 2007-03-15
you trying to stop a module form loading?

IF so look at /etc/modprobe.d/blackilst

---

