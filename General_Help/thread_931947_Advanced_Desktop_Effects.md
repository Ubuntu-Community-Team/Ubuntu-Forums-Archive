---
title: "Advanced Desktop Effects"
date: 2008-09-27
forum: General Help
---

### Post by jobo1313 on 2008-09-27
I for some reason dont have Advance Desktop Effects in my menu
Any help would be great

---

### Post by howefield on 2008-09-27
In terminal type

```
sudo apt-get install compizconfig-settings-manager
```


Or install it from Synaptic package manager. 

After installing you should find Advanced Desktop Effects Settings option in your System > Preferences menu.

---

### Post by jobo1313 on 2008-09-27
Okay but i cant open it

---

### Post by howefield on 2008-09-27
what happens when you type 

```
ccsm
``` 

in terminal ?

---

### Post by jobo1313 on 2008-09-27
This is what happened:

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 38, in <module>
    import compizconfig
ImportError: /usr/lib/python2.5/site-packages/compizconfig.so: undefined symbol: ccsGetPluginStrExtensions

---

### Post by DrVitoti on 2009-01-26
I happens to me as well, i would really appreciate it if somebody could help us solve it. Thanks beforehand.

---

### Post by rednano12 on 2009-01-26
```
sudo apt-get fusion-icon
```

???

---

