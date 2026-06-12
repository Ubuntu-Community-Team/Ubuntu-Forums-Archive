---
title: "Removing WiFi Access"
date: 2009-12-16
forum: Hardware
---

### Post by pAsM on 2009-12-16
Hello,
    Here is a bit of a strange request. I am working on modifying a copy of Ubuntu to match the needs of a few security minded users. So far it is going great. There is only 1 problem that I am unable to get past.

I need to find a way to remove the ability for the user to use a WiFi hotspot if their machine has a wireless card. There is a potential of sensitive data being transmitted and I do not want the user to be able to communicate it over a unsecured wireless access point (I honestly dont trust any external access point).

---

### Post by Grenage on 2009-12-16
I suppose you could remove all the wireless drivers?

---

### Post by pAsM on 2009-12-16
> **Grenage said:**
> I suppose you could remove all the wireless drivers?

Hello,
[INDENT]Where would I go to do that?[/INDENT]

---

### Post by Grenage on 2009-12-17
I have never had to do it myself, is the following link any help?

[http://www.cyberciti.biz/faq/add-remove-list-linux-kernel-modules/](http://www.cyberciti.biz/faq/add-remove-list-linux-kernel-modules/)

---

### Post by IcarusR on 2009-12-17
If you want to prevent wireless use completely why not disable it in the bios & password protect the bios (easier than finding & removing module).
But if you just want to prevent hotspot use & allow authorized wireless access that is a different matter. 
But must be a authorized networks config file some where.
Or possibly could do it with local firewall rules ??

---

