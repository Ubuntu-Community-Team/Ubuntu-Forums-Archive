---
title: "Hangs on restart"
date: 2008-11-12
forum: General Help
---

### Post by martinbc on 2008-11-12
Hi.

When I restart the computer, the shutting down works fine, but when the computer boots again the computer freezes.

When:
When grub is loading usually there is a underscore blinking and then you get the menu, right?
But in my case after restarting the computer the underscore is twice the size and nothing else happens!

Dist: Ubuntu 8.10 
Kernel: 2.6.27-7-generic
Computer: HP dv5-1055eo (laptop)

Hope this is all the information that you need, if not, let me know and I'll get some more information for ya.

Thanks.
Martin.

---

### Post by ryry46d9 on 2008-11-12
you can try and use the CD to fix grub 

if you do a "cold" boot is it fine ?

I some times get where I "warm" reboot log in and my desktop is froze

I did find  kicking the C**p out of the computer does not help

---

### Post by caljohnsmith on 2008-11-13
So you are saying you can't boot at all any more? You mentioned that shutting down works fine, so are you able to boot into some OS and shut down? Have been able to boot into Ubuntu after installing it, or did this happen right after you installed Ubuntu? 

How about booting your Live CD, opening a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

