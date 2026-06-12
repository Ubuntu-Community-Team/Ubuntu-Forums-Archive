---
title: "How to install lubuntu ?"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by sowhat123456789a on 2009-02-23
I open the lubuntu 8 from live cd but I don't know how to install it ? There isn't any install icon on desktop or on menus ? Can you please help  me ?

---

### Post by Partyboi2 on 2009-02-23
Just to clarify have you burned the ubuntu live cd iso to a disk and booted it?

---

### Post by tad1073 on 2009-02-23
Do you know how to change the boot order of you computer in your bios?

---

### Post by sowhat123456789a on 2009-02-24
[http://lxde.org/download](http://lxde.org/download) writes :
Install LXDE and Debian GNU/Linux into your computer
Thanks to Debian GNU/Linux project for making LXDE easily available. However, there is no installer available in Debian Live image yet. Nevertheless, if you want to install it into your computer system, you can use Debian XFCE+LXDE installation CD image available below

I thnik Lubuntu can't install from a livcd. :(

---

### Post by azroy on 2009-02-24
need me for solve time installation language desktop 'hang' or stop install...why??

now i use win xp and 2 partition...so i can install for drive d: ..

plzzz help me..

---

### Post by piroko on 2009-02-24
> **Partyboi2 said:**
> Just to clarify have you burned the ubuntu live cd to a disk and booted it?

Why would he burn a live cd to another cd?

---

### Post by cariboo on 2009-02-24
@sowhat123456789a

You need to boot from the LiveCD in order to install Ubuntu.

Enter your BIOS and set the boot order to boot from the CD first.

Jim

---

### Post by Partyboi2 on 2009-02-24
> **piroko said:**
> Why would he burn a live cd to another cd?
I forgot to add 'iso'  and just realized they are actually trying to install lubuntu :redface:   thanks for pointing that out. :)

---

### Post by sowhat123456789a on 2009-02-24
@all :) I burn the lubuntu iso which I had downloaded it. And I boot from live cd. But I couldn't see the "install" button,link,text anywhere... :(

---

### Post by KiwiWifi on 2009-09-10
Lubuntu can't be installed on the harddrive from the LiveCD - not in the B14 release anyways.

Hope they fix this asap, I'm really looking forward to this Lubuntu thingy.

---

### Post by gijsterbeek on 2009-09-13
> **KiwiWifi said:**
> Lubuntu can't be installed on the harddrive from the LiveCD - not in the B14 release anyways.

Hope they fix this asap, I'm really looking forward to this Lubuntu thingy.

Just grab the b23 release from this site:

[http://download.lxde.org/lubuntu-9.10/](http://download.lxde.org/lubuntu-9.10/)

It has a shortcut to the installer, but it doesn't work. What you should do, is open a terminal en type

```
sudo ubiquity
```

That almost does the trick. After the installer finishes and asks for a reboot, you might have to do that manually with

```
sudo reboot
```

Should do it, but rebooting doesn't automatically start X. So after login in, you have to do a ```
startx
```.

---

