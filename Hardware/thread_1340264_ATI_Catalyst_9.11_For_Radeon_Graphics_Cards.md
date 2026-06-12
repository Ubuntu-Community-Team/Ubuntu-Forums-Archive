---
title: "ATI Catalyst 9.11 For Radeon Graphics Cards"
date: 2009-11-28
forum: Hardware
---

### Post by Nomorebloat on 2009-11-28
Hello, I'm new to Ubuntu.

I installed a clean install of 9.10   64 bit version.

I successfuly installed the Catalyst drivers, but I can't change any display properties because it tells me I'm not the admin!

---

### Post by cariboo on 2009-11-28
I'm not sure how the catalyst control ap works, but any time you need to run as root, press Alt-F2 and type:

```
gksudo <app_name>
```

where app_name is the name of the application you need to run as root.

---

### Post by Nomorebloat on 2009-11-28
Thank you for much!  It works.

I created a desktop item, stuck the command in front of the file name, and now I can edit display properties.

I wonder if anyone knows a good software program that will tell you hardware stats, like gpu temp etc.

---

