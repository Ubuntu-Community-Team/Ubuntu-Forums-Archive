---
title: "Module programming"
date: 2008-07-19
forum: General Help
---

### Post by halilakin on 2008-07-19
Hello all.

I am trying to write a module and there are some questions in my mind.

First I am trying to write running processes to console.However printk() function doesn't display it properly. Using KERN_EMERG flag, it prints out like

Message from syslogd@johndoe-laptop at Fri Jul 18 18:51:08 2008 ...
johndoe-laptop kernel: [ 4603.244000] soffice.bin

Message from syslogd@johndoe-laptop at Fri Jul 18 18:51:08 2008 ...
johndoe-laptop kernel: [ 4603.244000] insmod

Message from syslogd@johndoe-laptop at Fri Jul 18 18:51:08 2008 ...
johndoe-laptop kernel: [ 4603.244000] kstopmachine

Message from syslogd@johndoe-laptop at Fri Jul 18 18:51:08 2008 ...
johndoe-laptop kernel: [ 4603.244000] udevd

it displays Message from syslogd@... on every printk.

World is a bit tough with printk. Is there any way of using standart libraries (at least studio.h) when writing modules?

And another question. I am supposed to refresh the data in a time interval given by the user as a paramaeter. So i must somehow use time.h or equivalent of it. Is there any source of functions we can use when wiriting modules. I dont know any other function except printk yet.

I am a bit newbie to kernel programming. So please help me :)

Kernel 2.6
Distro 7.04 Ubuntu

---

