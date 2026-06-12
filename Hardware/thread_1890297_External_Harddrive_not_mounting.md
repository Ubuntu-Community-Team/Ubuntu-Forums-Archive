---
title: "External Harddrive not mounting"
date: 2011-12-03
forum: Hardware
---

### Post by UncleMonty on 2011-12-03
My external harddrive is refusing to mount. The power light is coming on. It's not making any strange noises. It's a few months old and has only been used once to do a full back up. It has not been turned on since. Now it's refusing to show up when I plug it in and a strange drive called 'boot' has appeared from nowhere.

Anyone know what I can do?

---

### Post by cmcanulty on 2011-12-03
Try this it won't hurt anything and works for me.It takes a few minutes. When done try mounting

```
sudo killall udisks

``` then
```
sudo apt-get install udisks libgdu0 gnome-disk-utility policykit-desktop-privileges --reinstall
```

---

### Post by AlexandreMBM on 2013-02-21
See ["Re: NX Server, policykit, remote privileges" #3]("http://ubuntuforums.org/showpost.php?p=10095159&postcount=3") as analogy.

Try to edit the */usr/share/polkit-1/actions/org.freedesktop.**udisks**.policy* file.

---

### Post by wildmanne39 on 2013-02-21
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

