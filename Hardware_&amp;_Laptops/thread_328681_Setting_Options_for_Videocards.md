---
title: "Setting Options for Videocards"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by paulr on 2006-12-31
I think this belong here, not in Multimedia :)

I have a BT878 based TV card which I can make work. However, because I am in the UK I need to install the tuner parts with pal=i options ; on default set up the tuner card works with static sound ; if I remove the tda9887 tuner bt878 and bttv modules, then reload them with

modprobe tda9887 pal=i
modprobe tuner pal=i
modprobe bttv

it works fine. 

I've tried putting these in /etc/modprobe.conf/options as

option tda9887 pal=i
option tuner pal=i

but it seems not to work (is it autodetected before that ?) ?

Anyone offer advice on how to do this automatically ?

---

