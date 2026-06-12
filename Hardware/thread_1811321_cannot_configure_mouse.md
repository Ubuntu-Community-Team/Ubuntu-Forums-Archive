---
title: "cannot configure mouse"
date: 2011-07-24
forum: Hardware
---

### Post by Cnaeus on 2011-07-24
I would like to change the mouse sensitiv in lubuntu 11.04, but the mouse&keyboard config utility crashes whenever I try to bump up mouse sensitivity. Is there any workaround possible to make my mouse a bit more sensitve? Thanks

---

### Post by SteveDee on 2011-07-26
> **Cnaeus said:**
> Is there any workaround possible to make my mouse a bit more sensitve?

Your question is related to this one: [http://ubuntuforums.org/showthread.php?t=1744829](http://ubuntuforums.org/showthread.php?t=1744829)

For a regular mouse you can probably edit the desktop.conf file which is somewhere like: /home/{username}/.config/lxsession/LXDE/desktop.conf
...and has 3 mouse settings:-
```

[Mouse]
AccFactor=20
AccThreshold=10
LeftHanded=0

```

If you have a laptop with touchpad, open a terminal and type:-
```

 synclient

```
This should list all available settings for your touchpad. To change a setting, type the parameter=new value. Example:-
```

synclient MaxSpeed=2

```

---

### Post by Cnaeus on 2011-07-30
Arkanabar's solution on the link you posted worked just fine for me!
Many thanks! :)

---

