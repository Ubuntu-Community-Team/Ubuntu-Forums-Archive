---
title: "Laptop drivers are killing me"
date: 2008-10-04
forum: General Help
---

### Post by feras.ws on 2008-10-04
Dear Users ,

I have a very serious problem with my laptop (Toshiba A200-1M7).
The drivers issue !! there is no sound , no dial-up modem ! nothing ! just the wireless working ! even the blue-tooth doesn't work !
So , could you please help me .

Regards
Feras

---

### Post by linuxgr on 2008-10-05
For the sound, could you post the result of:

```
cat /proc/asound/card0/codec#* |grep Codec 
```

---

### Post by feras.ws on 2008-10-05
Well now I am using the damn vista but I remember it was intell !

---

