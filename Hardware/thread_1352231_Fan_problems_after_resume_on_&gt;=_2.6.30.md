---
title: "Fan problems after resume on &gt;= 2.6.30"
date: 2009-12-11
forum: Hardware
---

### Post by Trebaruna on 2009-12-11
I discovered that in 9.10 my laptop's fan will not turn on after I resume the machine from suspend. As soon as the reported temperature reaches 80C, however, the fan switches on at its highest speed and never slows down. This is pretty much a showstopper because I use suspend quite a lot.

After some experimenting with vanilla kernels it appears as though a change was introduced in 2.6.30 which causes this behavior: if I compile and install 2.6.29 it works. This is far from ideal, however, as my laptop's touchpad doesn't work in 9.10 with that version.

Could anyone help my figure out what happened in 30, and how to fix it for me?


[SIZE=1]Using 9.04 with stock kernel results in random graphical corruption, has crummy flash performance and only has a beta of firefox 3.5. Using 29 alleviates the corruption but it's clearly not ideal. Using 9.10 would be the preferred option, provided I can get it to work right.[/SIZE]

---

