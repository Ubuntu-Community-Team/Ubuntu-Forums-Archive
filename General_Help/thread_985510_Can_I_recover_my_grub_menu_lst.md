---
title: "Can I recover my grub menu lst?"
date: 2008-11-17
forum: General Help
---

### Post by nelsyeung on 2008-11-17
I was trying to backup the grub menu lst file but I seem to typed the wrong code and deleted it. :(  Just wondering is there anyway to recover the menu.lst without reinstalling ubuntu?

Some information: (hope it helps)
Window Vista (Installed first)
Ubuntu 8.10
2 partitions (first one for vista and second one for ubuntu)

Please help me thanks :(

---

### Post by jenkinbr on 2008-11-17
Do you recall what it was that you typed?  If it was rm, then it's gone.  what do you get when you type ```
ls /boot/grub
```?

edit: although this is primarily for windows users after installing windows after ubuntu,[ this should help]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") if all else fails...

---

### Post by sisco311 on 2008-11-17
did you reboot?
if not, then type:
```
sudo update-grub
```to generate a new menu.lst file.

---

### Post by jenkinbr on 2008-11-17
> **sisco311 said:**
> did you reboot?
if not, then type:
```
sudo update-grub
```to generate a new menu.lst file.
Doh!  *stupid me*

---

### Post by ibuclaw on 2008-11-17
Though you may require some tweak-age afterwards.

update-grub will only setup the grub menu.lst file for your **currently running operating system**.

So if you use anything else (ie: Windows, FreeBSD, Debian, etc) it won't appear in the newly generated menu.lst file.

Regards
Iain

---

### Post by nelsyeung on 2008-11-18
> **sisco311 said:**
> did you reboot?
if not, then type:
```
sudo update-grub
```to generate a new menu.lst file.

:)
Cool, thanks for this i got the menu.lst back but as...

> Though you may require some tweak-age afterwards.

update-grub will only setup the grub menu.lst file for your currently running operating system.

So if you use anything else (ie: Windows, FreeBSD, Debian, etc) it won't appear in the newly generated menu.lst file.
What do I need to do to get my window vista to come back up, I also have a D drive recovering disk before aswell.

thanks

---

### Post by caljohnsmith on 2008-11-18
How about first opening your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
And at the bottom add:
```
title Windows Vista
root (hd0,0)
chainloader +1
```
that should work assuming that Vista is on sda1. If not, how about first posting:
```
sudo fdisk -lu
```
And we can work from there if you want. :)

---

### Post by nelsyeung on 2008-11-18
Thank you so much **caljohnsmith**!! and **sisco311**!! :)
It works perfectly

---

### Post by sisco311 on 2008-11-18
Cool!

Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

---

