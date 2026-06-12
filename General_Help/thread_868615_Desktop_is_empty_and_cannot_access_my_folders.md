---
title: "Desktop is empty and cannot access my folders"
date: 2008-07-24
forum: General Help
---

### Post by windriver on 2008-07-24
Hi, All the files from desktop has been removed suddenly and cannot access to any of my folders except via terminal. Need help.

---

### Post by Dylock on 2008-07-24
Sounds like nautilus might not be running.

Open a terminal and type pidof nautilus and see if you get anything.

If not you can start nautilus from the command line:
```
nautilus &
```

---

### Post by windriver on 2008-07-24
> **Dylock said:**
> Sounds like nautilus might not be running.

Open a terminal and type pidof nautilus and see if you get anything.

If not you can start nautilus from the command line:
```
nautilus &
```

I tried but nothing is coming up

---

### Post by Dylock on 2008-07-24
does 

```
nautilus --no-desktop
``` 

do anything for you?

Check your logfiles see if anything is wonky after you attempt to open nautilus. Also i believe there is some test that can be done with nautilus, might be on the manpage.

---

