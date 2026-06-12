---
title: "Hplip and Hp1020"
date: 2008-11-15
forum: Hardware
---

### Post by ugo1 on 2008-11-15
Hi

It's a week that I'm trying to install the Hplip driver(I just finished to install ubuntu for the 3rd time) for the Hp 1020. I decided to use the run file at hplip site. I'm installing it on hardy 386 server version so I don't want/need gui. 

Which dependecies I need to install before?

when the printer must be plugged at the computer and turned on?

is correct start the install process from the directory home\user_name ? (logged as user_name not root)

Regards

Ugo

---

### Post by cariboo on 2008-11-15
Use cups to install the printer, you will have a much easier time of it. Install a text based web browser such links, then access cups from your server by entering:

```
links http://localhost:631
```

Jim

---

### Post by ugo1 on 2008-11-16
Hi

but cups doesn't have the driver for the hp 1020.

Regards

Ugo

---

