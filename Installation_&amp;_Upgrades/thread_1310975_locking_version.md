---
title: "locking version"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by leorolla on 2009-11-02
Hello,

If I lock the version of a package in synaptics, does apt-get respect it?

Does it survive after distribution ugrades?

Within a Gnome Desktop Hardy installation, if I lock Kile and Kdvi in synaptics, will Kdvi survive upgrading to Karmic and will Kile stay with the Hardy version (Kile 2.0) ?

Thanks!!!

---

### Post by lethalfang on 2009-11-05
> **leorolla said:**
> Hello,

If I lock the version of a package in synaptics, does apt-get respect it?

Does it survive after distribution ugrades?

Within a Gnome Desktop Hardy installation, if I lock Kile and Kdvi in synaptics, will Kdvi survive upgrading to Karmic and will Kile stay with the Hardy version (Kile 2.0) ?

Thanks!!!


You need to do the following to lock Kile and KDVI for apt-get:

```
sudo echo 'kile hold' | sudo dpkg --set-selections

```

To undo:
```
sudo echo 'kile install' | sudo dpkg --set-selections
```


To lock version in aptitude:

```
sudo aptitude hold kile
```

To undo:

```
sudo aptitude unhold kile  
```

---

### Post by leorolla on 2010-02-18
Thanks!

Recently I learned how to pin packages to different repository versions, which is closer to what I wanted.

---

