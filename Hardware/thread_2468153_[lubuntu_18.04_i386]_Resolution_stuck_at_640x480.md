---
title: "[lubuntu 18.04 i386] Resolution stuck at 640x480"
date: 2021-10-19
forum: Hardware
---

### Post by merlooo on 2021-10-19
Hello,

after fresh install of "lubuntu 18.04 i386" on a notebook "HP Mini 2133" i am trying to change the resolution to higher than 640x480.

However, its not possible. Can someone please help me with this issue?

Thanks in advance for any tips...

---

### Post by guiverc on 2021-10-19
You do realize Lubuntu 18.04 LTS was a *flavor* of Ubuntu, and thus only came with three years of supported life.  ie. you can see that here

- [https://lubuntu.me/bionic-eol/](https://lubuntu.me/bionic-eol/)
- [https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/](https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/)

> Maintenance updates will be provided for 5 years for Ubuntu Desktop,  Ubuntu Server, Ubuntu Cloud, and Ubuntu Base.  All the remaining  flavours will be supported for 3 years.

where the three years of supported life from release in April 2018 was reached April 2021.

You can use `ubuntu-support-status` to confirm what parts of your system are still supported, and which parts do not get security fixes/patches (a good deal of your system is base Ubuntu, so still gets upgrades & fixes!)

A tip:  I'd look at what kernel stack you're installed (the ISO used to install the system controls this) and trying to the alternate kernel stack choice for Ubuntu LTS releases is usually easy to do with no minimal ill effects (*more disk space used, more to upgrade* etc) though you could try booting *live* media to with the other stack if you don't want to install (I don't know your box; but I'm assuming it's not limited to 768MB of RAM so can use *live* media).

---

