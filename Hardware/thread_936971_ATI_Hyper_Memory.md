---
title: "ATI Hyper Memory"
date: 2008-10-03
forum: Hardware
---

### Post by proxess on 2008-10-03
Anyone know how to set up ubuntu to use ATI's Hyper Memory feature? I saw a way (don't know if its viable) using aticonfig, but I don't want to use aticonfig as to not lose my xorg.conf.

Any possibility?

I've got a: Asus Z53Jr Series (F3Jr Motherboard)

[COLOR="Gray"]Intel Centrino Duo T5500 1.66ghz; [/COLOR][COLOR="Silver"]2048mb RAM; [/COLOR][COLOR="Gray"]ATI Mobility Radeon x2300 128MB, Up to 896MB with Hyper Memory; [/COLOR][COLOR="Silver"]Hitachi 120gb + iPod Video 60GB + Maxtor 160GB External.[/COLOR]

---

### Post by markbuntu on 2008-10-03
aticonfig will not overwrite your xorg.conf unless you run aticonfig --initial and it will save the old one unless you tell it explicitly not to. It wont even read it unless you tell it to.

---

### Post by proxess on 2008-10-09
And is it possible to know what it does so I can permanently set xorg.conf with the Hyper Memory size?

---

### Post by markbuntu on 2008-10-09
aticonfig commands will set the defaults in the ati configuration file. xorg.conf is being deprecated.

---

### Post by proxess on 2008-10-23
There's still a long way to go before xorg.conf should be deprecated. There are a whole bunch of configurations which simply cannot be remove right now depending on one's system.

Seems like it won't be any time soon until AMD/ATI supports Hyper Memory on Linux.

---

