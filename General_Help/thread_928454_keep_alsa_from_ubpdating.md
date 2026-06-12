---
title: "keep alsa from ubpdating"
date: 2008-09-24
forum: General Help
---

### Post by rfrayer on 2008-09-24
Hi ive seen this done once but for the life of me cannot figure out how to do this..

alsa works fine after installing. making a custom asound.conf for my usb cam/mic works great. as soon as i run an upgrade through thye upgrade manager then blam usb mic no loger works.

is there a way to allow updates for everything except alsa?   and further more i notice that after updates oss-alsa no longer works with my games firefox etc.


please remove this if not leave it im sure someone else is wondering heres how i did it 

```

sudo su

echo "alsa-base hold" | dpkg --set-selections
```

---

