---
title: "Root Disabled"
date: 2008-09-06
forum: General Help
---

### Post by Kurou-san on 2008-09-06
My dad recently was chmod and chown a folder when the computer glitched up before he finished typing and it came up with chmod 644 /| chown root /. I couldn't open anything, so I rebooted. I came up with a terminal by pressing Alt + F3 after rebooting, but I don't know what to do. Please help.

---

### Post by Kurou-san on 2008-09-06
Bump. No one ever responds to my threads...

---

### Post by cariboo on 2008-09-06
Have you tried changing the permissions of the folder by using:

```
sudo chmod 777 /folder
```

Jim

---

### Post by Kurou-san on 2008-09-06
I can't use sudo, but can login as root through the termianl and tried that. No dice. Maybe a better title would be Sudo Disabled..

---

### Post by Sycron on 2008-09-06
I've done a big mistake. ```
cd / && chmod -rf 777 *
``` The only thing that i could done was to reinstall everything.

---

### Post by Kurou-san on 2008-09-06
> **Sycron said:**
> I've done a big mistake. ```
cd / && chmod -rf 777 *
``` The only thing that i could done was to reinstall everything.

I was afraid of that.

---

### Post by Sycron on 2008-09-06
Be careful when using sudo... You may harm your computer, like I've done, and it's not likely.

---

### Post by Elfy on 2008-09-06
when you login to recover you are root so don't need sudo.

Which folder did your dad chown and chmod?

---

### Post by Kurou-san on 2008-09-06
I know. And like said in the first post, "/".

Anyway, I already reinstalled.

---

