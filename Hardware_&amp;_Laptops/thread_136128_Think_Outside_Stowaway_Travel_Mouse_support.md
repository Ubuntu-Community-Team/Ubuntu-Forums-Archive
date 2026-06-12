---
title: "Think Outside Stowaway Travel Mouse support"
date: 2006-02-25
forum: Hardware &amp; Laptops
---

### Post by koolguynet on 2006-02-25
Has anyone been able to get the Think Outside Stowaway Travel Mouse (bluetooth) working?  I can see it in my bluetooth devices, but that is about it.

---

### Post by rvarnam on 2008-06-05
I haven't been able to get this working, either.  Using Hardy, device is discovered and identified as a 'Mouse' but Ubuntu won't then connect to discover services.

---

### Post by rvarnam on 2008-06-08
SOLVED - switch on computer's bluetooth receiver, then the mouse.  Press the 'hidden' button on the underside of the mouse to make it discoverable. Wait a few seconds, then do:

```
sudo hidd --search
```

In future, the mouse will just connect when it's switched on.

---

