---
title: "Saving Battery Power"
date: 2006-07-11
forum: Hardware &amp; Laptops
---

### Post by montag451 on 2006-07-11
Hey all,

New to Linux, just got myself a Dapper install on my Acer TravelMate 8200. I was wondering if there are any applets for GNOME to handle turning down screen brightness automatically when running on battery power, or handling anything else that would optimize battery life for a laptop.

Thanks.

---

### Post by nischg on 2006-07-11
check if you have power manager installed.

[http://www.gnome.org/projects/gnome-power-manager/]("http://www.gnome.org/projects/gnome-power-manager/")

```
sudo apt-get install gnome-power-manager
```

I have it on my Inspiron 6400 but even so I get lower battery life than in Win. It looks like it has something to do with the kernel capacity to undervolt when there is no need for that much juice. 

Regards

---

### Post by montag451 on 2006-07-12
Installed, but no useful power-saving features. Only options on when to turn off the screen, etc. Luckily, my function keys work correctly, so I'll just have to do it manually.

---

