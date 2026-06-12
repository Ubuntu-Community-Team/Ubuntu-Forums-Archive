---
title: "grub2 usage on 9.10"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by ankscorek on 2009-10-30
helo friends

i want a favour

title           bactrack4
root            (hd0,2)
kernel         (hd0,2)/boot/vmlinuz rw root=/dev/sda3
initrd         (hd0,2)/boot/splash.initrd
quiet


i want to put these lines in my grub how do i do it please?

i mean i have a multi boot system

with backtrack4 and ubuntu 9.10

---

### Post by Frantic_Earthling on 2009-10-30
I guess that what you need is here:

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=login+screen](http://ubuntuforums.org/showthread.php?t=1195275&highlight=login+screen)

---

### Post by ankscorek on 2009-10-30
well i did this small hack

in my grub menu

i edited the line

it read root=/dev/sda1 for my bt4

i just changed it to /dev/sda3


it worked

but when i will do a fresh install of new OS on some othe partition will grub2 recognise and update itself?

---

### Post by drs305 on 2009-10-30
> **ankscorek said:**
> but when i will do a fresh install of new OS on some othe partition will grub2 recognise and update itself?

You are talking about the install of a *different* OS? After you install it run "sudo update-grub". That will run os-prober, which will look for other OS's on your partitions. It does a fairly good job but doesn't always detect everything. Try it, if it doesn't find it, you can create a 40_custom menu.

See the links in my signature line regarding Grub 2.

---

### Post by ankscorek on 2009-10-30
thanks i will do update-grub from ubuntu 9.10...

yea and i will also remember not to install grub of new distro in hd0

i will use grub of ubuntu karmic

---

### Post by axel_2078 on 2009-10-30
> **ankscorek said:**
>  i will also remember not to install grub of new distro in hd0


What do you mean by this?

---

### Post by ankscorek on 2009-10-31
means if u r using grub of karmic then dont overwrite the grub when doing other distro install...dont install grub in hd0 in that case

---

