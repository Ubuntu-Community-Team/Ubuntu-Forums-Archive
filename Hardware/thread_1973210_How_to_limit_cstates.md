---
title: "How to limit cstates?"
date: 2012-05-04
forum: Hardware
---

### Post by kara mustafa on 2012-05-04
I am trying to limit c-states which my laptop uses with those commands: 

> processor.max_cstate=2
intel_idle.max_cstate=2but it doesn't work and I have no idea how do it in another way. 
Any help will be appreciate. 

My laptop is Asus N71Ja and I use ubuntu 12.04 64bit. 

Thanks in advance.

---

### Post by Popenuj on 2012-11-08
In a terminal type:
```
sudo nano -w /etc/default/grub
```Enter your password when prompted.
Change the line reading:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```to:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash processor.max_cstate=2"
```Press "ctrl+x"
Type:
```
update-grub
```Then restart your laptop.

---

