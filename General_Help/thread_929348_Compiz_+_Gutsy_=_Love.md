---
title: "Compiz + Gutsy = Love?"
date: 2008-09-24
forum: General Help
---

### Post by crunchyblack on 2008-09-24
Just wondering if compiz works with gutsy? 

I keep seeing all these cool desktops with the cube and i wanna know if its possible for me!! (since im using gutsy)

thanks in advance

---

### Post by Genius314 on 2008-09-24
Yeah. In fact, it should be installed by default. To enable it, go to System>Preferences>Appearance, and in the "Effects" tab, select normal or extra. (It might be a bit different in Gutsy, but it should be in about the same place)

---

### Post by el-mar01 on 2008-09-25
Upgrade to Hardy (why haven't you) and you get a newer version of Compiz.

---

### Post by crunchyblack on 2008-09-25
hardy freezes my system (as well as a million other peoples) its just messed up currently :\ dunno why...

---

### Post by anotherdisciple on 2008-09-25
You will be able to control the effects... like the desktop cube by doing this:

Open a terminal (Applications > Accessories > Terminal) and type:

```
sudo aptitude install compizconfig-settings-manager
```

After installing it... you can acces the Effects Manager through (System > Preferences > Advanced Desktop Effects Settings)

Also, you may need to enable restricted drivers to use the 3d effects. To do this in gutsy go to (System > Administration > Restricted Drivers Manager). If you have any available... Apply them.

---

